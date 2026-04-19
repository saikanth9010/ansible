# Proxmox LXC Automated Provisioning

This repository contains a professional Ansible-driven workflow to automatically provision, start, and configure an LXC container on a Proxmox VE host from a macOS workstation.

## 🚀 Features
- **API-First Provisioning**: Uses Proxmox API Tokens for secure authentication without sharing root passwords.
- **Automated Lifecycle**: Handles both creation (`state: present`) and power-on (`state: started`) in a single run.
- **Hardware Firewall Integration**: Automatically enables the NIC-level firewall and injects an `ACCEPT` rule for SSH (Port 22).
- **Dynamic Inventory**: Bridges the gap between the Proxmox API and the new container's SSH by registering the host on the fly.
- **System Hardening**: 
    - Installs the `sudo` package (missing in minimal Debian templates).
    - Creates a dedicated admin user (`sai`).
    - Injects your local SSH Public Key for passwordless login.
    - Configures non-interactive `sudo` via `/etc/sudoers.d/`.

## 📋 Prerequisites

### 1. Local Environment (MacBook)
Ensure the required Python libraries and Ansible collections are installed:
```bash
pip install proxmoxer passlib
ansible-galaxy collection install community.proxmox ansible.posix
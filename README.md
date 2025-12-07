# 🛡️ Metasploitable 2: Offensive Security Lab

![Status](https://img.shields.io/badge/Status-Active-brightgreen)
![Environment](https://img.shields.io/badge/Environment-VirtualBox%20NAT-blue)
![Focus](https://img.shields.io/badge/Focus-Manual%20Exploitation-red)

## 📖 About This Project
This repository documents my journey as an Offensive Cybersecurity Intern. It serves as a technical journal for manual exploitation techniques, network troubleshooting, and understanding the "why" behind legacy vulnerabilities.

Unlike automated script-kiddie approaches, this lab focuses on:
* **Manual Exploitation:** Understanding the underlying protocol failures.
* **Deep Troubleshooting:** documenting network conflicts (IP clashes) and configuration drifts.
* **Security First:** analyzing why these vulnerabilities exist and how they are patched.

## 🏗️ Lab Architecture
To ensure security and isolation from the host network, this lab utilizes a strictly controlled **NAT Network** environment.

* **Hypervisor:** Oracle VirtualBox 7.x
* **Network CIDR:** `10.0.2.0/24` (Isolated "NatNetwork")
* **Attacker:** Kali Linux (Rolling)
* **Target:** Metasploitable 2 (Intentionally Vulnerable Ubuntu)

### ⚠️ Critical Configuration Note
A common pitfall in home labs is "Ghost IP" conflicts when using Bridged mode. This lab enforces **NAT Network** mode to prevent the attacker machine from accidentally targeting devices on the physical LAN (routers, phones, etc.).

## 📂 Exploit Log

| Service | Port | Vulnerability Type | Key Concept | Status |
| :--- | :--- | :--- | :--- | :--- |
| **rlogin** | 513 | Trust Relationship Misconfiguration | Privileged Ports (`sudo`), `.rhosts` trust | ✅ Documented |
| **Ingreslock** | 1524 | Bind Shell Backdoor | Unauthenticated Socket Binding | ⏳ Planned |
| **VSFTPD** | 21 | Backdoor Command Execution | Supply Chain Attack | ⏳ Planned |

## 📝 Featured Documentation

### 1. The rlogin Trust Exploit
* **Summary:** Exploiting legacy Berkeley r-commands by manipulating source ports.
* **The Challenge:** Modern Linux kernels block standard users from binding to ports 1-1023. `rlogin` requires a source port in this range to verify "root" trust.
* **The Fix:** Using `sudo` to bind to a privileged port and ensuring the client binary (`rsh-redone-client`) is installed.
* **[📄 Read Full Documentation](docs/rlogin_exploit.md)** *(Note: You will link your detailed ODT content here)*

## 🛠️ Tools Used
* **Nmap:** Network mapping and service version detection.
* **Wireshark:** Analyzing TCP handshakes and RST packets.
* **rsh-client / inetutils:** Legacy binary interaction.

---
### ⚖️ Disclaimer
*This repository is for educational purposes only. All activities were performed in a strictly isolated virtual environment owned by the author. Unloading these techniques on unauthorized networks is illegal.*

---
*Maintained by Vikalp Pratap Yadav*

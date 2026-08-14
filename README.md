# 💻 Tyson's Cybersecurity Lab Environment
**NETWORKWALKS (B082) Cybersecurity Internship Week 1 - Lab Environment Installation & Setup**

![Static Badge](https://img.shields.io/badge/Skill-Cybersecurity-blue)
![Static Badge](https://img.shields.io/badge/Skill-Networking-blue)
![Static Badge](https://img.shields.io/badge/Skill-Virtualization-blue)
![Static Badge](https://img.shields.io/badge/Skill-Linux-blue)

![Static Badge](https://img.shields.io/badge/Host-MacOS%20Apple%20M4-red)
![Static Badge](https://img.shields.io/badge/Software-VirtualBox%20v7.2-red)
![Static Badge](https://img.shields.io/badge/Kali%20Linux-v2026.2-red)
![Static Badge](https://img.shields.io/badge/Network-10.0.0.0%2F24-red)

![Static Badge](https://img.shields.io/badge/Oracle%20VirtualBox-beige?logo=virtualbox&logoColor=%232F61B4)
![Static Badge](https://img.shields.io/badge/Kali%20Linux-beige?logo=kalilinux&logoColor=%2300000)
![Static Badge](https://img.shields.io/badge/GitHub-beige?logo=github&logoColor=%23181717)

---

## 🔎 Project Overview
This project focuses on designing and deploying an isolated cybersecurity testing environment using VirtualBox and Kali Linux.

The lab provides a controlled environment for cybersecurity practices such as network reconnaissance, vulnerability scanning, security assessment, and penetration-testing techniques in a safe and repeatable manner. A private virtual network was established to support future expansion, allowing additional virtual machines to be introduced as authorized targets for security testing and analysis.

---

## 📌 Task
Build an isolated virtual lab environment for pen-testing, ethical hacking, and cyber defense practice. 

---

## 📈 Objectives

- Install and configure Oracle VirtualBox 
- Install and import Kali Linux as a virtual machine 
- Create a private NAT Network for the cybersecurity lab
- Configure network connectivity for Kali Linux
- Assign a consistent IP address to the Kali VM
- Verify network connectivity and DNS resolution
- Take a clean VM snapshot for recovery
- Document the complete setup process
- Prepare the environment for future cybersecurity projects

---

## 📚 Purpose of the Lab
The lab provides an isolated and controlled environment for cybersecurity learning and authorized security testing, such as:

- Network reconnaissance
- Port scanning
- Vulnerability assessment
- Packet analysis
- Web security testing
- Exploitation practice
- Security-tool experimentation

⚠️ **Do not use this lab or its tools to attack unauthorized systems**

⚠️ **This must only be used for systems that you own or have explicit permission to test**

---
  
## 🌐 Lab Architecture
<img width="1346" height="616" alt="image" src="https://github.com/user-attachments/assets/55c02c3a-352e-4f74-b7c6-662bf9ab5d2c" />

Note: Additional target machines can be added to the same virtual network for future projects

---

## ⚙️ Lab Configuration

| COMPONENT  | CONFIGURATION |
| ----------- | ----------- |
| Host OS   | Mac OS Tahoe  |
| Host RAM  | 16 GB  |
| Processor  | Apple M4  |
| Hypervisor  | VirtualBox v7.2  |
| Security OS  | Kali Linux v2026.2  |
| Kali RAM  | 4096 MB  |
| Virtual Network  | NAT Network  |
| Network Address  | 10.0.0.0/24  |
| Kali IP Address  | 10.0.0.2/24  |
| Default Gateway  | 10.0.0.1  |
| DNS Server  | 8.8.8.8  |
| Future VM Range  | 10.0.0.3 - 10.0.0.99  |

---

## ☑️ Lab Setup Procedure

### Step 1. Install 7-Zip

I installed 7-Zip (Mac OS) to extract the Kali Linux VM package.

Tool: [7-Zip](https://www.7-zip.org/download.html)

---

### Step 2. Install VirtualBox

I installed VirtualBox (v7.2 for Mac OS/Apple M4) as the hypervisor.

Tool: [VirtualBox](https://www.virtualbox.org/wiki/Downloads)

---

### Step 3. Create NAT Network

I created a dedicated NAT Network in VirtualBox.

**Configuration:**

Network Name: NatNetwork

IPv4 Prefix: 10.0.0.0/24

DHCP: Enabled

IPv6: Disabled

<img width="2686" height="1521" alt="image" src="https://github.com/user-attachments/assets/2eb8c53b-c4b7-4bb9-ac8a-0fb0645f5ae7" />

Note: A NAT Network configuration was chosen specifically because it lets several VMs on the same virtual network reach each other directly, while still granting each one outbound access to the internet. This setup lays the groundwork for future lab scenarios, where separate attacker and target machines will need to interact with one another.

---

### Step 4. Import Kali Linux

The Kali Linux VM was obtained directly from Kali's official site and brought into VirtualBox through the import process. Because I have an Apple M4 chip, the architecture I dowloaded was: ARM64 Kali Linux Installer v2026.2. Its network adapter was then set up with the following configuration:

```
Adapter 1
Attached to: NAT Network
Network: NatNetwork
Adapter Type: Intel PRO/1000 MT Desktop
```

The VM was allocated:

```
RAM: 4096 MB
```

<img width="2555" height="1701" alt="image" src="https://github.com/user-attachments/assets/01cb9d16-dd60-47a6-874b-d1308d5a4303" />

Note: A shared folder was also configured for transferring required files between the host operating system and the Kali VM.

---

### Step 5. Configure Kali Linux Network

The Kali Linux network configuration was checked and configured with a consistent IPv4 address.

Example configuration:

```
IP Address: 10.0.0.2
Subnet Mask: 255.255.255.0
Gateway: 10.0.0.1
DNS: 8.8.8.8
```

A consistent IP address makes it easier to document the lab and reference the Kali machine in future exercises.

<img width="2562" height="1706" alt="image" src="https://github.com/user-attachments/assets/ab69b467-96c8-4f1f-a740-ece95fd96aca" />

---

### Step 6. Create VM Snapshot

After completing the initial configuration, a VirtualBox snapshot was created.

Example snapshot name:

```
My Fresh Kali Linux
```

The snapshot represents the clean baseline of the laboratory.

If a future exercise changes or damages the VM configuration, the machine can be restored to this baseline.

---

## 🫆 Lab Verification

| TEST  | COMMAND | EXPECTED RESULT |
| ------------- | ------------- | ------------- |
| Check IP Adress  | `ip a`  | Correct Kali IP displayed  |
| Test Gateway  | `ping 10.0.0.1`  | Successful replies  |
| Test Internet Connectivity  | `ping 8.8.8.8`  | Successful replies  |
| Test DNS Resolution  | `nslookup networkwalks.com` | Domain resolves  |
| Verify Nmap  | `nmap --version`  | Nmap version displayed  |
| Verify Snapshot  | Restore snapshot and run `ip a`  | Baseline configuration restored  |

**Example Results:**

```
IP Address:
10.0.0.2/24

Gateway:
10.0.0.1

DNS:
8.8.8.8
```

---

## 🚨 Problems & Solutions

Documenting problems is an important part of the project:

### Problem 1. Systems Compatibility

This exercise was designed and instructed to be executed using a Windows Operating System, I have a Mac OS.

The issue was resolved by:

- Analyzing project instructions and highlighting steps that were unique to Windows OS
- Converting conflicting steps into solutions for my Mac OS
- Downloading a compatible 7-Zip
- Downloading a compatible VirtualBox
- Downloading and Installing a compatible Kali Linux (ARM64 Kali Linux Installer v2026.2)

This setup allowed me to successfully link these systems and create a lab environment that worked for my specs.

### Problem 2. Internet Connectivity

After manually configuring the IPv4 settings, Internet connectivity initially failed due to the Kali/NetworkManager configuration.

As a solution for this issue, I was able to use a command line to bridge the connection with my Kali Linux v2026.2:

```
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
```

The network connection was then rebooted and connectivity was tested again, which successfully worked.

⚠️ **The network interface/connection names may differ between systems, identify your connection before running this command.**

---

## 💡 What I Learned

This project taught me how to build and manage a virtual environment suited for hands-on cybersecurity work:

**1. Hypervisor Fundamentals:**

I learned how a Type 2 hypervisor operates on top of an existing operating system rather than directly on hardware. I used VirtualBox as the intermediary layer that emulates virtual hardware, while macOS continued to manage the actual physical machine underneath.

**2. Host vs. Guest Operating Systems:**

I came to understand the distinction between the OS that controls physical hardware and the OS running in an isolated virtual space. In my setup, macOS served as the Host (supplying real CPU and memory resources) while Kali Linux ran as the Guest inside a contained virtual instance.

**3. Allocating System Resources:**

I practiced dividing up finite hardware resources (processor cores, memory, disk space) between host and guest. This meant carefully calculating how much RAM and how many CPU threads I could hand over to Kali without degrading my Mac's overall performance or causing instability.

**4. Networking Between Virtual Machines:**

I explored how VirtualBox's virtual adapters link VMs to different network types, and how these configuration choices shape whether and how machines can communicate with each other.

**5. Comparing NAT and NAT Network Modes:**

I learned that standard NAT and NAT Network configurations, while similar in name, serve distinct roles. A NAT Network setup lets several VMs share a common virtual network (enabling them to talk to one another) while still translating addresses for outbound internet access. This makes it a strong choice for setting up a multi-VM security testing lab.

**6. Manually Setting Static IP Configuration:**

I gained experience manually assigning and confirming IPv4 settings on Kali, including address, subnet mask, default gateway, and DNS configuration.

**7. VM Snapshot for Recovery:**

I learned the value of capturing a clean VM snapshot before diving into experimental or potentially destabilizing tasks, giving me a safe checkpoint to roll back to during future exercises.

**8. Documentation:**

I recognized that logging every command, configuration change, screenshot, issue encountered, and fix applied is a core habit of professional cybersecurity work.

**9. Presentation:**

I learned how to structure and present my lab notes in a compelling, well-organized way within a GitHub portfolio.

---

## 🔐 Security/Ethical Use

_This lab is intended strictly for education purposes only._

---

## 🧰 Tools & Resources

7-Zip: https://7-zip.org/download.html

Oracle VirtualBox: https://www.virtualbox.org/wiki/Downloads

Kali Linux: https://kali.org/get-kali

---

## 👤 Author

### Tyson Kimball

_Cybersecurity Professional B082_

LinkedIn: https://www.linkedin.com/in/tdkpng/

---

## 📎 Project Information
Program Name: Cybersecurity at NETWORKWALKS

Project: Cybersecurity Lab Setup

Timeline: Week 1

Repository: GitHub

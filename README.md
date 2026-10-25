# Cybersecurity Lab Setup | NetworkWalks Week 1

**By Revathi G.**  
Cybersecurity | VAPT | Hands-on Lab Practice

## About This Project

Hi, I'm Revathi, and I'm building my practical skills in cybersecurity, with an interest in Vulnerability Assessment and Penetration Testing (VAPT).

As part of my **NetworkWalks Cybersecurity Internship — Week 1**, I worked on a Kali Linux lab running inside Oracle VirtualBox. I explored the network configuration, tested connectivity, and documented the process with screenshots.

This project is part of my hands-on cybersecurity learning journey.

## What I Worked On

- Reviewed the Kali Linux virtual machine configuration.
- Checked the VirtualBox network settings.
- Identified the network interface and IPv4 address.
- Inspected the routing table and default gateway.
- Tested network connectivity using `ping`.
- Used NetworkManager commands during troubleshooting.
- Documented the steps and results with screenshots.

## Lab Environment

### Host System

| Component | Details |
|---|---|
| Operating System | Windows 11 Pro |
| RAM | 8 GB |
| Processor | AMD Ryzen 5 |
| Virtualization Software | Oracle VirtualBox 7.2.10 |

### Kali Linux Virtual Machine

| Component | Details |
|---|---|
| Operating System | Kali GNU/Linux Rolling |
| Version | 2026.1 |
| Allocated RAM | 2471 MB |
| Network Mode | NAT Network |
| Network Interface | `eth0` |
| IPv4 Address | `10.0.0.2/24` |
| Default Gateway | `10.0.0.1` |
| DNS Server | `8.8.8.8` |

## 1. VirtualBox Network Settings

I reviewed the virtual machine's network configuration in Oracle VirtualBox.

**Screenshot:**

![VirtualBox Network Settings](screenshots/1%20VirtualBox%20Network%20Settings.png)

## 2. Kali Linux Environment

This screenshot shows the Kali Linux environment used for the lab.

**Screenshot:**

![Kali Linux Installed](screenshots/2%20Kali%20Linux%20Installed.png)

## 3. Kali Linux Network Settings

I checked the network settings and identified the `eth0` interface and its IPv4 address.

**Screenshot:**

![Kali Network Settings](screenshots/3%20Kali%20Network%20Settings.png)

## 4. Network Testing and Verification

I used Linux networking commands to check the interface configuration and test connectivity.

### Check the operating system

```bash
cat /etc/os-release
```

This command displays information about the operating system and its version.

### Check the network interface

```bash
ip -br addr
```

**Observed `eth0` configuration:**

| Detail | Result |
|---|---|
| Interface | `eth0` |
| Status | UP |
| IPv4 Address | `10.0.0.2/24` |

### Check the routing table

```bash
ip route
```

I used this command to inspect the configured routes and understand how network traffic is directed.

For `eth0`, the observed network was `10.0.0.0/24`, with gateway `10.0.0.1`.

### Test the gateway connection

```bash
ping -c 3 10.0.0.1
```

**Result:** 3 packets received, with 0% packet loss.

### Test external IP connectivity

```bash
ping -c 3 8.8.8.8
```

**Result:** 3 packets received, with 0% packet loss.

Both tests were successful when I ran them. The external IP test confirmed connectivity to that IP address; DNS name resolution was not independently tested.

### Lab Verification Screenshot

![Lab Verification Results](screenshots/5%20Lab%20Verifications.png)

## 5. Network Troubleshooting

During troubleshooting, I used NetworkManager commands to modify a connection setting and reactivate the connection.

```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
sudo nmcli connection down "Wired connection 1"
sudo nmcli connection up "Wired connection 1"
```

These commands were used to update the connection setting and bring the specified connection down and back up.

### Troubleshooting Screenshot

![Network Troubleshooting](screenshots/4%20Fixing%20Internet%20Connectivity%20Issues%20for%20Kali%202026.png)

## What I Learned

Through this task, I gained practical experience with:

- Kali Linux and Oracle VirtualBox.
- Virtual machine network configuration.
- Linux network interfaces and IPv4 addressing.
- Routing tables and default gateways.
- Testing connectivity using `ping`.
- Using `ip`, `ping`, and `nmcli` commands.
- Recording technical steps and results with screenshots.

## Security and Ethical Practice

Cybersecurity testing should always be performed with proper authorization. I aim to use these skills responsibly in controlled lab environments and on systems where testing is explicitly permitted.

## Tools Used

- Kali Linux
- Oracle VirtualBox
- Linux Terminal
- NetworkManager

## References

- [Kali Linux](https://www.kali.org/)
- [Oracle VirtualBox](https://www.virtualbox.org/)
- [NetworkWalks Sample Repository](https://github.com/waqaskarimccie/NETWORKWALKS-B082-WK1-PM1-CYBERSECURITY-LAB-SETUP-SAMPLE)

---

**Author:** Revathi G.  
**Program:** NetworkWalks Cybersecurity Internship  
**Task:** Week 1 — Cybersecurity Lab Setup

*Learning by doing. Improving one lab at a time.*

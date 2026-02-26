# Wazuh SIEM Attack Detection Lab

## Project Overview

This project demonstrates the implementation of a Security Information
and Event Management (SIEM) lab using Wazuh to detect network attacks
and authentication failures in a controlled virtual environment.

The lab simulates real-world attack scenarios using Kali Linux and
monitors them through a Windows 10 endpoint integrated with a Wazuh
manager.

## Objectives

-   Deploy Wazuh SIEM in a local environment
-   Configure a Windows 10 agent for log collection
-   Enable advanced Windows auditing policies
-   Simulate network scanning attacks using Nmap
-   Detect firewall blocked traffic (Event ID 5152)
-   Detect brute force login attempts
-   Analyze alerts using MITRE ATT&CK mapping

## Lab Architecture

-   Wazuh Manager installed on WSL (Ubuntu)
-   Windows 10 Virtual Machine (Wazuh Agent installed)
-   Kali Linux Virtual Machine (Attacker machine)
-   VirtualBox Host-Only Network

The attacker machine performs reconnaissance and login attempts against
the Windows machine. The Windows Firewall blocks malicious traffic and
generates security logs, which are forwarded to the Wazuh Manager for
analysis and alerting.

## Attack Scenarios Simulated

### 1. Nmap SYN Scan Attack

Command used:

    nmap -sS <target-ip>

Detection: - Windows Event ID 5152 - Wazuh Rule ID 60104 - Security log:
Windows Filtering Platform blocked a packet

### 2. Brute Force Login Attempt

Detection: - Logon failure events - Rule ID 60122 - MITRE Techniques:
T1078, T1531

## Key Detection Events

-   Event ID 5152 -- Firewall blocked packet
-   Event ID 4625 -- Failed logon attempt
-   Event ID 4624 -- Successful logon
-   Wazuh rule-based correlation and alert generation

## Technologies Used

-   Wazuh SIEM
-   Windows 10
-   Kali Linux
-   Nmap
-   VirtualBox
-   Windows Advanced Audit Policy

## Results

-   Successful detection of network scan attempts
-   Real-time alert generation in Wazuh dashboard
-   MITRE ATT&CK mapping applied to detected events
-   Verification of firewall enforcement effectiveness

## Skills Demonstrated

-   SIEM deployment and configuration
-   Windows event log monitoring
-   Network attack simulation
-   Security event correlation
-   Threat detection and analysis
-   MITRE ATT&CK framework understanding

## Future Improvements

-   Custom Wazuh detection rules
-   Integration with threat intelligence feeds
-   Email alert automation
-   Active response configuration
-   Log forwarding to external SOC tools

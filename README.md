# Pyramid-of-Pain--TryHackMe--Cybersecurity-Learning-Journey
A comprehensive walkthrough and conceptual breakdown of the **Pyramid of Pain** room on TryHackMe. This repository documents my understanding of threat intelligence, Indicators of Compromise (IoCs), and how to effectively increase the cost of operations for adversaries.

# TryHackMe: Pyramid of Pain – Comprehensive Walkthrough & Notes

[![TryHackMe](https://img.shields.io/badge/TryHackMe-Pyramid%20of%20Pain-red?style=for-the-badge&logo=tryhackme)](https://tryhackme.com/room/pyramidofpainax)
[![Cybersecurity](https://img.shields.io/badge/Focus-Threat%20Intelligence%20%26%20Detection-blue?style=for-the-badge)](https://github.com/topics/cybersecurity)

A deep-dive documentation and practical write-up of the **Pyramid of Pain** room on TryHackMe. This repository serves as a comprehensive resource detailing threat intelligence concepts, Indicators of Compromise (IoCs), and strategies for shifting defense mechanisms from reactive to proactive by increasing the operational cost for adversaries.

---

## 🗺️ Overview: What is the Pyramid of Pain?

Designed by David J. Bianco, the **Pyramid of Pain** is a conceptual framework utilized in Cyber Threat Intelligence (CTI), Incident Response (IR), and Threat Hunting. It categorizes different types of Indicators of Compromise (IoCs) based on the level of "pain" or difficulty an organization inflicts on an adversary when those indicators are blocked or neutralized.

```
               /\
              /  \      TTPs (Tough)
             /____\     Tools (Challenging)
            /______\    Network/Host Artifacts (Annoying)
           /________\   Domain Names (Simple)
          /__________\  IP Addresses (Easy)
         /____________\ Hash Values (Trivial)

```
---
The core philosophy is simple: The higher up the pyramid you can detect and defend, the more devastating the impact on the attacker's operations.
🗂️ Detailed Tier-by-Tier Breakdown
1. Hash Values (Trivial)

    Definition: Mathematical representations of a fixed length uniquely identifying a specific file (e.g., MD5, SHA-1, SHA-256).

    Adversary Pain Level: Trivial (1/6)

    Why it's Trivial: Attackers can bypass hash-based detections instantly. By changing a single, non-functional bit of code or employing automated polymorphic compilation tools, the malware generates a completely new hash value while retaining its malicious capabilities.

    Defensive Tooling: VirusTotal, open-source threat intelligence feeds, local blocklists in Endpoint Detection and Response (EDR) agents.

2. IP Addresses (Easy)

    Definition: Network layer addresses used by adversaries to route malicious traffic, host Command & Control (C2) servers, or perform infrastructure scanning.

    Adversary Pain Level: Easy (2/6)

    Why it's Easy: IP addresses are inherently fluid. Attackers can quickly switch to a different bulletproof hosting provider, rotate through public VPNs, utilize Tor nodes, or route traffic via newly compromised residential proxies.

    Defensive Tooling: Firewalls, Network Security Monitoring (NSM), IP reputation databases (e.g., AbuseIPDB).

3. Domain Names (Simple)

    Definition: Human-readable web addresses mapped to IP addresses (e.g., malicious-phishing-update.com).

    Adversary Pain Level: Simple (3/6)

    Why it's Simple: Registering a new domain requires a minor financial cost and registration time, making it slightly more inconvenient than shifting an IP address. Furthermore, sophisticated adversaries use Domain Generation Algorithms (DGAs) to dynamically generate thousands of domains daily, keeping ahead of standard domain reputation blocklists.

    Defensive Tooling: DNS filtering (e.g., Cisco Umbrella), WHOIS lookup toolsets, DNS query log analysis.

4. Network & Host Artifacts (Annoying)

    Definition:

        Network Artifacts: Traces left during transit, such as unique HTTP User-Agent strings, specific URI patterns, or distinct TLS certificate handshakes.

        Host Artifacts: Traces left behind on an endpoint, including distinct registry keys, files dropped in specific paths, scheduled tasks, or unique service creation logs.

    Adversary Pain Level: Annoying (4/6)

    Why it's Annoying: Overcoming artifact-based detection requires the attacker to actively change their operational playbook or modify their codebase. It forces them to spend time reconfiguring their malware, sanitizing compilation variables, or varying their timing to avoid triggering heuristic alerts.

    Defensive Tooling: Sysmon, Event Viewer analysis, Wireshark, Zeek/Snort/Suricata IDS signatures.

5. Tools (Challenging)

    Definition: The actual software programs, scripts, or post-exploitation frameworks utilized by the adversary to execute the attack (e.g., Cobalt Strike, Mimikatz, BloodHound, or custom-compiled Python backdoors).

    Adversary Pain Level: Challenging (5/6)

    Why it's Challenging: At this level, defenders block the operational utility of an entire program rather than just a trace of it. If an organization signature-matches and blocks a specific tool across the enterprise, the adversary must invest massive resources into heavily obfuscating the code, writing a custom alternative tool, or discovering a new method entirely.

    Defensive Tooling: YARA rules, Antivirus/AMSI integration, advanced EDR behavior tracking.

6. TTPs (Tactics, Techniques, and Procedures)

    Definition: The overarching behavior, methodology, and operational strategies of the threat actor. This encompasses how they gain initial access, move laterally, maintain persistence, and achieve data exfiltration (mapped directly to frameworks like MITRE ATT&CK).

    Adversary Pain Level: Tough (6/6)

    Why it's Tough: This is the pinnacle of defense. TTPs represent how the human attacker thinks and operates. If you build a detection matrix that successfully renders an entire technique useless (e.g., catching all variations of LSASS memory dumping or Living-off-the-Land Binaries), you force the adversary to completely reinvent their entire attack methodology and retrain their operators.

    Defensive Tooling: MITRE ATT&CK mapping, behavioral analytics, threat hunting hypotheses, User and Entity Behavior Analytics (UEBA).

🛠️ Hands-on Exercises & Labs Completed

During the completion of this room, I engaged in practical exercises that demonstrated how to apply these conceptual layers:

    OSINT Investigation: Used VirusTotal and external threat feeds to extract and analyze known-malicious file hashes.

    Infrastructure Tracking: Utilized WHOIS protocols and DNS records to find patterns in malicious domain generation timelines.

    Data Transformation & Extraction: Applied CyberChef to decode obfuscated commands, look up base64-encoded strings, and reveal hidden indicators of compromise.

    Log Analysis: Reviewed host-level and network-level event configurations to trace where specific artifacts are dropped during an infection lifecycle.

🧠 Key Takeaways for Defensive Security

    Shift to Behavior: Traditional security architectures rely too heavily on the bottom three layers (Hashes, IPs, Domains) because they are easy to collect and block. However, true long-term security resilience lies in mastering the top three layers (Artifacts, Tools, TTPs).

    Resource Asymmetry: Effective detection engineering aims to tip the financial and operational scale. By focusing on TTP detection, we make it too costly and time-consuming for an attacker to successfully breach the network.
---

⚠️ Disclaimer

To adhere to TryHackMe’s Terms of Service and protect lab integrity, this repository contains conceptual frameworks, structural notes, and methodological insights. No direct flags or answers are published within.

---
My LinkedIn link: [https://www.linkedin.com/feed/update/urn:li:activity:7466030701671264256/]


#Cybersecurity #ThreatIntelligence #CyberThreatIntelligence #CTI #IncidentResponse #ThreatHunting #SOC #DetectionEngineering #MitreAttack #TryHackMe #BlueTeam #InfoSec

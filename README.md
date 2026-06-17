# Network Defense: VaultFin Services

> **Course:** Network Defense
> 
> **Path:** Junior Cybersecurity Analyst Career Path
> 
> **Scenario:** Layered network defense engagement for a mid-sized financial services firm
> 
> **Status:** Complete

---

## Client Scenario

**VaultFin Services** is a mid-sized financial firm handling customer transaction data and internal banking operations across two sites. A recent PCI-DSS compliance audit flagged critical gaps in perimeter security, access control, and log monitoring. This project documents the full remediation engagement — from defense posture assessment through firewall deployment, cryptographic controls, and SOC alert triage.

---

## What This Project Covers

All 11 modules of the Cisco Networking Academy Network Defense course, applied to the VaultFin scenario:

| Part | Type | Topic |
|---|---|---|
| 01 | Documentation | Defense-in-Depth Assessment |
| 02 | Documentation | Network Hardening and Segmentation |
| 03 | Documentation | AAA Framework and Access Control Policy |
| 04 | Packet Tracer | ACL Configuration on VaultFin-R1 |
| 05 | Documentation | Firewall Design and DMZ Architecture |
| 06 | Packet Tracer | ZPF Deployment on VaultFin-FW1 |
| 07 | Documentation | Cloud Security Posture Assessment |
| 08 | Documentation | Cryptographic Controls for Data and VPN |
| 09 | Documentation | Network Monitoring Protocol Configuration |
| 10 | Documentation | SIEM Architecture and Log Collection Framework |
| 11 | Documentation | SOC Alert Triage and Incident Evaluation |

---

## Key Skills Demonstrated

`Defense-in-Depth` `Network Hardening` `AAA / Access Control` `Standard ACLs` `Extended ACLs`
`Firewall Technologies` `Zone-Based Policy Firewall` `DMZ Design` `Cloud Security`
`Cryptography` `PKI` `VPN Concepts` `Syslog / SNMP / NetFlow` `SIEM Architecture`
`Alert Triage` `Security Policies` `Cisco IOS CLI` `Packet Tracer`

---

## Tools Used

| Tool | Purpose |
|---|---|
| Cisco Packet Tracer | ACL and ZPF firewall simulation |
| Cisco IOS CLI | Router and firewall device configuration |
| Security Documentation | Policy, analysis, and framework deliverables |
| SIEM Concepts | Log aggregation and alert correlation architecture |

---

## Network Topology

```
INTERNET (untrusted)
     |
[VaultFin-FW1]  -- Zone-Based Policy Firewall
     |         |
  [INSIDE]   [DMZ]
  VLANs 10    Web Server:   192.168.30.10
  20, 99      Email Relay:  192.168.30.20

VLAN 10   STAFF       192.168.10.0/24   General staff endpoints
VLAN 20   PAYMENTS    192.168.20.0/24   POS terminals, payment servers
VLAN 30   DMZ         192.168.30.0/24   Public-facing services
VLAN 99   MANAGEMENT  192.168.99.0/24   Admin access to network devices only
```

---

## Highlights

### Access Control Lists
Three ACLs configured on VaultFin-R1:
- `STAFF-TO-PAYMENTS-DENY` — blocks staff VLAN direct access to payments subnet
- `INTERNET-INBOUND-POLICY` — permits only DMZ traffic from internet; blocks all access to internal VLANs
- `MGMT-ACCESS-ONLY` — restricts SSH/VTY access to VLAN 99 only

### Zone-Based Policy Firewall
ZPF deployed on VaultFin-FW1 with three zones: INSIDE, PAYMENTS, OUTSIDE.
Default-deny between all zones. Only explicitly permitted zone-pair traffic passes.
PAYMENTS zone is fully isolated — no internet access permitted.

### SIEM Correlation Rules
Six correlation rules deployed:

| Rule | Name | Trigger | Severity |
|---|---|---|---|
| CR-01 | Brute Force Login | 5+ failed logins in 60s same source | HIGH |
| CR-02 | After-Hours Admin Login | Privilege-15 login after 20:00 | MEDIUM |
| CR-03 | Lateral Movement | 1 host to 10+ destinations in 5 min | HIGH |
| CR-04 | Data Exfiltration | 100MB+ outbound in 1 hour | HIGH |
| CR-05 | New Admin Account | Event ID 4720 + Domain Admins group | CRITICAL |
| CR-06 | Firewall Rule Disabled | FW1 syslog: ACL removed or changed | CRITICAL |

### Alert Triage
Five simulated SIEM alerts evaluated end-to-end:
- 3 true positives: external brute force, data exfiltration, backdoor admin account creation
- 2 false positives: after-hours IT maintenance, normal file server access

---

## Files in This Repository

| File | Description |
|---|---|
| `index.html` | Full project write-up (live via GitHub Pages) |
| `README.md` | This file |
| `topology.pkt` | Cisco Packet Tracer file — ACL and ZPF lab |
| `images` | Network Topology

---

## Links

- [Full Project Write-up](https://oziomainya.github.io/network-defense)
- [Portfolio](https://oziomainya.github.io)

---
*Ozioma Inya · [LinkedIn ↗](https://linkedin.com/in/ozioma-inya-a46327304) · [Github ↗](https://github.com/oziomainya)*

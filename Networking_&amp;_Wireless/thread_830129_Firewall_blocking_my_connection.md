---
title: "Firewall blocking my connection"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by adamsad1 on 2008-06-15
Every time I reboot my computer my network (wifi) connection is blocked until I turn the firewall off and back on. My network uses DHCP, but I don't have DDNS set up.

I've set Firestarter to allow all the connections/ports that it was showing it was blocking, but that still doesn't seem to help. The inbound policy is:

Allow 192.168.1.1 & 192.168.1.101

Allow port 80 (HTTP), 53 (DNS), and 5353 (MDNS) for the above IP addresses.

Outbound policy permissive by default.

Under Firestarter's Network Device Setup I have "IP address is assigned via DHCP" checked.

---


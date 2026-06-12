---
title: "Block all non-OpenVPN traffic"
date: 2018-09-06
forum: Networking &amp; Wireless
---

### Post by bubunta2018 on 2018-09-06
Hello! I found the script:

# ufw default deny incoming
# ufw default deny outgoing
# ufw allow out on XYZ to XXX.XXX.XXX.XXX
# ufw allow out on tun0
# ufw enable

  XYZ - virtual interface network card (wlp3s0, or eth0),  XXX.XXX.XXX.XXX - ip VPN-server. Seems good but my VPN provider gives me  dynamic ip. I tried to add istead XXX.XXX.XXX.XXX - 120.XXX.XXX.XXX,  120.0.0.0 and 120.**.**.* but ufw says - incorrect destination. What I should do?

How to add a rule for the ufw with IP range? I seen ip addresses such as 192.168.0.0/16 with numbers behind the slash. Where can I find the IP range table?

---


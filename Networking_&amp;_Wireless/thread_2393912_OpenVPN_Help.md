---
title: "OpenVPN Help"
date: 2018-06-09
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2018-06-09
I am trying to VPN into my network from my phone.  When I try to connect to my VPN server, it says "server poll timeout, trying next remote entry...".  Doing a tcpdump on my external interface for 1194 traffic, I am not seeing any.  I can not also telnet from my server to my IP via port 1194.  Does it matter if my phone is on my home wi-fi network while trying to vpn into the external network IP?  Also, I've added these IPtables rules to my firewall: [https://arashmilani.com/post?id=53](https://arashmilani.com/post?id=53).

---

### Post by gordintoronto on 2018-06-11
Did you set up port forwarding on your router?

---

### Post by sniper8752 on 2018-06-11
It's not a router, but a server with iptables.  Isn't that what the iptables forward chain is for?
Edit: I've enabled port forwarding in Ubuntu.

---

### Post by sniper8752 on 2018-06-16
*bump*

---


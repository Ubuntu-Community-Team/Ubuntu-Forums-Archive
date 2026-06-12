---
title: "TCP IP v 6 &amp; OpenVPN networking."
date: 2017-11-03
forum: Networking &amp; Wireless
---

### Post by Sami_Mattila on 2017-11-03
I can't seem to be able to pass ALL traffic trough my VPN. Only IPv4 traffic is routed normally trough my VPN.
ALL IPv6 traffic is routed normally by-passing the VPN tunnel.
I have tried to disable IPv6 on the the NetworkManager but apparently IPv6 Method "Disable" has no affect.
What now?

Sam

Ubuntu 17.10
64Bit

---

### Post by Sami_Mattila on 2017-11-03
Found a temp solution by disabling IPv6 while using VPN:

Disable:
sysctl -w net.ipv6.conf.all.disable_ipv6=1
Enable:
 sysctl -w net.ipv6.conf.all.disable_ipv6=0

Let me know if you can figure out a better solution.

Sam

PS. You can test IPv6 here: [http://ipv6-test.com/](http://ipv6-test.com/)

---


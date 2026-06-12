---
title: "How to route after vpn?"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by gregsheu on 2007-07-05
I need help to add route to ppp0 after I vpn to my company's Windows VPN server.
After I vpn, this is the result after route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 ath0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0


The ppp0 IP is 192.168.10.x, I can access the the server in the 192.168.10.x pool, but I can't access to 192.168.20.x servers pool, and I can't access to the internet after the vpn's connected. Can anyone show me how to route or is there another way to do this?
Thank you in advance.

---


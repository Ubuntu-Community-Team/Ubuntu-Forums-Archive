---
title: "PPP dialer high-speed acts different if lan is on"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by darkwave80 on 2007-10-09
If i have my lan on the route command shows
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
26.174.36.13    *               255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


if i have my lan off then it shows this for route.

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
13.sub-26-174-3 *               255.255.255.255 UH    0      0        0 ppp0
default         *               0.0.0.0         U     0      0        0 ppp0



So under destination it shows a different set of information for PPP0 if the "network" icon is diasbled on the bottom left.

but if i turn on the network and dial out then the top is what it shows and it does not browse the internet. which is the TOP route info.

I dont know enough about the network even though Im reading my ubuntu unleashed book which only gives illustrations of doing one thing at a time, not anything about having 2 network interfaces going on at once.

I just want to have the network card on which is running apache. and have my ppp work if i happen to dial out.

---


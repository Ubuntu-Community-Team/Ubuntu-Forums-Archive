---
title: "Network becomes very slow after some time"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by rayfidelity on 2008-04-08
Hi,

I've been having some strange problems after the last week's updates. The network works OK for some time (it varies from 1min to 2 hours) but then it becomes very slow (10kb/s on the LAN side!!!) i can barely get to the router...after a reboot everything is back to normal

i've tried renewing (sudo dhclient) and restarting (sudo /etc/init.d/networking restart) without success...only reboot helps...and then again after a few minutes/hours...

Ubuntu 7.10 (AMD64)
nVidia nForce 4 Pro
Wired network, eth0, DHCP (tried static too)
Linksys with tomato 1.17 (tried 1.16, 1.15, 1.13 with the same results...)

BTW: the network works fine on all other (windows) computer...

---


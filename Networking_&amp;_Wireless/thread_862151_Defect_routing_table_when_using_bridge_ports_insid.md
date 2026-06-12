---
title: "Defect routing table when using bridge_ports inside network/interfaces (8.4.1)"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by hfaber on 2008-07-17
Hi,

I'm trying to create a bridge using the bridge-utils package under kubuntu 8.04.1.

= /etc/network/interfaces =
[FONT="Courier New"]auto lo
iface lo inet loopback

# from [http://www.virtualbox.org/download/UserManual.pdf](http://www.virtualbox.org/download/UserManual.pdf)
auto br0
iface br0 inet dhcp
      bridge_ports eth0
[/FONT]===========================

This worked fine the first time I did a "/etc/init.d/network restart" ... However, whenever I reboot my machine the network is down, which is probably due to a defect routing table:

[FONT="Courier New"]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.4.0.0        *               255.255.255.0   U     0      0        0 br0
10.4.0.0        *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 br0
default         tor.xxxxxxx     0.0.0.0         UG    0      0        0 eth0
default         tor.xxxxxxx     0.0.0.0         UG    100    0        0 br0
[/FONT]
If I remove the routes using eth0 manually, the network is up again. Thread [http://ubuntuforums.org/showthread.php?t=807563](http://ubuntuforums.org/showthread.php?t=807563) seem to describe the same problem, but the solution found there (disabling the bridge) is no alternative to me, I'm afraid.

Does anybody have an idea where the ambiguous routes to eth0 may come from?

Regards

HFaber

---


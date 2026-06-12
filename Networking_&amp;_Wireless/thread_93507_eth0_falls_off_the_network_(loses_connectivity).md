---
title: "eth0 falls off the network (loses connectivity)"
date: 2005-11-22
forum: Networking &amp; Wireless
---

### Post by wizkrz on 2005-11-22
I have a RealTek 8139 that works, but seems to fall off of the LAN several times a day. It's not the card, because it worked for over a year without an issue running windoze.
The IP is static. When the issue occurs, I can ping the workstation IP, but can't ping the attached router. If I restart the network (/etc/init.d/networking restart) everything works. I can also get it to work if I "ifconfig eth0 down/up".

Has anyone seen this? Any help would be appreciated. I've been working with IP for a dozen or so years, but I'm fairly new to Linux.

Thanks!

---

### Post by souki on 2005-11-22
I can confirm, the link goes down and up
dmesg says:
> ...
[4294956.285000] r8169: eth1: link up
[4294963.668000] r8169: eth1: link up
[4295031.103000] r8169: eth1: PHY reset until link up
[4295041.103000] r8169: eth1: PHY reset until link up
[4295042.980000] r8169: eth1: link up
...

---


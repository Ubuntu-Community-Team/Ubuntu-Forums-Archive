---
title: "Network connectivity loss"
date: 2015-09-01
forum: Networking &amp; Wireless
---

### Post by Kerbi on 2015-09-01
I have an Ubuntu guest host on VMware.
Version 14.04.3 LTS, Trusty Tahr

Having an issue with the networking where on boot I am able to ping/connect to other hosts on the LAN. Other hosts on the network are able to connect to this host.
However, a very short time there after it stops working. 
If I do an ifdown/ifup same as on boot it starts working then stops after a very short time.

interface config:
auto eht0
iface eth0 inet static
address 255.255.254.0
gateway 172.20.10.1

There is no selinux and iptables is not installed.

I really am stumped here. Any ideas on how this can be fixed?

---


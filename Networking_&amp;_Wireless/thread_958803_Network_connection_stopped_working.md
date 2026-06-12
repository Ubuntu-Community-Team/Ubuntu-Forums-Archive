---
title: "Network connection stopped working"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by renova on 2008-10-25
My network connection stopped working suddenly. I'm running Ubuntu server 8.04. It's running virtually using Virtual PC 2007 on a Vista box. I've been running it for over 6 months with zero problems. Any help would be greatly appreciated. Thanks!

Results of ifconfig:

lo     Link encap:Local Loopback
       inet addr:127.0.0.1 Mask:255.0.0.0
       inet6 addr: ::1/128 Scope:Host
       UP LOOPBACK RUNNING MTU:16436 Metric:1

-----------------
/etc/network/interfaces:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

-----------------
Hosts file:

127.0.0.1        localhost
127.0.1.1        renovaLAMP

::1       ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by renova on 2008-10-25
It works now. I changed eth0 to eth1 and now it's back up. Not sure what happened.

---


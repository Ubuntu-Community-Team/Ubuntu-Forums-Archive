---
title: "network raise fails on restart for bond interfaces"
date: 2017-06-15
forum: Networking &amp; Wireless
---

### Post by bpasdar2 on 2017-06-15
Hello, 

I am running Ubuntu 17.04 using ifenslave two support two bonds (bond0 & bond1).  On boot the system functions as it is supposed to, however if I do a < sudo systemctl restart networking > networking goes down hard.  On investigation I see that ifensalve is trying to modify bond interface configuration by adding a config to a directory that does not exist. /sys/class/net/bond0.3004/**bonding** does not exist.

> 

Jun 15 14:15:15 ewr1-h002 sh[5290]: /etc/network/if-pre-up.d/ifenslave: 65: /etc/network/if-pre-up.d/ifenslave: cannot create /sys/class/net/bond0.3976/bonding/miimon: Directory nonexistent

Jun 15 14:15:15 ewr1-h002 sh[5290]: /etc/network/if-pre-up.d/ifenslave: 65: /etc/network/if-pre-up.d/ifenslave: cannot create /sys/class/net/bond0.3976/bonding/mode: Directory nonexistent

Jun 15 14:15:15 ewr1-h002 sh[5290]: /etc/network/if-pre-up.d/ifenslave: 65: /etc/network/if-pre-up.d/ifenslave: cannot create /sys/class/net/bond0.3976/bonding/lacp_rate: Directory nonexistent

Jun 15 14:16:15 ewr1-h002 sh[5290]: cat: /sys/class/net/bond0.3976/bonding/slaves: No such file or directory


I am bonding two GigE interfaces on bond0 and two TenGig interfaces on bond1.  On boot bonding with 802.3ad LACP works great.

Any help is appreciated.

Babak

---

### Post by bpasdar2 on 2017-06-21
update -  It seems that with ifenslave bonding no post-boot manipulation of the network is possible. When I manually try to take an interface down and bring it up again.  the master takes down the slaves.  For example with

> sudo ifenslave bond0.3976 eno1 eno2 

I get 

> sh: echo: I/O error
eno1: could not add interface

it then immediately takes down the first slave interface.  In this case eno1.

Suggestions are appreciated. 

Thanks,

Babak

---


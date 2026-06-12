---
title: "Virtualbox: no network on Guest after reboot!"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by vik69 on 2008-03-11
Hi all, i have several problems with Bridged Network on Virtualbox. After reboot i must allways make "sudo /etc/init.d/networking restart"  to have network access on guests (i becomme always this messagge "tap0 is not a slave of br0" tap1 is not a slave of br0" for every tap device). Here its my "Interfaces", i think its OK but maybe not:

```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet manual
adress 0.0.0.0

auto br0
iface br0 inet dhcp
bridge_ports eth1 tap0 tap1 tap2 tap3 tap4 tap5
bridge_maxwait 0

auto tap0
iface tap0 inet manual
up ifconfig $IFACE 0.0.0.0 up
down ifconfig $IFACE down
tunctl_user viktor

auto tap1
iface tap1 inet manual
up ifconfig $IFACE 0.0.0.0 up
down ifconfig $IFACE down
tunctl_user viktor

auto tap2
iface tap2 inet manual
up ifconfig $IFACE 0.0.0.0 up
down ifconfig $IFACE down
tunctl_user viktor

auto tap3
iface tap3 inet manual
up ifconfig $IFACE 0.0.0.0 up
down ifconfig $IFACE down
tunctl_user viktor

auto tap4
iface tap4 inet manual
up ifconfig $IFACE 0.0.0.0 up
down ifconfig $IFACE down
tunctl_user viktor

auto tap5
iface tap5 inet manual
up ifconfig $IFACE 0.0.0.0 up
down ifconfig $IFACE down
tunctl_user viktor

```


Please help me to solve this problem

Thanks
Vik

---


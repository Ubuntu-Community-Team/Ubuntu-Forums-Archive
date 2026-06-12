---
title: "[Cubieboard] No global IPv6 address after update of Ubuntu 14.04 to 16.04"
date: 2017-02-21
forum: Networking &amp; Wireless
---

### Post by c-korn on 2017-02-21
Hi,

after upgrading my Cubieboard (v4) from Ubuntu 14.04 to 16.04, the eth0 interface does not get a global IPv6 address any longer.
My ISP only gives my router a IPv6 addess, this is why I can only access the cubieboard from outside over IPv6.
```
$ ip addr show eth0
eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 06:91:c2:f1:e9:8b brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.100/24 brd 192.168.0.255 scope global eth0
    inet 192.168.0.20/24 brd 192.168.0.255 scope global secondary eth0
    inet6 fe80::491:c2ff:fef1:e98b/64 scope link
valid_lft forever preferred_lft forever
```

I also noticed this output in dmesg:
 
```
$ dmesg | grep eth0
[   20.575434] gmac0 gmac0: eth0: eth0: PHY ID 001cc915 at 0 IRQ poll     (gmac0-0:00)
[   31.115157] eth0: no IPv6 routers present
```

The output of dhclient also looks suspicious:
```
$ sudo dhclient -v -6
Internet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
Listening on Socket/wlan0
Sending on   Socket/wlan0
Listening on Socket/p2p0
Sending on   Socket/p2p0
Listening on Socket/eth0
Sending on   Socket/eth0
no link-local IPv6 address for bond0
If you think you have received this message due to a bug rather
than a configuration issue please read the section on submitting
bugs on either our web page at www.isc.org or in the README file
before submitting a bug.  These pages explain the proper
process and the information we find helpful for debugging..
exiting.
```

The cubieboard still has this kernel running:
 
```
$ uname -r
3.4.39
```
Also I don't know how to upgrade the kernel on this board, if it has anything to do with it.
 

On my PC with Ubuntu 16.10 the global IPv6 address is successfully given.
So the fault cannot be the router.

---

### Post by c-korn on 2017-02-26
Solved the problem by deleting the .leases files in the directory **/var/lib/dhcp/ **and running **sudo dhclient -6 eth0**.

---


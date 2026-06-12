---
title: "DHCP problem"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by bobberu on 2006-11-14
I've just installed Ubuntu on top of Fedora Core 4 in a dual boot system with XP. Both FC4 and XP were happy with my Linksys router, but I can't seem to obtain an IP with Ubuntu. I tried enabling/disabling through the Networking GUI tool, but no luck. So I applied my small amount of networking knowledge on the command line and still nothing happened. Below is a copy of the command line stuff. Help would be appreciated!

Thanks...

```
bob@bob-desktop:~$ sudo ifdown eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:80:ad:8a:30:d2
Sending on   LPF/eth0/00:80:ad:8a:30:d2
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
bob@bob-desktop:~$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:80:ad:8a:30:d2
Sending on   LPF/eth0/00:80:ad:8a:30:d2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by bobberu on 2006-11-19
Just in case anyone's interested....I changed the kernel from 2.6.15-23 to 2.6.15-27 and the problem disappeared!

---


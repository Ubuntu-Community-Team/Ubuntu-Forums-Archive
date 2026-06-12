---
title: "No DHCP Offers Recieved"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by stormblue on 2006-08-02
Hello,

I've had my wireless card working in the past and it no longer works correctly.  I didn't change anything that I can think of. However, our power did go out, but the router was plugged into a surge protector and everything else seems to function fine and I started to have problems before this.  Here is the output when I request DHCP

```
bluestorm@blackbox-4du8nm:~$ sudo dhclient eth2
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth2/00:02:6f:21:c5:cc
Sending on   LPF/eth2/00:02:6f:21:c5:cc
Sending on   Socket/fallback
DHCPREQUEST on eth2 to 255.255.255.255 port 67
DHCPREQUEST on eth2 to 255.255.255.255 port 67
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
Trying recorded lease 192.168.1.3
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 1.318/1.318/1.318/0.000 ms
bound: renewal in 30903 seconds.
bluestorm@blackbox-4du8nm:~$
```

I changed the DHCP range on my router to 192.168.1.50 - 192.168.1.75 to see if it would pick up something in that range and it didn't.

Problem solved via commenting out IPv6 via instructions found on forum!

---


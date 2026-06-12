---
title: "Xubuntu Network Problem"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by alejo on 2007-03-01
I have a router with 3 pc connected to this.. All works nice. 
The las weekend my brothers arrive for vacations and put his wireless router, for use his notebook too.
Now he is gone, and let my old router, but one pc cant connect to inet...

This are some log... from this machine

> gerardo@radiation:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0D:88:B6:1A:3D
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x9400

gerardo@radiation:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:0d:88:b6:1a:3d
Sending on   LPF/eth0/00:0d:88:b6:1a:3d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

gerardo@radiation:~$ cat /etc/resolv.conf
search localdomain
nameserver 192.168.0.1
domain RUCA

gerardo@radiation:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


please help me... I cant found the problem... the another 2 pc are working nice.

---

### Post by tgalati4 on 2007-03-01
Welcome to the forums.

My guess is that the wireless router created a new gateway that is still stored on that port.

I would disconnect all of your ethernet cables, unplug the router, unplug your cable/dsl modem.

Then plug them back in the following order:  cable/dsl modem first.  then router, then each PC one at a time.

Each machine should be able to:

sudo ping 192.168.0.1

If not then there is a subtle problem that needs further investigation.

Let us know how it turns out.

---

### Post by alejo on 2007-03-02
Its so rare... I unplug and plug all the cables many times. 
But now it works... I dont know what happends, but now is working.

Sorry.

---

### Post by tgalati4 on 2007-03-03
We're glad you're back online.  Now you can help others!

---


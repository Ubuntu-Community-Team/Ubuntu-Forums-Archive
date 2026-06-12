---
title: "Weird Netgear WG111 Problems"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by Shyper on 2007-07-14
Alright, I've ndiswrapper'd my new Netgear WG111 USB Adapter's drivers to the point that the computer seems to recognize the device and can see wireless networks in range. Whenever I try to connect to my wireless network, my computer will randomly do one of two things:

1. The network thing on the toolbar will spin for a while, and one of the lights will turn green (the lower left one) - however, it'll just stop there and eventually time out.

2. I'll successfully connect to the network, but only for a period of 6 seconds-5 minutes. After that, it kicks me off, at which point it reverts to Task 1 when I try to reconnect.

I'm using Feisty Fawn (7.04) and am pretty much a total Linux newb. The router I'm using for this is a Westell 327w. I'm almost inclined to think it's a problem with the USB not playing nice with the router.

The LSUSB is as follows:
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 007 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 007 Device 002: ID 413c:2003 Dell Computer Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 03f0:0904 Hewlett-Packard DeskJet 845c
Bus 003 Device 002: ID 1058:0404 Western Digital Technologies, Inc.  --> External HD
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 010: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2) --> The adapter.
Bus 002 Device 007: ID 06a9:000e Westell --> Other, unrelated adapter that's unndiswrapperable.
Bus 002 Device 001: ID 0000:0000  

The ifconfig is...

eth0      Link encap:Ethernet  HWaddr 00:19: D1:69:7A:F4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xecc0 Memory:dfde0000-dfe00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2739 (2.6 KiB)  TX bytes:2739 (2.6 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:1B:2F:3C:81:55  
          inet6 addr: fe80::21b:2fff:fe3c:8155/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:40672 (39.7 KiB)

wlan0:ava Link encap:Ethernet  HWaddr 00:1B:2F:3C:81:55  
          inet addr:169.254.4.219  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-2F-3C-81-55-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Can anyone help me at all? I've been googling for about four days now, and I'm stumped. I'm pretty sure the adapter's installed correctly. Thanks in advance.

---

### Post by Shyper on 2007-07-15
Bump?

---

### Post by Shyper on 2007-07-16
Huh. Alright, I've solved it, but it's really, really weird still. Evidently, when using the Westell 327w router, you can only connect with the Netgear USB adapter *while someone else is also connected using a Westell USB adapter*. Weird, like I said.

---


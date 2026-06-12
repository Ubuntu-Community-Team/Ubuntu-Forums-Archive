---
title: "How do you automatically connect to your router?"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by bigyoy on 2007-02-18
Hi - I'm still getting used to linux so bear with me...

Sometimes I start my computer with my router turned off, so when linux has booted up and i turn the router on, it does not seem to automatically connect to it.

What do I need to do to get it to connect?

thanks

---

### Post by solar george on 2007-02-18
When you have booted up your computer with the router turned on open a terminal window and type;

```
$ ifconfig
```

This will give you information about your network e.g.

```
**eth0**      Link encap:Ethernet  HWaddr 00:D0:59:C0:D4:BF  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fec0:d4bf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:85239 (83.2 KiB)  TX bytes:6354 (6.2 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

In the example eth0 is the name of the adapter (this is likely to be the same for you but you may have wlan0 if you are using wireless)

When you have booted the computer without the router attached open a terminal and type
```
george@george-laptop:~$ **sudo ifdown eth0**
Password: (Enter your password)
There is already a pid file /var/run/dhclient.eth0.pid with pid 4365
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:d0:59:c0:d4:bf
Sending on   LPF/eth0/00:d0:59:c0:d4:bf
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.30 port 67
george@george-laptop:~$ **sudo ifup eth0**
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:d0:59:c0:d4:bf
Sending on   LPF/eth0/00:d0:59:c0:d4:bf
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.0.30
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.30
SIOCADDRT: Network is unreachable
bound to 192.168.0.11 -- renewal in 9218 seconds.

```

The bits in bold are what you actually type. Replace eht0 with the name your adapter.
The rest is just the type of output you will get.

---

### Post by bigyoy on 2007-02-18
thank you - I'll give this a try next time and let you know if I have any problems

---


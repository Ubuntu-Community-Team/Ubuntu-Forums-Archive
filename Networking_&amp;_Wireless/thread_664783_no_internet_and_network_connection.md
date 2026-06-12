---
title: "no internet and network connection"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by laminaatplaat on 2008-01-11
I'm trying to run Ubuntu 7.10 on my desktop that I use on a daily basis. But I can't get my computer connected to the internet and network :(

```

guy@guy-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:DC:7B:72:CC  
          inet6 addr: fe80::210:dcff:fe7b:72cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:2914 (2.8 KB)
          Interrupt:21 Base address:0xf00 

eth0:avah Link encap:Ethernet  HWaddr 00:10:DC:7B:72:CC  
          inet addr:169.254.8.254  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0xf00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:704 (704.0 b)  TX bytes:704 (704.0 b)

guy@guy-desktop:~$


```

The eternet port is on my motherboard and I'n not sure what type it is. the pc is a Pentium 4 fujitsu siemens scaleo 600. The router it is connected to is a linksys WRT54g in DHCP mode. I dont think there is a problem with the router because an ubuntu laptop i tested with did work automaticly with that router.

---

### Post by laminaatplaat on 2008-01-11
```

guy@guy-desktop:~$ sudo ifdown eth0:avah
[sudo] password for guy:
ifdown: interface eth0:avah not configured
guy@guy-desktop:~$ sudo ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 5222
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:10:dc:7b:72:cc
Sending on   LPF/eth0/00:10:dc:7b:72:cc
Sending on   Socket/fallback
guy@guy-desktop:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:10:dc:7b:72:cc
Sending on   LPF/eth0/00:10:dc:7b:72:cc
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
guy@guy-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:DC:7B:72:CC  
          inet6 addr: fe80::210:dcff:fe7b:72cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:273 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:77169 (75.3 KB)
          Interrupt:21 Base address:0xf00 

eth0:avah Link encap:Ethernet  HWaddr 00:10:DC:7B:72:CC  
          inet addr:169.254.8.254  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0xf00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1056 (1.0 KB)  TX bytes:1056 (1.0 KB)

guy@guy-desktop:~$

```

on the Dutch Ubuntu forum they gave me some tips to get it working, but it doesnt work. could realy use some help :(

---


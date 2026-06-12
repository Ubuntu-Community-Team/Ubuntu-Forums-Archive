---
title: "Wireless Problem"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by pritamps on 2007-12-27
I made a post about a strange wireless problem, and got no reply. I tried repairing it on my own and now wireless doesn't work at all :)

Wicd lists the wireless connections available, but then stops at "Obtaining IP address" and does not connect at all. Not to a secured network and not to an unsecured network either :(

I'm using a Trendner TEW424UB 3.0R USB wireless card on a Dell Latitude 131L with AMD Sempron, 2 GB RAM. I don't know what information is relevant, so it's all there...

The output of iwconfig is :
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"UIUCnet"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0C:E6:00:13:01   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:40/100  Signal level:-70 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by KCPokes on 2007-12-27
In this case, is this a secure or nonsecure network?  What is the output of your ifconfig -a?  Additionally, have you tried to bring the interface down and back up via commandline?  For whatever reason, when I change/add new connections I normally have to bring the interface down and back up via command line for it to work.

---

### Post by pritamps on 2007-12-30
Hey,

The output of ifconfig -a is :

```
eth0      Link encap:Ethernet  HWaddr 00:19:B9:64:1A:94  
          inet addr:128.174.133.5  Bcast:128.174.133.255  Mask:255.255.254.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38837 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22448 errors:0 dropped:0 overruns:0 carrier:0
          collisions:7318 txqueuelen:1000 
          RX bytes:25299730 (24.1 MB)  TX bytes:2160600 (2.0 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7190 (7.0 KB)  TX bytes:7190 (7.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:D1:39:78:6B  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

I followed this thread : 
 to try and connecting from the commandline, but this is the error I got :

```
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
UIUCnet: ERROR while getting interface flags: No such device
UIUCnet: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

```

-Pritam

---

### Post by pritamps on 2008-01-01
Bump Bump

---


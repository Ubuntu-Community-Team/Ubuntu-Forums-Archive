---
title: "Printer and Internet connection Problems"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by nhi on 2007-04-17
Hey i've just started to use ubuntu and ihave a problem

The Problem is internet connection problem I was told yesterday to post my ifconfig so one of the other ubuntu's will help me to recognize the problem, however the sympthoms are that the web browser stop loading new websites after a while and new downloads does seem to start however downloads at the middle of the process continue :confused: 
any idea what's the problem? 

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:18:F3:BD:60:F2  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:febd:60f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9804 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9895 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7807476 (7.4 MiB)  TX bytes:1437514 (1.3 MiB)
          Interrupt:209 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:55 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3353 (3.2 KiB)  TX bytes:3353 (3.2 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:82.81.166.242  P-t-P:82.81.166.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:1894 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1934 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:893688 (872.7 KiB)  TX bytes:226247 (220.9 KiB)

---

### Post by dmizer on 2007-04-17
blacklist ipv6.

```
gksudo gedit /etc/modprobe.d/blacklist
```
and add the phrase:
```
blacklist ipv6
```
to the end of the file.  save, reboot, all should be well.

---

### Post by nhi on 2007-04-18
> **dmizer said:**
> blacklist ipv6.

```
gksudo gedit /etc/modprobe.d/blacklist
```
and add the phrase:
```
blacklist ipv6
```
to the end of the file.  save, reboot, all should be well.

thanks but...

It didn't help any other idea?

by the way ifconfig now is:
eth0      Link encap:Ethernet  HWaddr 00:18:F3:BD:60:F2  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11593 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10927 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9091586 (8.6 MiB)  TX bytes:1724093 (1.6 MiB)
          Interrupt:209 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5272 (5.1 KiB)  TX bytes:5272 (5.1 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:88.155.30.237  P-t-P:88.155.30.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:495 errors:0 dropped:0 overruns:0 frame:0
          TX packets:506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:380214 (371.3 KiB)  TX bytes:76099 (74.3 KiB)

---


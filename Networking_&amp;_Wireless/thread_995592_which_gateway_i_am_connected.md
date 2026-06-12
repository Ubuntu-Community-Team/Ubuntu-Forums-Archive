---
title: "which gateway i am connected"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by jagdishrao on 2008-11-28
hello all

i am running ubuntu intrepid ibex on acer 4710 laptop
we have 2 routers at our office
one has a gateway ip as 192.168.0.1 and other has 192.168.0.254
i had auto connected to eth0 i.e the ethernet card.

i would like to know the command which shows 
which router i am connected to
=========================================================
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d3:e7:98:dc  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fee7:98dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:4009 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2703529 (2.7 MB)  TX bytes:595492 (595.4 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:1b:77:6d:9b:39  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:317420 (317.4 KB)  TX bytes:317420 (317.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-6D-9B-39-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



regards
jags

---

### Post by mechanicalturk on 2008-11-28
Try using traceroute.  Something like
```
traceroute www.google.com
```
will show you in the first line of output which router you're connected through.

If you don't have traceroute you can
```
sudo apt-get install traceroute
```

---


---
title: "iBurst Problem on Gusty"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by mybuffalo on 2008-01-19
Hi All,

After two weeks of trying, I finally managed to install iBurst but I can't go online. 

From ifconfig I get these:

eth0      Link encap:Ethernet  HWaddr 00:1B:38:9B:FA:26  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe9b:fa26/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:2622 (2.5 KB)
          Interrupt:21 

ib0       Link encap:Ethernet  HWaddr 00:C0:EE:18:01:C1  
          inet6 addr: fe80::2c0:eeff:fe18:1c1/64 Scope:Link
          UP BROADCAST RUNNING NOARP DYNAMIC  MTU:1500  Metric:1
          RX packets:192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8428 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5975 (5.8 KB)  TX bytes:71523 (69.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5712 (5.5 KB)  TX bytes:5712 (5.5 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:116.206.76.39  P-t-P:116.206.1.8  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1400  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1444 (1.4 KB)  TX bytes:1156 (1.1 KB)

I can ping 116.206.76.39 and 116.206.1.8, but I can't ping the DNS IPs 116.206.0.35/36.  The message is network is unreachable.

I appreciate it if anyone can help me cause I don't want to go back to Windows if I can.

Thanks in advance.

---


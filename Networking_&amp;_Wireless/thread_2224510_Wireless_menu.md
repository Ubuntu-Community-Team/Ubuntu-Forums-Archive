---
title: "Wireless menu"
date: 2014-05-16
forum: Networking &amp; Wireless
---

### Post by smss on 2014-05-16
Hi everybody,
My wireless menu has been lost since last session of my computer.
Although I work with it in the last session of my P.C, I can't see my wireless menu because it has been lost.
I have installed the driver in the past, And I got connected with it, but now the wireless does NOT appear!

You can see the output of these commands below: lspci, ifconfig
```

smss@smss-network:~$ lspci | grep Network
00:19.0 Ethernet controller: Intel Corporation 82567LM-2 Gigabit Network Connection
07:02.0 Network controller: Ralink corp. RT3060 Wireless 802.11n 1T/1R
smss@smss-network:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:f3:b1:5c  
          inet6 addr: fe80::21c:c0ff:fef3:b15c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43 errors:0 dropped:5 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11136 (11.1 KB)  TX bytes:12255 (12.2 KB)
          Interrupt:20 Memory:d1300000-d1320000 

eth1      Link encap:Ethernet  HWaddr 00:26:5a:95:a3:a1  
          inet6 addr: fe80::226:5aff:fe95:a3a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7285 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4391714 (4.3 MB)  TX bytes:980689 (980.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8334 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8334 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:565449 (565.4 KB)  TX bytes:565449 (565.4 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:*.*.*.*  P-t-P:*.*.*.*  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:6191 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:4326873 (4.3 MB)  TX bytes:803215 (803.2 KB)

smss@smss-network:~$ 


```

Thanks for any suggestion.

---

### Post by smss on 2014-05-16
Seems that the wireless card disabled at all ! 
I replace it with another one at now, and hand over it to guarantor company.

---


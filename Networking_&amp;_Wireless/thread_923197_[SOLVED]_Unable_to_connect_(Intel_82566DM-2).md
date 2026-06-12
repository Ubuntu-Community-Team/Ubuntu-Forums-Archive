---
title: "[SOLVED] Unable to connect (Intel 82566DM-2)"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by achelis on 2008-09-18
Hi

I've just installed Hardy (32-bit) on my computer, but I'm unable to connect to the network. 

Output from ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:1c:c4:d6:64:87  
          inet addr:10.12.66.195  Bcast:10.12.66.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c4ff:fed6:6487/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1542 (1.5 KB)  TX bytes:6991 (6.8 KB)
          Memory:f0180000-f01a0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1492 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1492 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74600 (72.8 KB)  TX bytes:74600 (72.8 KB)

```

Output from lspci
```

00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)

```

I'm fairly new to Ubuntu, so any help would be appreciated :)

---

### Post by sonicb00m on 2008-10-06
How was this solved? I also have this problem.

---


---
title: "[ath0 + eth0]"
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by max_dev on 2008-02-08
Can use at the same time ath0 and eth0 in Ubuntu or not? 
 When I bring up ath0 automatically bring down eth0. 
 When I bring up eth0 automatically bring down ath0. 
 So either I connect via wireless or cable. 
 But I need to use at the same time ath0 and eth0. 
 Following data. 
 
 Thanks

```
ifconfig -a

ath0      Link encap:Ethernet  HWaddr 00:16:CF:34:0F:1E
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cfff:fe34:f1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:699 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:216946 (211.8 KB)  TX bytes:5571 (5.4 KB)

eth0      Link encap:Ethernet  HWaddr 00:16:D4:18:9B:8B
          inet addr:192.168.1.85  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe18:9b8b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:471 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:28368 (27.7 KB)
          Interrupt:21 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:28540 (27.8 KB)  TX bytes:28540 (27.8 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-16-CF-34-0F-1E-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16780 errors:0 dropped:0 overruns:0 frame:47237
          TX packets:168 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:1780626 (1.6 MB)  TX bytes:12623 (12.3 KB)
          Interrupt:22
```

---

### Post by max_dev on 2008-02-09
Si? No?

---


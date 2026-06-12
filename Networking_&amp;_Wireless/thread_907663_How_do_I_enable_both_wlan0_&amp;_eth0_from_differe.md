---
title: "How do I enable both wlan0 &amp; eth0 from different subnets?"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by pokipoki08 on 2008-09-01
I can get wlan0 & eth0 working, but only one at a time.

Q1 How do I get both to be working at the same time?

Q2 How do I add a default gateway for each device?

Thanks.

```
eth0      Link encap:Ethernet  HWaddr 00:16:cb:98:a1:79  
          inet6 addr: fe80::216:cbff:fe98:a179/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:243558 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11391509 (10.8 MB)  TX bytes:468 (468.0 B)
          Interrupt:16 

wlan0     Link encap:Ethernet  HWaddr 00:0e:2e:4c:78:f6  
          inet addr:192.168.100.5  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::20e:2eff:fe4c:78f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24139490 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30373200 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3794287972 (3.5 GB)  TX bytes:4191441251 (3.9 GB)

```

---


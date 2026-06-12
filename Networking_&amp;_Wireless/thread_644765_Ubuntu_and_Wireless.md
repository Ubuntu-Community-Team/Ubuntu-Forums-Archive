---
title: "Ubuntu and Wireless"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by Caghkan on 2007-12-19
Hi all. I have a problem with my wireless network. My ubuntu don't see my wireless connection. We have a wireless connection, but my ubuntu don't see it! There is no wireless network! What should I do? I have installed WLAN software etc, but it doesn't work. Otherwise, when I log into Windows Vista, it sees my wireless connection. Please help me!

---

### Post by mellowd on 2007-12-19
Open up a terminal and type this:

```
ifconfig
```

What do you see?

---

### Post by Caghkan on 2008-03-05
I see these.

eth0      Link encap:Ethernet  HWaddr 00:1B:38:3E:F4:56  
          inet addr:139.179.199.104  Bcast:139.179.199.255  Mask:255.255.254.0
          inet6 addr: fe80::21b:38ff:fe3e:f456/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24817 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8297 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11383343 (10.8 MB)  TX bytes:1274631 (1.2 MB)
          Interrupt:18 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

PS: I am sorry to late post. I wasn't here temporary.

---

### Post by Caghkan on 2008-03-05
Hey! Is anyone there?

---


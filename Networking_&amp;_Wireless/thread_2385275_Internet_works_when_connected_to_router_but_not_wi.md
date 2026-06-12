---
title: "Internet works when connected to router but not with cable"
date: 2018-02-18
forum: Networking &amp; Wireless
---

### Post by elsherif27 on 2018-02-18
I can't get the internet to work when I connect via cable but the net works when connected to a router using to the same cable. I tried another laptop with mint and the same problem occurs while the ethernet works fine on windows.

This is the output of ifconfig on cable:
```

enp1s0    Link encap:Ethernet  HWaddr c8:5b:76:24:a1:ae  
          inet6 addr: 2001:638:208:d800:b4b0:382f:3a62:e191/64 Scope:Global
          inet6 addr: fe80::ffdf:f9f8:9f6b:ab5d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8858 errors:0 dropped:0 overruns:0 frame:0
          TX packets:701 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1089733 (1.0 MB)  TX bytes:137678 (137.6 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:31582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31582 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:2537744 (2.5 MB)  TX bytes:2537744 (2.5 MB)

```

And this is the output when connected to the router:
```

wlp2s0    Link encap:Ethernet  HWaddr b8:81:98:44:e6:b6  
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::32eb:58f:d290:547d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1942216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2349426 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1800622608 (1.8 GB)  TX bytes:2395620006 (2.3 GB)

```

---


---
title: "New Kernel"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by Sub101 on 2008-07-25
Hiya, i just upgraded to kernel -20 and my system has lost its wireless. The drivers it used were restricted Intel® PRO/Wireless 3945ABG Network Connection but it is no longer in the restricted drivers.
```
lo        no wireless extensions.

eth0      no wireless extensions.


```

```
eth0      Link encap:Ethernet  HWaddr 00:16:d3:fc:fa:ae  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fefc:faae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5573 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5584 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2815337 (2.6 MB)  TX bytes:863331 (843.0 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:600 (600.0 B)  TX bytes:600 (600.0 B)


```

Any ideas? Thanks

---

### Post by superprash2003 on 2008-07-25
Please post lshw -C network output

---


---
title: "I installed ubuntu fresh today on my computer and the wired network isn't working"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by grandpa2390 on 2008-06-17
i dont know what to do, ive never had this problem before.

---

### Post by rlzyoner on 2008-06-17
What is the output of ifconfig

---

### Post by grandpa2390 on 2008-06-17
eth0 link encap:Ethernet HWaddr 00:11:43:5e:2c:50
     UP BROADCAST MULTICAST MTU:1500 Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:1000
     RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
     Interrupt:7

lo   Link encap:Local Loopback
     inet addr: 127.0.0.1 Mask:255.0.0.0
     inet6 addr: ::1/128 Scope:Host
     UP LOOPBACK RUNNING MTU:16436 Metric:1 
     RX packets:1380 errors:0 dropped:0 overruns:0 frame:0
     TX packets:1380 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:0
     RX bytes:69000 (67.3 KB) TX bytes:69000 (67.3 B)


this is without ethernet plugged in, if you want me to do it with the cable plugged in, tell me please

---

### Post by grandpa2390 on 2008-06-17
i went ahead and did it with ethernet plugged in and i got the same results

---

### Post by Iowan on 2008-06-17
Verify that "Enable roaming mode" is unchecked (Under Manual Configuration).

---


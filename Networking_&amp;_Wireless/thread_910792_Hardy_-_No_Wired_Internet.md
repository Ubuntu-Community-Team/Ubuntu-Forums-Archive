---
title: "Hardy - No Wired Internet"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by bchen8341 on 2008-09-04
Hi, just switched to hardy like 2 days ago. My internet worked for perhaps a day and is now no longer working. I didn't change anything. I have a wired connection without any routers or anything. Everytime I try to restart the connection (by clicking on the networking icon and enabling/disabling it), it always spends a long time "requesting a network address", but after it finishes that internet still doesnt work. I'm pretty sure its the machine because internet works fine on a windows computer. I tried both "roaming mode" and DHCP but they both don't work. Can anyone help me?

---

### Post by bchen8341 on 2008-09-05
Oh, and I just noticed that if I unplug the internet cable from my linux computer and plug it into my windows computer, wait for it to connect/get network address and then replug it back into the linux computer, internet works. But then after a while it stops working again, and I have to redo the whole thing. Anyone has any ideas?

---

### Post by Crafty Kisses on 2008-09-05
Post the results of this command: ```
ifconfig
```

---

### Post by bchen8341 on 2008-09-05
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:9e:f0:e3  
          inet addr:206.223.233.48  Bcast:206.223.233.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101551 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12342485 (11.7 MB)  TX bytes:2347428 (2.2 MB)
          Interrupt:252 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:775 errors:0 dropped:0 overruns:0 frame:0
          TX packets:775 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69233 (67.6 KB)  TX bytes:69233 (67.6 KB)

---


---
title: "Unable add/remove-no connectivety"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by dlolson on 2009-05-19
Installed U 8.04 Dual boot with winxp. The operating system will not recognize the internet connection. Firefox in Ubuntu works okay and XP works.
Here is the result of ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:17:31:C0:5E:89  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fec0:5e89/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:940 errors:0 dropped:0 overruns:0 frame:0
          TX packets:789 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1103726 (1.0 MiB)  TX bytes:192310 (187.8 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

I cant update or install with add/remove as it cant find connection. 
Have rebooted, system and router to no avail. What's up?

---

### Post by porchrat on 2009-05-19
Weird man.

So basically what you are saying is that Firefox works, but you can't access the various repositories?

Is it just some repositories or all of them?

---

### Post by plucky on 2009-05-19
Check your sources.list.Open a terminal (**Applications > Accessories > Terminal**)and post output of```
cat /etc/apt/sources.list
``` or go to **System > Administration > Software Sources** and make sure the boxes are ticked.(See attachments)

Good Luck

---


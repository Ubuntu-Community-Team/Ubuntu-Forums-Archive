---
title: "What can detect and close unwanted Net connections?"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by DonaldJ on 2009-02-20
Which are the best softwares, for Ubuntu, that show me in real-time, every active connection to and from the Internet.. and permit me to permanently close the connections that I don't want connecting to my PC..?

---

### Post by handydan918 on 2009-02-20
See man netstat

---

### Post by Archmage on 2009-02-20
There are HUNDERTS out there. I did use firestarter for some time.

---

### Post by superprash2003 on 2009-02-20
etherape

---

### Post by DonaldJ on 2009-02-21
Thanks...

I installed EtherApe, but when I click it up I get a pop-up, "Error getting device. No suitable device found"...

---

### Post by superprash2003 on 2009-02-21
in your terminal type **ifconfig** and post output

---

### Post by DonaldJ on 2009-02-21
eth0      Link encap:Ethernet  HWaddr 00:05:5d:f4:88:8d  
          inet addr:******** Bcast:******** Mask:**********
          inet6 addr: fe80::****:5dff:fef4:888d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14559 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12759 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:15040732 (15.0 MB)  TX bytes:1780021 (1.7 MB)
          Interrupt:17

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7728 (7.7 KB)  TX bytes:7728 (7.7 KB)

---

### Post by superprash2003 on 2009-02-22
run etherape as ROOT..

---

### Post by DonaldJ on 2009-02-22
Look like I found what I wanted...


[http://ubuntuforums.org/attachment.php?attachmentid=20949&d=1165960838](http://ubuntuforums.org/attachment.php?attachmentid=20949&d=1165960838)

---

### Post by hobo on 2009-02-22
What program is it? I figured it out.....

---

### Post by DonaldJ on 2009-02-22
Don't know yet..  but if you follow the last posts in the thread you will probably find out...

---

### Post by raydeen on 2009-02-22
:lolflag: at the machine name. Commodore 64 ftw!

---


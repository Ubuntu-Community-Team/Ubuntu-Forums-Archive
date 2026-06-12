---
title: "Internet Sharing with Firestarter (or anything) to get Xbox Live working"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by ncraig on 2007-11-04
So with Vista I could just click share internet... now I love Ubuntu and if I can get this to work I can become 100% a Ubuntu user...

When I start up Firestarter and I choose my eth1 (wireless) as my internet device, and then eth0 (my wired) as my local connection then I attempt to start the firewall but it says that eth0 is not ready.  

when I ifconfig I get this:

eth0      Link encap:Ethernet  HWaddr 00:1B:24:AA:A1:81  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30778 (30.0 KB)  TX bytes:7596 (7.4 KB)
          Interrupt:17 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:1C:BF:07:54:80  
          inet addr:10.14.5.91  Bcast:10.14.255.255  Mask:255.255.0.0
          inet6 addr: fe80::21c:bfff:fe07:5480/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13792 errors:9432 dropped:10929 overruns:0 frame:0
          TX packets:1864 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3625261 (3.4 MB)  TX bytes:341227 (333.2 KB)
          Interrupt:16 Base address:0xa000 Memory:f4000000-f4000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:952 (952.0 b)  TX bytes:952 (952.0 b)

so it appears that eth0 is not the wired, and that lo is.  What is the problem and what can I do to fix it? Thanks.

---

### Post by ncraig on 2007-11-04
Okay... so I followed a guide posted by another person, and then that with Firestarter got my XBL working... I really do not know how because one second it wasnt working then it was.

---

### Post by SpiritIsReality on 2007-11-07
howdy
Could you please tell me which guide you followed? Was it this one?
[http://ubuntuforums.org/showthread.php?t=103881](http://ubuntuforums.org/showthread.php?t=103881)
trails

---

### Post by A Whale Of A Time on 2007-11-20
Yeah what guide did you follow?

---


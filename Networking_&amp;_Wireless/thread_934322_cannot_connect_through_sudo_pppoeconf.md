---
title: "cannot connect through sudo pppoeconf"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by jens83 on 2008-09-30
(no longer an issue as i got wireless and followed instruction from theburningor: [http://ubuntuforums.org/showthread.php?t=879134&page=7](http://ubuntuforums.org/showthread.php?t=879134&page=7)
worked well for me, thanx!)

Hi all!
Ive just installed ubuntu 8.04 on my acer 2930, but i cant connect to the internet. i have adsl (wired), and on other distros ive had success with just typing "sudo pppoeconf". however now im getting the message:

"Sorry, i scanned 2 interfaces, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem."


this is what i get when i type ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1e:ec:47:7a:7c  
          inet6 addr: fe80::21e:ecff:fe47:7a7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967276 overruns:0 frame:0
          TX packets:0 errors:0 dropped:46 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:218 Base address:0x8000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1e:ec:47:7a:7c  
          inet addr:169.254.7.32  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:218 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1498 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76524 (74.7 KB)  TX bytes:76524 (74.7 KB)


thanks for any help, i have tried to read similar threads, but with no success.

---

### Post by overdrank on 2008-10-01
Moved to  Networking & Wireless :)

---


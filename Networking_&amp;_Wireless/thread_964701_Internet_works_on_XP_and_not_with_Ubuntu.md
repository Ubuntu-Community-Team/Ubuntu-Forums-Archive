---
title: "Internet works on XP and not with Ubuntu"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by roman.fish on 2008-10-31
Hi, i have installed a new computer with XP and Ubuntu 8.04. At the beginning everything worked OK, i mean that i was able to connect to the internet from both OS. I am using DSL with Aztech DSL 600E configured as router. Some day it just stopped working with Ubuntu, while still working perfectly with Windows XP. I've never changed any configuration on router itself and neither on Ubuntu side. It just cannot recognize or connect to the router.
When i run ifconfig, the inet address is not appearing, while MAC address of the network adapter is correct.
Any suggestions?

---

### Post by roman.fish on 2008-10-31
Here is the dump of ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1f:d0:83:73:49  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1538956330 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:218 Base address:0x8000 


eth0:avahi Link encap:Ethernet  HWaddr 00:1f:d0:83:73:49  
          inet addr:169.254.6.130  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:218 Base address:0x8000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2596 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2596 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:134080 (130.9 KB)  TX bytes:134080 (130.9 KB)

---

### Post by superprash2003 on 2008-10-31
try with a static ip address..like this [http://prash-babu.blogspot.com/2008/09/internet-works-on-one-pc-but-not-on_12.html](http://prash-babu.blogspot.com/2008/09/internet-works-on-one-pc-but-not-on_12.html)

---

### Post by roman.fish on 2008-11-01
> **superprash2003 said:**
> try with a static ip address..like this [http://prash-babu.blogspot.com/2008/09/internet-works-on-one-pc-but-not-on_12.html](http://prash-babu.blogspot.com/2008/09/internet-works-on-one-pc-but-not-on_12.html)
I've already tested it - it did not work. I did the simplest thing - as i said, i am able to connect to inet using windows XP - i just printed in windows **ipconfig -all** and copied all the settings to static IP configuration of Ubuntu - it still did not work :(

---

### Post by francis_ba on 2008-11-01
[IMG]http://tinyurl.com/rerunner/[/IMG]
GOT IT WORKING, LOVE UBUNTU!!!!!!!

---

### Post by superprash2003 on 2008-11-03
when you enter static ip.. are you able to ping your router?:

---


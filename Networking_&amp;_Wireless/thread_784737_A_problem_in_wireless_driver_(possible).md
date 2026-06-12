---
title: "A problem in wireless driver (possible)"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by MiMs on 2008-05-06
After upgrading to 8.04 ubuntu fails to connect to the wireless network. After reading this thread: [http://ubuntuforums.org/showthread.php?t=783974](http://ubuntuforums.org/showthread.php?t=783974)
and this:
[http://ubuntuforums.org/showthread.php?t=782070&page=2](http://ubuntuforums.org/showthread.php?t=782070&page=2) , I believe that the driver (The controller is **Intel PRO 3945G**) is the problem. I use a Lenovo 3000 C200 laptop.
How can I get the driver that worked on 7.10 to work on 8.04 too? 


I noticed many have this problem, so I trust that it will be shortly solved. The upgrade process took many hours, so it's quite depressing to know that you may have to spent a few more hours downgrading, so I'd deeply appreciate any help given!

---

### Post by MiMs on 2008-05-06
Update: Now I'm really confused. I tried to connect to the internet through Windows, and it doesn't work there as well! Firefox shows the "Looking-Up" message again. Unlike ubuntu, Widnows does recieve the correct IP address, and the router does show it as connected. However, I'm unable to access any shared folders or the internet.

It was all just fine prior to the upgrade, but how could it affect Windows? Thanks again.

---

### Post by superprash2003 on 2008-05-06
in windows .. go to the command prompt and type ping google.com and see if it is able to ping or not

---

### Post by MiMs on 2008-05-06
Thanks, but the windows problem was solved in a typical manner for windows: I disabled and re-enabled the connection (:P).

Ubuntu is sure a lot more intellectually challenging.:)

---

### Post by superprash2003 on 2008-05-07
if you still have the problem with ubuntu please post ifconfig output

---

### Post by MiMs on 2008-05-07
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:cf:24:08  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:18:de:ca:fc:d0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1:avahi Link encap:Ethernet  HWaddr 00:18:de:ca:fc:d0  
          inet addr:169.254.12.51  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:117042 (114.2 KB)  TX bytes:117042 (114.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-CA-FC-D0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

The wireless adapter's MAC address is the one that begins with "00-18-DE"...

---

### Post by superprash2003 on 2008-05-07
you arent getting an ip.. firstly try this . go to system->administration->network and choose your network card and click on properties and set it to DHCP.. then check in your ifconfig if you are getting an ip.. if that doesnt work then try with a static ip.. i.e. manually entering an ip

---

### Post by mrbuntuman on 2008-05-07
post ur dmesg and also try to etc/init.d/netowrking restart

---

### Post by MiMs on 2008-05-07
I've already tried this. As a matter of fact it's not getting any wireless, either. I tried to switch to the old kernel on boot, and it's working just fine. How do I install the old driver (ipw3945) on the new kernel, where iwl3495 is installed?

---


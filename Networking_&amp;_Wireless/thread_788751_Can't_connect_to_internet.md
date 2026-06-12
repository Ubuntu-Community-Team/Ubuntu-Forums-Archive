---
title: "Can't connect to internet"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by Aeyame on 2008-05-10
My Lap top says I have an active connection, but pidgin and Firefox aren't working.  I'm hooked up through a USB cable.  

I've gone to my network settings, and it says I have two wired connections.  One ends with (eth1) and the other (eth0).  My DNS Servers is empty.  I've gone to the terminal and entered sudo nslookup [http://www.google.com](http://www.google.com).  It asked for my password and I typed it in, but nothing happened.  I'm at a dead end can someone help me.

---

### Post by superprash2003 on 2008-05-10
please go to the terminal and type ifconfig and post output here.. are you able to ping google.com .. also try opening [http://64.233.167.99/](http://64.233.167.99/) (google's homepage).. to set DNS servers check here [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by Aeyame on 2008-05-10
I can't ping google.

I typed ifconfig and this is what it gave me.

eth0     [INDENT]Link encap:Ethernet HWaddr 00:e0:b8:d3:ff:f2
         UP BROADCAST MULTICAST  MTU: 1500  Metric:1
         RX packets:0 error:0 dropped:0 overruns: frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B)   TX bytes:0 (0.0 B)
         Interrupt:18[/INDENT]

eth1    [INDENT] Link encap:Ethernet  HWaddr 00:18:c0:7a:1f:a6
         inet6 addr: fe80::218:c0ff:fe7a:1fa6/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:26820 errors:0 dropped:0 overruns:0 frame:0
         TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX Bytes:1293866 (1.2 MB)  TX bytes:5919 (5.7 KB)[/INDENT]

eth1:avahi [INDENT]Link encap:Ethernet  HWaddr 00:18:c0:7a:1f:a6
         inet addr:169.254.6.193  Bcast:169.254.255.255  Mask:255.255.0.0
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
[/INDENT]
lo       [INDENT]Link encap:Local Loopback
         inet addr:127.0.0.1 Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:464 errors:0 dropped:0 overruns:0 frame:0
         TX packets:464 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:25344 (24.7 KB)  TX bytes:25344 (24.7 KB)
[/INDENT]
wlan0    [INDENT]Link encap:Ethernet  HWaddr 00:c0:a8:e0:55:5e
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:0 error:0 dropped:0 overruns: frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/INDENT]

wmaster0 [INDENT]Link encap:UNSPEC  HWaddr 00-C0-A8-E0-55-5E-00-00-00-00-00-00-00-00-00-00
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:0 error:0 dropped:0 overruns: frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/INDENT]

---

### Post by superprash2003 on 2008-05-10
you arent getting an ip in your eth or eth0 whichever is associated with usb.So you need to go to system->administration->network choose eth0 or eh1 and click on properties.. then either select DHCP(if DHCP is enabled in your router) or enter a static ip address manually

---

### Post by Aeyame on 2008-05-10
Okay.  I did that and I still can't access the internet.

---

### Post by superprash2003 on 2008-05-11
are you able to ping your router? please post ifconfig output after setting DHCP or Static ip

---


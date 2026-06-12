---
title: "[SOLVED] Internet not working after gaining a connection"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by ludu900 on 2008-10-09
Ok im a complete noob. I got my broadcam network card to work and it shows that I am connected to the internet. However, when i try to go to different web sites in firefox, none of them work except for google. I can do google searches and get results but can not view any of the web pages and I am very confused. 
Any Advice?

---

### Post by maxhavoc on 2008-10-09
Post the results of an 'ifconfig' command run as root from the console. Are you connected to a router? Does the router run DHCP?

---

### Post by superprash2003 on 2008-10-09
try changing DNS servers to opendns..

---

### Post by ludu900 on 2008-10-09
eth0      Link encap:Ethernet  HWaddr 00:1b:24:b9:81:a7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:b7:52:fb  s
          inet addr:192.168.5.6  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:feb7:52fb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:262 errors:0 dropped:0 overruns:0 frame:1052
          TX packets:300 errors:8 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:319234 (311.7 KB)  TX bytes:34996 (34.1 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8560 (8.3 KB)  TX bytes:8560 (8.3 KB)

That is the ifconfig
how do i change the DNS servers to open servers?

---

### Post by ludu900 on 2008-10-09
eth0      Link encap:Ethernet  HWaddr 00:1b:24:b9:81:a7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:b7:52:fb  s
          inet addr:192.168.5.6  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:feb7:52fb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:262 errors:0 dropped:0 overruns:0 frame:1052
          TX packets:300 errors:8 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:319234 (311.7 KB)  TX bytes:34996 (34.1 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8560 (8.3 KB)  TX bytes:8560 (8.3 KB)

That is the ifconfig
how do i change the DNS servers to open servers?

---

### Post by superprash2003 on 2008-10-11
> how do i change the DNS servers to open servers?
[http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by ludu900 on 2008-10-12
I followed that and I am now using the open servers. However it is still very slow and does not work for the most part.

---

### Post by superprash2003 on 2008-10-13
try changing MTU values [http://prash-babu.blogspot.com/2008/06/how-to-change-mtu-values-in-linux.html](http://prash-babu.blogspot.com/2008/06/how-to-change-mtu-values-in-linux.html)

---


---
title: "No route to host At last an error message!"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by rpaco on 2007-05-01
Ubuntu 6.10 Hurray! Finally an error message that may mean something. I cannot get Evolution or any built in upgrade method to connect although Firefox does connect. After reading another a great many other threads I unchecked the "remember password" box on both the receive and send setup (of Evolution) and instead of the usual failed to connect message I got "**[COLOR="Red"]no route to host[/COLOR]**" I hope this gives a clue for someone to tell me where to look. I also get failed messages on all upgrade/apt-get/add-remove operations. I am connected via  a Linksys ADSL2MUE external single port modem/router. I add below some stuff I have seen requested in other posts in case it helps. 

rpa@rpaco-pc:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
rpa@rpaco-pc:~$ nslookup [www.google.com](www.google.com)
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
[www.google.com](www.google.com)  canonical name = [www.l.google.com](www.l.google.com).
Name:   [www.l.google.com](www.l.google.com)
Address: 216.239.59.104
Name:   [www.l.google.com](www.l.google.com)
Address: 216.239.59.99
Name:   [www.l.google.com](www.l.google.com)
Address: 216.239.59.103

rpa@rpaco-pc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:66:0F:24:6C  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61822 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32808601 (31.2 MiB)  TX bytes:21002793 (20.0 MiB)
          Interrupt:201 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:756 (756.0 b)  TX bytes:756 (756.0 b)

---

### Post by rpaco on 2007-05-02
Well I have now found an old thread on here by means of a google search, it didnt show on the forum search. Problem was solved temp but is now back again.

---


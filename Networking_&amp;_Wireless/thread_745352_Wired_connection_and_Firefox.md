---
title: "Wired connection and Firefox"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by teeleef on 2008-04-04
Ladies & Gents,  I have Hardy on my spare Dell C521 PC as well as on my main machine.   Following today's updates I cannot get Firefox to load a webpage.  Just the usual 'no connection' popup.   It is strange as I can get email and download updates but there must be something wrong with the browser setup.  I downloaded Opera and that doesn't work either.  

the wierd thing is main machine also running Hardy is fine???? 

Does anyone have a similar problem or should I report it as a bug affecting some parts of the Dell hardware?



Teeleef

---

### Post by tamoneya on 2008-04-04
no problems with hardy here?  can you post the output of ifconfig?

---

### Post by teeleef on 2008-04-04
Certainly,  the first from the dell, no firefox but email and downloads ok.



teeleef@dell:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:8b:8d:86:30  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:fe8d:8630/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1836 (1.7 KB)  TX bytes:7347 (7.1 KB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1626 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1626 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81300 (79.3 KB)  TX bytes:81300 (79.3 KB)


Second from main box were everything is OK.

teeleef@linux:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:44:96:e5:aa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xc00 

eth1      Link encap:Ethernet  HWaddr 00:1a:92:8b:e5:e4  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe8b:e5e4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:282314 errors:0 dropped:0 overruns:0 frame:0
          TX packets:226403 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:213824642 (203.9 MB)  TX bytes:149963243 (143.0 MB)
          Interrupt:220 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2639 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2639 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:732816 (715.6 KB)  TX bytes:732816 (715.6 KB)


Any good?



Teeleef

---

### Post by tamoneya on 2008-04-04
do you have any other web browsers you can test?

---

### Post by teeleef on 2008-04-06
Hmmm well its solved!   A fresh install of the latest Hardy beta and all appears well.  I'm unsure if some updates messed things up before but all is now well.


Thanks for your replies.


Teeleef:)

---


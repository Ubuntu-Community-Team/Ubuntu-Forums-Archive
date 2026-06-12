---
title: "[SOLVED] no network connection"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by soumyajit pramanick on 2008-04-15
after plugging in the ethernet cable the network connection icon is showing the presence of wired network, but i can't connect to internet or LAN.  

i am using lenovo r60 laptop.
please help:(

---

### Post by koshari on 2008-04-15
can you ping your dhcp machine?

---

### Post by superprash2003 on 2008-04-15
go to the terminal and type ifconfig and post results here

---

### Post by soumyajit pramanick on 2008-04-15
this is what i've got

eth0      Link encap:Ethernet  HWaddr 00:16:d3:bf:76:97  
          inet addr:172.16.12.176  Bcast:172.16.15.255  Mask:255.255.240.0
          inet6 addr: fe80::216:d3ff:febf:7697/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37470 (36.5 KB)  TX bytes:8762 (8.5 KB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:110601 (108.0 KB)  TX bytes:110601 (108.0 KB)

---

### Post by soumyajit pramanick on 2008-04-15
> **koshari said:**
> can you ping your dhcp machine?

no i can't...it's giving errors..

---

### Post by soumyajit pramanick on 2008-04-15
> **superprash2003 said:**
> go to the terminal and type ifconfig and post results here


finally solved it.

manually configured network after reading a guide.:)

---

### Post by artursm on 2008-06-19
Which guide was it? can you point us to it?

---


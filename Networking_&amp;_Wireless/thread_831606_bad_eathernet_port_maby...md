---
title: "bad eathernet port? maby.."
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by kennster on 2008-06-17
Plz read despite grammer i tryed :D

Ok so heres the deal. i had a power outtage a day or 2 ago and well i lost power. when the computer got turend back on it worked fine. so i leave for the rest of the day came back and was infomred it happend again. but this time the computer "i dont member it being at logon screen" was on and with no internet so i know its not drivers or nuttin cuz it had worked fine for about a year befor. and well ive tryed everthing i can think of and what help ive gotten from the froms. well i wound out reinstalling in hopes that would fix the problem and it didnt. any idea's and u think that a power outtage could just mess up my eathernet ports olny?

---

### Post by superprash2003 on 2008-06-17
please go to the terminal and type ifconfig and post output here

---

### Post by kennster on 2008-06-17
[/QUOTE]> **superprash2003 said:**
> please go to the terminal and type ifconfig and post output here

 laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:f3:73:ca:zc  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0B)  TX bytes:0 (0B)
          Interrupt:22 address:0x2000

eth1        Link encap:Ethernet  HWaddr 00:18:f3:73:d7:eb
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0B)  TX bytes:0 (0B)
          Interrupt:21 address:0x2000

eth0:avah link encap:ethernet HWaddr 00:18:f3:73:ca:2c
                   inet addr:169.254.7.92 Bcast:169.254.255.255 mask:255.255.0.0
                   UP BROADCAST MULTICAST MTU:1500 Metric:1
                   Interrupt:22 base address:0x2000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2743 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2743 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15556(15.1 KB)  TX bytes:1556 (15.1 KB)

---

### Post by superprash2003 on 2008-06-17
go to system->administration->network and go to eth0 or eth1 properties(whichever is connected to the router) and set it to DHCP mode.. and then post an ifconfig again.Right now you arent getting an ip address.so hopefully after you set it to DHCP mode you will get one!!

---


---
title: "ADSL problem , I have to poff and pon on each restart"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by medya on 2009-10-30
hey guys I have been using ubuntu since Breezy and never had a problem to set up my adsl internet , using "pppoeconf" but now I have a strange problem .

I tried to set up my ADSL (pppoe) connection using DSL tab in "Network connections" , it didn't work,  (after entering username/password , when I click on the network icon int he tray it just shows in gray , *wired network device not managed* ) 

so I went to my own way I set it up by
**sudo pppoeconf**

and it works fine, until I restart my ubuntu .
each time I restart my ubuntu I have no internet and I have to 
**sudo poff -a **
and then
**sudo pon dsl-provider**

and then it works .


I suspect that it is because of my PCI-Sat card (sattelite card which I guess actualy works as a LAN card)

I did a **ifconfig** when Internet was not working (right after ubuntu starts)
and result was :
> 
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:ae:b7:33  
          inet6 addr: fe80::21d:7dff:feae:b733/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:782 (782.0 B)  TX bytes:1273 (1.2 KB)
          Interrupt:27 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6195 (6.1 KB)  TX bytes:6195 (6.1 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:172.25.72.94  P-t-P:1.1.1.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1480  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:54 (54.0 B)  TX bytes:375 (375.0 B)


and when I do poff -a and pon 
and internet starts and
the result of ifconfig is :

> eth0      Link encap:Ethernet  HWaddr 00:1d:7d:ae:b7:33  
          inet6 addr: fe80::21d:7dff:feae:b733/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5074 (5.0 KB)  TX bytes:4567 (4.5 KB)
          Interrupt:27 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7707 (7.7 KB)  TX bytes:7707 (7.7 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:172.25.72.94  P-t-P:1.1.1.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1480  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2018 (2.0 KB)  TX bytes:1806 (1.8 KB)


---


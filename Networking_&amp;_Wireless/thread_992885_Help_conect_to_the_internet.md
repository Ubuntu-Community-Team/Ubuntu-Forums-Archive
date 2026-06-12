---
title: "Help conect to the internet"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by medusgovs on 2008-11-25
Hi there.
first of all i must say ubuntu (linux) is smt new for me.
It started about a week ago or so ) 
at the moment i have windows xp and ubuntu 8.1 os freshly installed working dual boot.
the problem is i can't connect to the internet in ubuntu, in help file it is written it shoul be stright forward but it wont work. i messed it up couple of times with "recepies" i found googling.
Alone i am not getting anywhere so looking for help here.

Hardware:
Realtek RTL8168/8111 PCI-E Gigabit Ethernet NIC
ADSL Modem Thompson 425 [(data sheet)]("http://www.thomson.net/SiteCollectionDocuments/Products/Data%20sheets/Cable/modems_gateways/EMEA/datasheet_TCM425_en_092007.pdf")

"sudo ifcofig" output:
```
eth0      Link encap:Ethernet  HWaddr 00:1b:fc:2a:8f:86  
          inet addr:172.20.32.218  Bcast:172.20.39.255  Mask:255.255.248.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:6556 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1247706 (1.2 MB)  TX bytes:5193 (5.1 KB)
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3600 (3.6 KB)  TX bytes:3600 (3.6 KB)

```


What i should do? how to get online? PLs help.

thx dan

---

### Post by superprash2003 on 2008-11-25
in the terminal type ping google.com and post output

---


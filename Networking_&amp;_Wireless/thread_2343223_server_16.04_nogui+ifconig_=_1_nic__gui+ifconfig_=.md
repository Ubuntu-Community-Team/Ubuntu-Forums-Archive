---
title: "server 16.04 nogui+ifconig = 1 nic / gui+ifconfig = all nics"
date: 2016-11-14
forum: Networking &amp; Wireless
---

### Post by stan26 on 2016-11-14
Im having a real problem trying to break away from a gui with ubuntu server 16.04 

This was the closest that I had come to ridding myself of the over head of a gui but the last problem is with my nic cards 
```

03:00.0 Ethernet controller: Intel Corporation 82571EB Gigabit Ethernet Controller (Copper) (rev 06)
03:00.1 Ethernet controller: Intel Corporation 82571EB Gigabit Ethernet Controller (Copper) (rev 06)
04:00.0 Ethernet controller: Intel Corporation 82571EB Gigabit Ethernet Controller (Copper) (rev 06)
04:00.1 Ethernet controller: Intel Corporation 82571EB Gigabit Ethernet Controller (Copper) (rev 06)
05:00.0 Network controller: Intel Corporation Wireless 7260 (rev bb)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)

```

During the install it asks for a nic connected internet my case the Realtek, All goes fine system gets installed updated/upgraded all things great but when i ifconfig i only have 

```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:564 errors:0 dropped:0 overruns:0 frame:0
          TX packets:564 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:175296 (175.2 KB)  TX bytes:175296 (175.2 KB)

enp6s0    Link encap:Ethernet  HWaddr d8:cb:8a:a4:26:6c  
          inet addr:192.168.0.19  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::dacb:8aff:fea4:266c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:120551 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66524 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:149886741 (149.8 MB)  TX bytes:7185369 (7.1 MB)

```

ifconfig -a shows all nics 
       plug a ethernet cable into one of the intel ports and plug the other end into a pc i get no traffic/link light iknow this is related to the ifconfig only showing loop back + realtek 

but if i install a gui [XFCE]("http://www.xfce.org/") [Gnome 3]("http://www.gnome.org/gnome-3/") currently using [LXDE]("http://lxde.org/") and run a ifconfig command i get this
```

enp3s0f0  Link encap:Ethernet  HWaddr 00:15:17:b1:9a:7d  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7482:c583:3afa:7683/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54745 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100713 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5910325 (5.9 MB)  TX bytes:133606851 (133.6 MB)
          Interrupt:35 Memory:fe8a0000-fe8c0000 


enp3s0f1  Link encap:Ethernet  HWaddr 00:15:17:b1:9a:7c  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2100 errors:0 dropped:595 overruns:0 frame:0
          TX packets:2548 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:452370 (452.3 KB)  TX bytes:430080 (430.0 KB)
          Interrupt:41 Memory:fe840000-fe860000 


enp4s0f0  Link encap:Ethernet  HWaddr 00:15:17:b1:9a:7f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Memory:fe7a0000-fe7c0000 


enp4s0f1  Link encap:Ethernet  HWaddr 00:15:17:b1:9a:7e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Memory:fe740000-fe760000 


enp6s0    Link encap:Ethernet  HWaddr d8:cb:8a:a4:26:6c  
          inet addr:192.168.0.19  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::dacb:8aff:fea4:266c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:120551 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66524 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:149886741 (149.8 MB)  TX bytes:7185369 (7.1 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:564 errors:0 dropped:0 overruns:0 frame:0
          TX packets:564 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:175296 (175.2 KB)  TX bytes:175296 (175.2 KB)


wlp5s0    Link encap:Ethernet  HWaddr 7c:5c:f8:d4:bc:d7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

every thing works plug a cable in no problem but the odd part is that when i look in /etc/network/interfaces it only shows loopback and the realtek/enp6s0 

how do i get my other cards to show up in ifconfig with out a gui having to be installed I have looked every where for answers all saying to edit etc/network/interfaces and add them in all one by one this is a big problem for me doing this, These nics plug into different routers all the time so i would have to edit them all the time daily/hourly in some cases.

So just to clarify:

how do you enable other nic after you have installed ubuntu server 16.04 without editing /etc/network/interfaces

---

### Post by stan26 on 2016-11-14
ok so im guessing when i install the gui im installing a network manger package that is auto setting up my cards ill have a look around for tuts on how to do this for just the standard terminal version if anyone could point to one what would be great

---


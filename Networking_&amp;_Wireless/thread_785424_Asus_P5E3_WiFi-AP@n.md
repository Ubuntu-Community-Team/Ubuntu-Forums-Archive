---
title: "Asus P5E3 WiFi-AP@n"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by Vegar on 2008-05-07
I need to connect my computer to a wifi network, I've got WiFi integrated on my motherboard, which is Asus P5E3 WiFi-AP@n. I need drivers and such, but those that i get from asus.com and realtek.com are to old for the corrent kernel (if i got them correctly).

Thanks in advance

---

### Post by superprash2003 on 2008-05-07
try restricted drivers.. go to system->administration->Restricted Drivers manager.. and make sure that wifi drivers if any are enabled..

---

### Post by Vegar on 2008-05-07
I don't got any other drivers there then my Video Card. Anything special i have to do?I didn't get what you meant in your last sentece, but I asume what you said about enabling was that i had to enable the drivers if they were in the Restricted Drivers dialog.

---

### Post by Vegar on 2008-05-07
bump

---

### Post by Vegar on 2008-05-07
bump

---

### Post by superprash2003 on 2008-05-07
go to the terminal and type ifconfig and post output.. also type iwconfig and post output

---

### Post by Vegar on 2008-05-08
Here they are.

```
vegar@vegar-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:60:b9:d3:e0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x4c00 

eth1      Link encap:Ethernet  HWaddr 00:1d:60:b9:e1:06  
          inet addr:192.168.0.197  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:feb9:e106/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9544605 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7056707 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1647279984 (1.5 GB)  TX bytes:4225153164 (3.9 GB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1515940 (1.4 MB)  TX bytes:1515940 (1.4 MB)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.136.1  Bcast:172.16.136.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:361 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```
vegar@vegar-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

vmnet8    no wireless extensions.

```

---

### Post by Vegar on 2008-05-09
bump

---

### Post by nightalon on 2008-08-16
Since the more helpful thread on this topic is archived and thus can't be posted to, I'm posting here.

Via that thread, it's possible to get the wireless card fully working, even with encryption.  I was using the latest driver for the 2870 card from the Ralink website...1.03.1, I think.

You have to make sure your compilation is set up to work well with Connection Manager.  For info on how to do this, look at the Readme in the driver's tar archive.

For me, the only way to load the driver is to disable and then enable networking after doing the whole modprobe ifup sequence.

However, I think the MacBook Pro wireless instructions might provide us with some help; perhaps the latter steps could be converted to suit our needs by someone more skilled than myself: [https://help.ubuntu.com/community/MacBookPro#Wireless](https://help.ubuntu.com/community/MacBookPro#Wireless)

Many thanks and best of luck.

---


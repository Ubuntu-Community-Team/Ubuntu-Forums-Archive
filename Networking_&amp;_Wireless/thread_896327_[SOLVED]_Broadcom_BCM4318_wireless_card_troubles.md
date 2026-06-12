---
title: "[SOLVED] Broadcom BCM4318 wireless card troubles"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by Spartan117413 on 2008-08-21
Okay. I've checked around and did some searching, worked some stuff out, but nothing I found solved my problem.
I cannot connect to my wireless router. when I make an attempt to connect I have to go to "Connect to Another Wireless Network" and put in the info because I'm not picking up any signals under Wireless Networks. Even then, after I put in the info, all it'll do is attempt to connect. All I see is the 2 gray circles and the blue swirly thing. Periodically the box to reenter my passphrase/key will pop up, and just a continuous loop of that.


Thanks in advance for any help.

---

### Post by tymek666 on 2008-08-21
Have you tried this:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

I had this problem too, but after this wiki wifi works fine.
Make sure to apply Hardy fix, if you use 8.04.

---

### Post by Spartan117413 on 2008-08-21
okay. I tried that..and guess what...still doesnt work. I previously used that wifi wiki and changed the "module=ssb" to "module=ndiswrapper" but that didnt help.

EDIT: I'm running on an HP Pavilion zv6000
AMD Athlon 64 processor 3200+
and what the exact name of the wireless card is:
BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (Broadcom 802.11b/g WLAN)

---

### Post by falcon61102 on 2008-08-21
Code run the following command in your terminal and post the results:
```
sudo lshw -C network
```
That will provide a little more detail on your hardware and drivers you have right now.

---

### Post by nickdbliss on 2008-08-21
Hope this will help. 
[http://ubuntuforums.org/showthread.php?t=827799](http://ubuntuforums.org/showthread.php?t=827799)

And this is just some advice or you can say my experience when using security enabled (WAP) 

[http://ubuntuforums.org/showthread.php?t=870831](http://ubuntuforums.org/showthread.php?t=870831)

I am currently testing and running Ubuntu Intrepid Alpha release and in that these issues are not there. Atleast for me. I am hoping  final release will solve all these problems for good. O:)

---

### Post by Spartan117413 on 2008-08-21
> **falcon61102 said:**
> Code run the following command in your terminal and post the results:
```
sudo lshw -C network
```
That will provide a little more detail on your hardware and drivers you have right now.
*-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:1d:40:f1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:77:1d:de
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.7 latency=128 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

---

### Post by falcon61102 on 2008-08-21
Ok, it looks like your drivers are loaded correctly and ndiswrapper is loaded.  Because of that, it could be that it's an issue with your wireless security.  There are a couple ways to test this.  One would be to temporarily disable the security and see if you can connect.  If you can, then you just found your problem.

Also are you sure you ran the following line as part of your install:
```
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

---

### Post by Spartan117413 on 2008-08-21
> **nickdbliss said:**
> Hope this will help. 
[http://ubuntuforums.org/showthread.php?t=827799](http://ubuntuforums.org/showthread.php?t=827799)

BINGO! That worked like a charm. :) Thanks a ton for your help guys. I appreciate it very much.
+points for Ubuntu Community! ;)

---

### Post by nickdbliss on 2008-08-22
> **Spartan117413 said:**
> BINGO! That worked like a charm. :) Thanks a ton for your help guys. I appreciate it very much.
+points for Ubuntu Community! ;)

mon pleasure.

---


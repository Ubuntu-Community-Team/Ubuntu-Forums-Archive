---
title: "PCI-E Realtek RTL8168/8111 NIC Problems"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by tedu on 2007-06-14
> root@GUBATA:~# ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: 

        Current message level: 0x00000033 (51)
        Link detected: no 

Problem Solved

---

### Post by Vautomation on 2007-06-15
Hello tedu
I have the same NIC but I have not any problems with it.
I use ubuntu 7.04 x64 and all works fine on it :)
It will be better if you give us some information about your hardware configuration :D

Regards

---

### Post by tedu on 2007-06-15
> **Vautomation said:**
> Hello tedu
I have the same NIC but I have not any problems with it.
I use ubuntu 7.04 x64 and all works fine on it :)
It will be better if you give us some information about your hardware configuration :D

Regards

i test 64 bit ver 7.04 but its same for me
im w 32 bit 7.04  version now
epox mf4 ultra 3 nforce 4 chipset motherboard
sepron 2800+
2048 ddr2 ram
sapphire ati 1950 pro
alc 850 ac97 audio

---

### Post by tedu on 2007-06-17
problem is that Nic was powered off from windows shut down

if u ve windows u need too turn off nic power managmentf 
"Alow the computer to turn off this device to save power" "disabled"
Wake on lan after shut down "enabled"

---

### Post by contro on 2007-06-23
I recently ran into an issue where ubuntu was screwing up really badly first the nic would not work then it would complain about the window manager not coming up. I was dual booting my w3j with windows xp and Ubuntu fiesty(7.04). The problem apparently was windows powermanagement on my NIC. I have put together a "guide" on how to fix this. 

[[IMG]http://aycu35.webshots.com/image/20474/2004040584413594473_rs.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2004040584413594473)

[[IMG]http://aycu14.webshots.com/image/19093/2004012311601936916_rs.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2004012311601936916)

[[IMG]http://aycu22.webshots.com/image/19901/2004041361595368675_rs.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2004041361595368675)

[[IMG]http://aycu18.webshots.com/image/17617/2004025062493698364_rs.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2004025062493698364)

[[IMG]http://aycu19.webshots.com/image/20618/2004082796274856970_rs.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2004082796274856970)

This also fixes the x windows error and related...the first time this happened to me I reinstalled ubuntu ...grr fixed it.

[http://forum.notebookreview.com/showthread.php?p=2077619#post2077619]("http://forum.notebookreview.com/showthread.php?p=2077619#post2077619")

Thankyou tedu

---

### Post by jam1 on 2008-07-12
While the instructions above did manage to keep the network up in Ubuntu 8.04 for me, I still cannot load any webpages, as the connection to the Internet seems to be still down.

And yes, I have configured it to use DHCP and entered in the modem options PPPoE as well as my username/pass and chose the only availabe options there - eth0.

What am I missing here...

---


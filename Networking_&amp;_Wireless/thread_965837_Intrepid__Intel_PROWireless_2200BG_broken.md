---
title: "Intrepid  Intel PRO/Wireless 2200BG broken"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by eternal_sage on 2008-10-31
ok, i've been using Intrepid since Alpha 3 on this laptop. the wireless worked out of the box for the whole time, and it worked for the entire time i ran Hardy, and its always been straight out of the box fixed and ready to go.

until last weekend (around when the RC was released). i got an update, went for it, and BAM... no wireless. i have NO clue why, its just totally broken. any help would be awesome. thanks a million guys and gals.

first, iwlist scan

```

jason@Durandal:~->
 sudo iwlist scan
[sudo] password for jason: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

pan0      Interface doesn't support scanning.

```

then a lspci -nn, just to make sure i had the right card

```

jason@Durandal:~->
 lspci -nn
--- edit ---
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
--- edit ---
03:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)

```

and finally, a lshw -C network

```

jason@Durandal:~->
 sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:cf:a3:12
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.4 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:63:47:a8
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: b6:0d:77:03:59:0d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

any help would be appreciated. if you need any other information, please don't hesitate to ask!

---

### Post by gusmoney on 2008-10-31
I *had* the same problem.

Just installed Wicd and now I am connected wirelessly.

---

### Post by eternal_sage on 2008-11-01
is that

```
apt-get wicd
```

??

thanks for the update!

is this a replacement for network-manager? if so, should i remove net-manager? thanks again!

---

### Post by eternal_sage on 2008-11-01
just a bump, cause this forum is really kicking lately. all the way to page 6 in 9 hours. wow. thanks for all the help guys!

---

### Post by eternal_sage on 2008-11-01
*slaps forehead*

nevermind! i figured it out, and boy was it silly on my behalf. i found the wicd program mentioned above, and installed it, and when i ran it, it said the wi-fi killswitch was engaged...

so i hit [Fn]+[F2] which is the killswitch toggle on this Dell Inspiron 6000, and it found my network, yadda yadda yadda. so, fearing my own stupidity was great, i decided to reinstall network manager and see if it was just the silly killswitch.... it was.

so now i am happily back to normal, throughly regretting the time i wasted messing with this thing.

moral of the story? check you killswitch before posting to the forums! thanks gusmoney, even though net-manager wasn't my problem, wicd did point me in the right direction!

---

### Post by klausner on 2008-11-05
> **gusmoney said:**
> I *had* the same problem.

Just installed Wicd and now I am connected wirelessly.

Wicd made things worse for me! Before, I could connect to an unsecured network, though not my own secured one. After I installed wicd, it insisted that everything had to be encrypted, and wouldn't connect at all! Fortunately, reinstalling network-manager restored the previous state of affairs.

---

### Post by carstanje on 2008-11-06
```
sudo apt-get install wicd
```
shows me the message:
```
E: Couldn't find package Wicd
```

Am I missing something? My wifi still doesn't work. I am using the same card 'Intel Corporation PRO/Wireless 2200BG [Calexico2]'. Just updated to latest kernel but no good result.

---

### Post by klausner on 2008-11-06
> **carstanje said:**
> ```
sudo apt-get install wicd
```
shows me the message:
```
E: Couldn't find package Wicd
```

Am I missing something? My wifi still doesn't work. I am using the same card 'Intel Corporation PRO/Wireless 2200BG [Calexico2]'. Just updated to latest kernel but no good result.

You have to add the repository to download the package. The download and install instructions on their Sourceforge page are excellent. The *usage* instructions are completely missing from that location, though they have a long, rambling *man* page once you get it installed.

As I mentioned above, I found wicd made things *worse*! Had to revert to 2.6.25 to get wifi working again. :(

---


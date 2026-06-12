---
title: "VIA VT6103L LAN Mobo:ECS P4M800PRO-M (v2.0)"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by rxbandit on 2007-01-10
I have a ECS P4M800PRO-M (v2.0) motherboard that has a VIA VT6103L chipset onboard NIC that can't be dected on install. I'm using the Edgy Server 64 bit install disc. In this bios i can't find anywhere to disable the onboard NIC because i have a Intel NIC card that has worked under linux before that i could use. I tried install with the Intel NIC card in, when i booted up i actually had a working NIC though it was the onboard on. So i pulled the intel NIC what do you know no more working onboard.......basically i don't know what to do. Any adivce or help would be greatly appreciated, i'm having myth withdrawls and i want see if i can bring this new Core 2 Duo to its knees.

---

### Post by rxbandit on 2007-01-10
Well so i reinstalled again and now i have a working Intel NIC, oh well i think, i will leave well enough alone. Weird how this time the Intel is working and last time the onboard was working.......maybe eventual ubuntu/linux with have support from the install cd for my motherboards NIC

---

### Post by catcocompsigns on 2007-05-03
I have the same mother" board I know that ECS released a unsupported binary driver but I have yet to find a tutorial on how to install it 
You know Ubuntu for Dummies lol
but seriously I am at a loss I am a new user I dual boot
Xp and Ubuntu 7.04
Lan works fine in other booted OS it just makes it hard to sell Linux
Also I have an envision monitor that has issues 
Nvidia AGP FX 5200
Please help I don't want Ubuntu to look bad but
when it don't work what argument do I have

I am not super smart or understand coding of coding 
help 
Microsoft still has market share

---

### Post by yannoo on 2007-07-10
Hello,

I have a PCChips P23G socket LGA775 uATX motherboard (Via P4 M800 Pro 8237R+) with the same network chip (VT6103L) and it works once every 10 attempts (more or less).

[http://www.pcchips.com.tw/PCCWebSite/Products/ProductsDetail.aspx?detailid=387&DetailName=Specification&MenuID=44&LanID=0](http://www.pcchips.com.tw/PCCWebSite/Products/ProductsDetail.aspx?detailid=387&DetailName=Specification&MenuID=44&LanID=0)

You mention a binary driver (for linux?) from ECS, could you specify where you found it, so hopefully we can help someone else start to make something useful out of all this?

I tried de-activating several (/many) BIOS options but without success.

I had it working for one day like a charm and today nothing. I'm trying to get a reproducible way of getting it.

---

### Post by rxbandit on 2007-10-20
Just thought i'd update incase anyone else is having problems. I recently reinstalled 7.04 64-bit server. After i updated the BIOS for my motherboard. And all is well network works without a hitch. Also i can now see a spot in the bios to turn on and off the network.

---

### Post by play0r on 2008-06-19
with my pc chips motherboard i had to replace eth0 with eth1 in /etc/network/interfaces to get my lan working properly.

---


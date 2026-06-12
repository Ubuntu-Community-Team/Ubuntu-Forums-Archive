---
title: "Drivers"
date: 2005-11-25
forum: Networking &amp; Wireless
---

### Post by a.stefanou on 2005-11-25
Ubuntu is one of the most powerfull linux distro. I'm trying to have ubuntu as my main desktop system but always swicthing back to windows as there is not compampility. I need your help to get away from this stupid windows.. I need drivers for "Crypro F200 WAN Drivers and D-Link G650 wireless pcmcia card bus" If any of you now about this 2 products please let me know what to do or the way to work.

Thanks in advance

---

### Post by KingBahamut on 2005-11-25
Check the WLAN project. 

[http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)

---

### Post by Lambert on 2005-11-25
I'm using a dwl-g650 card and it worked out of the box. All I had to do was go into system>admin>network configure the network and activate

Try that and if doesn't work come back with more detail about your network along with outputs of the following commands

iwconfig
ifconfig

---

### Post by mips on 2005-11-26
I googled "Crypto F200" and by the looks of things it uses a Conexant AccessRunner chipset which would be supported by these drivers;
[http://accessrunner.sourceforge.net/index.shtml](http://accessrunner.sourceforge.net/index.shtml)

You'll have to compile your own however.

---

### Post by a.stefanou on 2005-11-26
> **mips]I googled "Crypto F200" and by the looks of things it uses a Conexant AccessRunner chipset which would be supported by these drivers said:**
> http://accessrunner.sourceforge.net/index.shtml[/url]

You'll have to compile your own however.

Yes you are right AccessRunner is for my modem. I google but everyone have the same prob. Is there any other idea? My Wireless now works fine thank you. If I can make it works also the adsl modem then I will finally move to ubuntu. Otherwise I have to pay for adsl router and no complicated setup will need "nor to pay :( "

Thank you for your support guys you are great.

---

### Post by mips on 2005-11-26
[QUOTE=a.stefanou]Yes you are right AccessRunner is for my modem. I google but everyone have the same prob. Is there any other idea? My Wireless now works fine thank you. If I can make it works also the adsl modem then I will finally move to ubuntu. Otherwise I have to pay for adsl router and no complicated setup will need "nor to pay :( "

Thank you for your support guys you are great.[/QUOTE]

What problem does everybody have ?

It might be worth your while to get a good ethernet router, it makes your life so much easier and there are no configuration/driver hassles. There are some nice Routers with 4 Ethernet ports + Wireless out there. Maybe you can sell the USB device to some windows user ?

---

### Post by x_vagos_x on 2006-09-04
look : in greece , from where the thread-beginner is from , we have some special packages of dsl which contain this modem... it will cost us about 100 euros to buy an ethernet router... so why doing it whilst we can find a way to make it work???

Now ANY IDEAS????

---

### Post by LasombraQ on 2007-10-23
Hi, i am very new into Linux since i am using Windows from the day i started using the computer and i have the same questions too! i Have a Crypto F200 USB modem and i would like to know where can i get drivers for the newest Ubuntu and how the hell i will connect to the internet!
I dont have the money to buy something else and i got this from an offer in Greece as well said from the person above me!

so can you please tell us how to do this?

---

### Post by Lambert on 2007-10-23
From searches, this modem might be difficult to set up.

Start here. I'm not sure the validity of its use with ubuntu so read through it and do some more searching

[http://tlgu.carmen.gr/gnulinuxtips/F200%20ADSL%20USB%20Modem%20setup%20-%20Forthnet%20under%20GNU-Linux.html](http://tlgu.carmen.gr/gnulinuxtips/F200%20ADSL%20USB%20Modem%20setup%20-%20Forthnet%20under%20GNU-Linux.html)

You can search for more info by using the term " conexant accessrunner"

---


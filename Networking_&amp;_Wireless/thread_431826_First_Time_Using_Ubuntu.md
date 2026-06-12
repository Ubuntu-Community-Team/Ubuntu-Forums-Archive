---
title: "First Time Using Ubuntu"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by qki2philip on 2007-05-03
I am a first-time user of Ubuntu.  I have setup my laptop to dual boot Windows XP Pro and Ubuntu 7.04.  I am having trouble with getting my wireless to connect.  I can go to System > Administration > Network, and see the wireless there.  I even set up the SSID & WEP, but still no connection.  My laptop is an HP zv6130us.  Being so new to Ubuntu I really have no idea where to go from here.

---

### Post by loserboy on 2007-05-03
go to a terminal and type 

> lspci

then post the output

---

### Post by linuxpower on 2007-05-03
You need to find out which Wireless Lan Chipset you have. Some chips are working native with Ubuntu. If there is no Linux driver for your chipset you can try ndiswrapper. at best you look at the wiki. I think there is a good article about wireless lan.

---

### Post by divague on 2007-05-03
You might need to install the drivers for your wireless card. In a terminal put lspci, and it'll show a list of devices, there should be listed your wireless card. An you can search through the forum for how-tos.

---

### Post by qki2philip on 2007-05-03
When I enter **lspci** in terminal it displays the following line regarding wireless:

03:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by divague on 2007-05-04
I have broadcom 4306, i installed bcm43xx-fwcutter and it automatically installed the drivers, but i don' know if that will work for you card,.You could try this how to:

[http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318)

hope it helps

---

### Post by qki2philip on 2007-05-04
Installing that did work!  Thanks everyone for your help.  Now I need to see if I can get WoW to run :)

---

### Post by Blacktalon on 2007-05-04
You can play WoW through a number of things, like Cedga, Wine, or my personal favorite CrossOver

---

### Post by loserboy on 2007-05-07
yea I used wine to play Wow and it worked fine, just search around for  "howto Wow and wine" or something like that

---


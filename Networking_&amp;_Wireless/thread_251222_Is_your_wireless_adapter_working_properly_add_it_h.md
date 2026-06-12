---
title: "Is your wireless adapter working properly? add it here!"
date: 2006-09-05
forum: Networking &amp; Wireless
---

### Post by japs_it88 on 2006-09-05
Hi everybody.
   I'm having problems making my PCI network adapter (US robotics mod.5416) work under linux. The first thing I did was looking on the internet if my device was supported, but unfortunately i didn't find any community maintained list of tested/working products.

   This post wants to be a database of working network adapters, cards and similar, so please add the brand, model and if possible the way you made your device work under linux, plus any additional note that might be useful for people who need to make their own device work or still have to buy it and they want a good advice on compatibility.

---

### Post by wieman01 on 2006-09-05
Intel IPW2200 >> Recognized out of the box
Linksys wusb54g v4 >> ndiswrapper & native Windows driver

Both run with WPA2 enabled.

---

### Post by blaamann on 2006-09-05
3Com® Wireless 11a/b/g PCI Adapter

Product # 3CRDAG675B

Works with the madwifi drivers

---

### Post by garrye on 2006-09-05
Most any card using Atheros chipsets.  See blah blah below...:-D 

Two wireless cards that I've tried simply work "out-of-the-box".  A D-Link DWL-G650 PCMCIA card and another off of eBay, a Mini-PCI card  Model#: XG-621-n4cnw 802.11 b/g.  The latter is one of many to be found.  They are part of a nation-wide liquidation of cards that (my guess) appear to have been made by/for Nortel Networks.  Finding winbloze drivers that work for these cards is super difficult.  However with Ubuntu 6.06 LTS they work like a charm. I've tested unsecured networks as well as WEP40, WEP104, WPA, AND WPA2 security layers.  These cards DO NOT support WPA2.  Not many adapters do.  With WPA, while these adapters support TKIP and AES/CCMP I cannot get any useful rates of data transfer using AES/CCMP.  But hey WPA/TKIP ain't bad.  Just try cracking the security on one of those connections some time!!!  I live in a neighbourhood populated by a truckload of noisy 2.4 Ghz riff raff equipment and a handful of wannabe wardriving script kiddies that love to vandalize peoples' wifi networks.  Given this environment, wifi stuff has to be good to survive.  I'm currently using an Acer Aspire 3003 WLCi with the above XG-621 retro fitted as this lappy orginally shipped with Broadcom 4318 wireless silicon and I didn't like having to use NDiswrapper to get it to work. I use the laptop in a production environment.  I does all my business email, and also serves to test and set up peoples' DSL connections.  About the only time I end up booting into winxp is when somebody phones me with a support request and I end up starting winxp so we can have a common frame of reference.

---

### Post by garrye on 2006-09-05
.

---

### Post by acorn22 on 2006-09-05
Linksys Wusb54G v4

installed ndiswrapper (but never ran it or gave it windows drivers)

Works, but is iffy cuz sometimes i have to unplug it to start

---

### Post by compuguy1088 on 2006-09-13
> **garrye said:**
> Most any card using Atheros chipsets.  See blah blah below...:-D 

Two wireless cards that I've tried simply work "out-of-the-box".  A D-Link DWL-G650 PCMCIA card and another off of eBay, a Mini-PCI card  Model#: XG-621-n4cnw 802.11 b/g.  The latter is one of many to be found.  They are part of a nation-wide liquidation of cards that (my guess) appear to have been made by/for Nortel Networks.  Finding winbloze drivers that work for these cards is super difficult.  However with Ubuntu 6.06 LTS they work like a charm. I've tested unsecured networks as well as WEP40, WEP104, WPA, AND WPA2 security layers.  These cards DO NOT support WPA2.  Not many adapters do.  With WPA, while these adapters support TKIP and AES/CCMP I cannot get any useful rates of data transfer using AES/CCMP.  But hey WPA/TKIP ain't bad.  Just try cracking the security on one of those connections some time!!!  I live in a neighbourhood populated by a truckload of noisy 2.4 Ghz riff raff equipment and a handful of wannabe wardriving script kiddies that love to vandalize peoples' wifi networks.  Given this environment, wifi stuff has to be good to survive.  I'm currently using an Acer Aspire 3003 WLCi with the above XG-621 retro fitted as this lappy orginally shipped with Broadcom 4318 wireless silicon and I didn't like having to use NDiswrapper to get it to work. I use the laptop in a production environment.  I does all my business email, and also serves to test and set up peoples' DSL connections.  About the only time I end up booting into winxp is when somebody phones me with a support request and I end up starting winxp so we can have a common frame of reference.

I have a similar laptop, a Acer Aspire 3003 WLCi, and the Broadcom 4318 is a piece of junk, could never get it to work reliably, in the end, I bought a Intel 2200BG mini-pci card, works very well, expcept for odd connection dropping issues, which I'm working on.

---

### Post by dannyboy79 on 2006-10-16
Netgear WG511T works out of the box. I believe it has the Atheros AR5212 chipset. For some reason though, after long inactivity I'll come back to my laptop to find it is disconnected and I have to do a sudo ifdown ath0 and then a sudo ifup ath0 and it will start working again. and then if that doesn't work, i'll do a sudo ifdown ath0 and remove the card fro mit's pcmcia slot, wait a sec, then plug it back in and do the sudo ifup ath0 and it'll be flying again.

---

### Post by wieman01 on 2006-10-16
> **dannyboy79 said:**
> Netgear WG511T works out of the box. I believe it has the Atheros AR5212 chipset. For some reason though, after long inactivity I'll come back to my laptop to find it is disconnected and I have to do a sudo ifdown ath0 and then a sudo ifup ath0 and it will start working again. and then if that doesn't work, i'll do a sudo ifdown ath0 and remove the card fro mit's pcmcia slot, wait a sec, then plug it back in and do the sudo ifup ath0 and it'll be flying again.
I had similar timeout issues until I changed my router's settings a bit. In my case I had to set the "beacon interval" to 10 rather than 100 (being the default). That did the trick and I have not had a timeout ever since. This somehow points to the router... Give it a go.

---

### Post by RLR on 2006-10-18
D-Link DWL-G650M
Works via ndiswrapper and Win2000 driver from Dlink website.
Installed using ndis-gtk, works great!

---


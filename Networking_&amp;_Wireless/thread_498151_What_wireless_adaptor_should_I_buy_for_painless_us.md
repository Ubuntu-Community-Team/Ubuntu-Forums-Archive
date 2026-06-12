---
title: "What wireless adaptor should I buy for painless use w/ Feisty?"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by fitzhugh on 2007-07-11
I'm running Kubuntu 7.10 on a desktop, so I figure a PCI card would be right. I have never set up any wireless networks, but otherwise have a decent amount of hardware and a good amount of unix and linux experience, so I don't mind playing around. However, I would much prefer to buy something that just worked out of the box. Any suggestions?

I tried stopping by (unnamed horrible ripoff store down the street) and bought a linksys WMP54G, not realizing it had sat on the shelf for over a year, nor knowing that there were so many problems with wireless and linux. I've tried ndiswrapper but the drivers on the cd didn't work, and I tried getting other drivers from linksys but they are only downloadable as .exe files which don't unzip or unshield. I am not at all sure the problems weren't my doing rather than the drivers, but I think so.

Please give me any advice you can about cards that work - I really can't get away with stringing ethernet across the house since I just moved - the housemates would not appreciate it :)

THANK YOU!
Fitzhugh

---

### Post by Qrk on 2007-07-11
I've found that the most likely to work are atheros and ralink.

[http://www.ralinktech.com/](http://www.ralinktech.com/)

[http://www.atheros.com/news/linux.html](http://www.atheros.com/news/linux.html)

I've also heard good things (and bad things) about belkin. Support can vary across the same brand names (which can use different chipsets), so be sure to search the model number before you buy.

---

### Post by rfdeshon on 2007-07-11
I have an Intel Pro Wireless 2200 card that works great out of the box. Also, the Intel Pro Wireless 3945 is supposed to work just as well if not better. Other than that, go to [https://wiki.ubuntu.com/CategoryNetworking?highlight=%28%28WifiDocs%7CWirelessCardsSupported%29%29](https://wiki.ubuntu.com/CategoryNetworking?highlight=%28%28WifiDocs%7CWirelessCardsSupported%29%29) for a more complete list of what is/is not supported. Look for something that works "Out of the box"

---

### Post by rfdeshon on 2007-07-11
> **rfdeshon said:**
> I have an Intel Pro Wireless 2200 card that works great out of the box. Also, the Intel Pro Wireless 3945 is supposed to work just as well if not better. Other than that, go to [https://wiki.ubuntu.com/CategoryNetworking?highlight=%28%28WifiDocs%7CWirelessCardsSupported%29%29](https://wiki.ubuntu.com/CategoryNetworking?highlight=%28%28WifiDocs%7CWirelessCardsSupported%29%29) for a more complete list of what is/is not supported. Look for something that works "Out of the box"

Correction... go here for a list of cards [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) sorry!

---

### Post by kevdog on 2007-07-11
I'd probably support the assertion that either Atheros or Ra cards work very well.  Ra cards in my experience with Feisty dont exactly work out of the box with Ubuntu.  Some compilation of serial monkey drivers are needed.  Also they dont work well with network manager.  

Some Atheros cards seem to work out of the box, some dont.  Sorry I cant be more specific.  

I own a Broadcom chipset.  Depending on the version of the card I would rate these cards as very tempermental.  Most people have problems configuring their cards to work, but in the end, most work well with ndiswrapper.

---


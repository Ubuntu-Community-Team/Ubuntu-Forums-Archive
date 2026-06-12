---
title: "Will the Netgear wnda3100 v2 wifi USB work in Ubuntu?"
date: 2014-11-27
forum: Networking &amp; Wireless
---

### Post by Tar_Ni on 2014-11-27
Hi,

I have a desktop computer at home plugged to the internet with an ethernet cable that has Lubuntu installed on it and someone offered me a wireless adapter for free as he no longer uses it. We have wifi at home so that can be useful.

It is a **Netgear wnda3100 v2** ([http://www.netgear.com/home/products/networking/wifi-adapters/WNDA3100.aspx](http://www.netgear.com/home/products/networking/wifi-adapters/WNDA3100.aspx))

My question is: Will it work out-of-the box in Ubuntu/Lubuntu? Is it supported by the kernel?

I am an unexperienced user when it comes to the technical aspect of Linux and I don't want to bang my head on the wall just to get that piece of hardware working.. So if this model is proved to work without too much trouble on Ubuntu, I would be inclined to accept his gift.

Thanks.

---

### Post by slickymaster on 2014-11-27
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by chili555 on 2014-11-27
> My question is: Will it work out-of-the box in Ubuntu/Lubuntu? Is it supported by the kernel?No. Not maybe. No.

There are plenty of tear-stained threads of 100 replies or so about this and, actually, using ndiswrapper, some of them get it working. There are also plenty of threads about working out of the box USB wireless devices. Save yourself and me some pain; read the latter.

---

### Post by JeQhdMD on 2014-11-27
If you do want (for future reference), usb wifi adapters that work out o'the box . . . see below:

 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
|| Brand || Model || Chipset || Driver || Plug and Play || Phone ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 TP-Link || TL-WN722N || AR9271  || ath9k_htc || Yes ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 TP-Link || TL-WN822N || AR7010 || ath9k_htc || Yes ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 """"" || """"" || AR9287 || """"" || Yes ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  Airlink || AWL5088 || RTL8188CUS || ??? || Yes ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 """" || """" || RTL8192CUS || ??? || Yes ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 Panda || Ultra Wifi || RTL8188CUS || ??? || Yes ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 """" || """" || RTL8192CUS || ??? || Yes ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 Edimax || EW-7811UN || RTL8188CUS || ??? || Yes ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 ASUS || USBN13 || RTL8188CUS || ??? || Yes ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

---


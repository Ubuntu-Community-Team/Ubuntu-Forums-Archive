---
title: "Gateway 7422GX and Wireless card"
date: 2005-11-26
forum: Networking &amp; Wireless
---

### Post by rg3000 on 2005-11-26
OK, I have managed to get my wireless card installed, it is listed in the network list.  It is a broadcom card.  It seems that all is working correctly.  The problem is that on this laptop, Gateway has a put a feature where you can turn your wireless card off via (function + f2), when Ubuntu is running, I cannot turn the WiFi card on and the indicator for WiFi is not on so I am assuming that it is not looking for a signal.

Can anybody help me out here?  Does the function key work with Ubuntu or is there a command I can type in the Terminal to turn it on?

Thanks

rg3000
[email]rwgood@gmail.com[/email]

---

### Post by kryton9 on 2006-11-27
I am in the same boat. I am new to linux and ubuntu, but in the device manager it does show my wirless as a broadcom card, which it is. It shows my regular network card too, but I use the wireless on my notebook, so will be great to know how to turn on the wireless with the FN + F2 as it is in windows.

Thanks.

---

### Post by Er1ck on 2007-09-09
I got mine working by installing the latest version of ndiswrapper from [http://ndiswrapper.sourceforge.net/joomla/index.php](http://ndiswrapper.sourceforge.net/joomla/index.php) and also getting the 64-bit driver from [http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php) or for 32-bit drivers look at the list from ndiswrapper for broadcom BCM4306....mine was rev 03  adn had 14e4:4320 as its location when I ran lspci and lspci -n  I had to install a few packages before I could complie and run the latest version of ndiswrapper. I will post a better guide later, but for now....I basically blacklisted the bcm43xx default driver provided and ndiswrapped one of the drivers provided from the links above and then I just turn on the wireless with the function keys and everything worked.

---


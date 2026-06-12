---
title: "What have i done to my wireless card (acx 111)"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by karachuonyo on 2008-07-16
Another dreaded acx 111 wireless problem. I could not connect wirelessly with the generic drivers so followed this how-to [http://ubuntuforums.org/showthread.php?t=434983&highlight=ACX+111](http://ubuntuforums.org/showthread.php?t=434983&highlight=ACX+111) and installed the win drivers using ndiswrapper. Ndiswrapper shows the driver is installed properly and the module is loaded at boot. Now however network manager reports I have no wiress card. lspci -v shows my card is present and correctly identified but iwconfig shows no wireless extension. In fact the red power led on the card is off. Card is still working under my XP dual boot.

---

### Post by karachuonyo on 2008-07-17
24 hrs later and no ideas. So i get the wifi card working again but still not connecting to my network, even when encryption is off. Strange that when working on the terminal with unencrypted network i get connected and an ip address assigned but network manager displays no connection and obviously no internet.

---


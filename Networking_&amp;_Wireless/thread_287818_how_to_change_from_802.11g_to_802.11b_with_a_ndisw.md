---
title: "how to change from 802.11g to 802.11b with a ndiswrapper driver?"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by Starlight on 2006-10-29
Hello! I installed a wireless card driver on my Ubuntu using ndiswrapper... and it almost works. I can see a list of access points, but I can't connect to any of them. I don't have such problems on Windows, and I'm using the same driver here. I've noticed that when I do iwconfig, it lists my wireless card as 802.11g... at the same time, in Windows it says it's 802.11 b/g mix. Maybe that's the reason why it doesn't work in Linux... How can I switch it from 802.11g to 802.11b?

---

### Post by Starlight on 2006-10-29
I found out how to do it, but it didn't fix the problem... I still don't have internet connection on my Ubuntu, and I think I tried everything... :(

---

### Post by wieman01 on 2006-10-29
What chipset are you using? Broadcom?

---

### Post by Starlight on 2006-10-29
I don't think so... I'm using Ralink RT61

---

### Post by wieman01 on 2006-10-29
*"Driver: Don't use driver that ships with card, it didnt work with ndiswrapper. Use the close source driver from Ralink [http://www.ralinktech.com](http://www.ralinktech.com). It compiles for 2.4 and 2.6 kernels."*

Comment taken from this site: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")

Apparently you need to use a driver different than the one that comes with the card.

---

### Post by Starlight on 2006-10-29
Thanks :)

Well, I tried to use the driver from Ralink, but I had problems with it which I posted here: [http://www.ubuntuforums.org/showthread.php?t=287330](http://www.ubuntuforums.org/showthread.php?t=287330)

---


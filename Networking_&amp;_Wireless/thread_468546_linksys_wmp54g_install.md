---
title: "linksys wmp54g install"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by castles on 2007-06-09
I've been trying to get this silly wirless card to work in ubuntu feisty for the last few weeks.

Ubuntu seems to of installed it fine but it won't lock onto a connection at all. I've tried all the different encryption types (even no encryption). I've tried using ndiswrapper etc etc

I just found this wiki... [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)

and from the comments it seems I need to blacklist a driver...

Works only in Feisty if you put to "blacklist" the "rt61pci" module BEFORE install the card. If not, your computer will freeze often. There is an other module: "rt61" it works fine, with WEP too.

How exactly do I do this and any other suggestions?

---

### Post by K-Man_22 on 2007-06-19
How to blacklist a kernel module?

[Description here]("http://wiki.ubuntuusers.de/Kernelmodule#head-e183eac150d93c856d29f5f247a16fedea87932d")

---

### Post by MeeMaw on 2007-06-19
and this is a good tutorial......

[http://ubuntuforums.org/showthread.php?t=419709&highlight=rt61](http://ubuntuforums.org/showthread.php?t=419709&highlight=rt61)

I'm sure you can get it going.

---


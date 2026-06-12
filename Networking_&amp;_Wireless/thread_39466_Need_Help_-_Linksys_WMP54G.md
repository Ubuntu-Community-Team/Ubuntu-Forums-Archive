---
title: "Need Help - Linksys WMP54G"
date: 2005-06-05
forum: Networking &amp; Wireless
---

### Post by I3roknI3ottle on 2005-06-05
Well I installed Ubuntu today because I didnt like Mandrake and SuSe 9.1 was having problems.  So far I like Ubuntu but I cant figure out how to connect to the internet with my wireless card: Linksys Wireless - G PCI Adapter, Model #: WMP54G.  Any help would be appreciated. 

off to bed, hope u guys can help me  :grin:

---

### Post by poofyhairguy on 2005-06-05
[QUOTE=I3roknI3ottle]Well I installed Ubuntu today because I didnt like Mandrake and SuSe 9.1 was having problems.  So far I like Ubuntu but I cant figure out how to connect to the internet with my wireless card: Linksys Wireless - G PCI Adapter, Model #: WMP54G.  Any help would be appreciated. 

off to bed, hope u guys can help me  :grin:[/QUOTE]


You need ndiswrapper.

[http://www.ubuntulinux.org/wiki/HowToSetUpNdiswrapper](http://www.ubuntulinux.org/wiki/HowToSetUpNdiswrapper)

---

### Post by I3roknI3ottle on 2005-06-05
I noticed that NDIS Wrapper allows ubuntu to use windows .inf files, but when installing my card on windows the driver i always point it to is not a .inf, but a .sys.

the file my card asks for when installling is rt2005.sys

---

### Post by meldroc on 2005-06-06
I got mine working using ndiswrapper.

Edit: I forgot, you might want to look at [http://www.ubuntulinux.org/wiki/HowToSetUpNdiswrapper](http://www.ubuntulinux.org/wiki/HowToSetUpNdiswrapper)

I found that page very helpful.

---


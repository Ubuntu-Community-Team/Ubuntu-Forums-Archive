---
title: "Ndiswrapper + Dell Truemobile 1450. Head's about to explode!"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by utrob on 2007-01-04
After managing to get through the installation stage without damaging my winxp installation, i've hit another snag. The internet. Now i'd read wireless is difficult in Linux however on [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#D](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#D) my card is listed. 

Card: Dell Wireless 1450 Dual-band (802.11a/b/g) USB 2.0 Adapter

    * pciid: 413c:8104 Dell Computer Corp.
    * Driver: DELLNIC.INF as shipped on CD.
    * Other: ndiswrapper 1.2, kernel 2.6.11-1.1369_FC4 on Fedora Core 4. 

Now as far as I can tell from other forum posts i need to install ndiswrapper first.  I tried following [http://www.ubuntuforums.org/showthread.php?t=327098&highlight=dell+1450](http://www.ubuntuforums.org/showthread.php?t=327098&highlight=dell+1450) before realising that was for 6.10 and im on 6.0.6 (Does it make a difference?). But anyway i got ndiswrapper-utils=1.1_1.1-5_i386.deb onto ubuntu and tried sudo dpkg -i. Failure. I believe i may be missed the kernel? But as a complete Linux noob all this code is about to make my head explode! 

I just want my card working! 

Ps i have the DELLNIC.INF - totally unsure about the others.

Thanks in advance

---


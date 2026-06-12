---
title: "Linksys WPC 11 ver4"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by joelw135 on 2007-05-05
I can't get Ubuntu to reconize my Linksys WPC11 ver 4 PCMCIA card. Any hints would be welcome. thanks. I was running from the CD not HD.

---

### Post by fwheeler_1 on 2007-05-07
Hi- Try these 2 threads

[http://ubuntuforums.org/showthread.p...ght=fwheeler_1](http://ubuntuforums.org/showthread.p...ght=fwheeler_1)

[http://ubuntuforums.org/showthread.p...ght=fwheeler_1](http://ubuntuforums.org/showthread.p...ght=fwheeler_1)

There are 2 basic approachs: 1) install Windows drivers for the card via ndiswrapper or it's gui equivalent, 2) unblacklist the native driver and see how that works. These approaches are described in the threads.

Good luck, Fw

---

### Post by joelw135 on 2007-05-07
Your links are not working, can you please provide them again?

---

### Post by Titus A Duxass on 2007-05-07
I have the same card, it works out the box with Dapper.
Mine has the 8180 chipset.

---

### Post by joelw135 on 2007-05-07
OK maybe I am doing something wrong. I am running Ubuntu off the CD, but after it is finished initializing I don't see the PCMCIA card.

---

### Post by fwheeler_1 on 2007-05-07
Sorry for the links that didn't work.  Try this post to use the native driver:

[http://ubuntuforums.org/showthread.php?t=414594&highlight=fwheeler_1](http://ubuntuforums.org/showthread.php?t=414594&highlight=fwheeler_1)

I've lost the link for using the Windows driver with ndiswrapper, but if you search the forum for "wpc11 ndiswrapper", you should be able to find it.  The basic idea is to use the Windows driver that came with the card or can be downloaded, and some special software that allows Windows wireless drivers to work with Linux.  You may need to try both to see which works best for you, but the native driver approach is pretty quick to try since all of the software is already on the Ubuntu CD.

Good luck, Fw

P.S.  The card not showing up while using the Live CD (and a subsequent HD install) is the typical problem these two solutions aim to solve.

---


---
title: "Linksys usb wireless network adaptor not pleasing me right now..."
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by parkland on 2008-03-11
Why dosnt my ubuntu pc use my recently installed "linksys usb 802.11b" network adaptor?

What do i haVE to do to make it work?

what a PITA!!!!  

Still, not enough of a PITA to consider using windows again!

help?~

---

### Post by kevdog on 2008-03-11
You need to discover the chipset on the device (google=friend) so we can direct you.  Either that or crack it open to look at the processor inside (which no joke someone did once and sent me a picture -- too bad I cant remember the post - it was a great picture -- still remember it said Ra right on the device).

---

### Post by parkland on 2008-03-11
biggest ic, guessing the cpu, is "ATMEL" AT76C505,  56781-2 , 3J2622,  0404 KOREA

---

### Post by rustybronco on 2008-03-11
looks like Linksys wusb11v2.8 uses that chipset.
is it a wusb11-v2? (look on the device)

---

### Post by parkland on 2008-03-11
YES! YES! its model NO. wusb11 ver.2.8

---

### Post by rustybronco on 2008-03-12
The chipset does not appear to be supported natively so the only solution is to use ndiswrapper with the proper windows drivers.

ndiswrapper how-to's 
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/)

---


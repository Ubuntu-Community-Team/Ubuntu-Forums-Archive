---
title: "wlan0 doesn't support monitor mode"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by kbsuperstar on 2007-02-04
I'm using the aircrack suite to test my wireless network security, and it appears that my integrated wireless card (broadcom 4311 chipset) doesn't support "monitor mode."

Is there a way to patch this or install a driver to make it support monitor mode??

Or, I can probably buy a non-integrated wireless card. Which would you suggest, based on price, ease of Ubuntu detection and/or ndiswrapper-compatability, and IT MUST BE ABLE TO RUN IN MONITOR MODE! (ha ha, obviously :))


Please and Thank You!

EDIT:
Ok, apparently you can't enable monitor mode with Ndiswrapper, but what wifi cards would you suggest me buying :D?

---

### Post by jml on 2007-02-04
The card that I use for monitor mode work is the Cisco Aironet 802.11 a/b/g card.  Its a bit pricey, but I think its worth it.  Cisco supports Linux by offering Linux drivers for this card from their web site.  Therefore many Linux distros (including Ubuntu) support this card out of the box.  The card supports monitor mode, (not all cards do.)  This card comes with a very sensitive receiver, and a slightly more powerful transmitter so I tend to get better range from this card compared to cheaper ones.  If you don't need 802.11 a or g compatibility, you might try to buy an older Cisco Aironet 350 802.11 b card.  It also supports monitor mode and if you can find it, will cost less then the other card.

By the way, if you are really into Pentesting, you might want to check out these live CD's:

Knoppix STD
Phlak
Bactrack

They are all live CD's loaded with software to test network security.  To be used only for purposes of good   ;-)

Joe

---

### Post by tturrisi on 2007-02-04
I have cards with atheros chipsets, they all support rfmon mode.
I have a card w/ an acx chipset, it supports rfmon mode.
I have a card w/ an agere chipset. it too supports rfmon mode.
aircrack cards:
[http://www.wirelessdefence.org/Contents/AircrackORIGINAL.html](http://www.wirelessdefence.org/Contents/AircrackORIGINAL.html)
aircrack_ng cards:
[http://www.aircrack-ng.org/doku.php?id=compatibility_drivers](http://www.aircrack-ng.org/doku.php?id=compatibility_drivers)
what chipset is in card X?
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

---

### Post by jml on 2007-02-04
I forgot to mention, both Cisco cards are based on the Atheros chip set.  Another less expensive card that has the same chip set is the NetGear WG511T.  It supports 802.11 b and g.  I didn't mention it earlier because I have not used it in monitor mode so I could not be sure it would do what you want.

---

### Post by tturrisi on 2007-02-05
all atheros cards
[http://customerproducts.atheros.com/customerproducts/ResultsPageBasic.asp](http://customerproducts.atheros.com/customerproducts/ResultsPageBasic.asp)

---

### Post by bkj1 on 2007-03-17
JML:

did you have to do any patching to get the cisco card into monitor mode?  i am thinking of gettting one of these cards.

---


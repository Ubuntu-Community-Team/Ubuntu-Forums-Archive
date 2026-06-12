---
title: "Need Help"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by ikegreg40906 on 2007-01-03
I Just Installed A Second Hard Drive In My Computer So I Installed Ubuntu With Linux 2.6.  I Have A Belkins F5d7000 Wireless Dexktop Driver Install And I Wanting To Have It Workwith  The Hard Drive With The Ubuntu.  Can Anyone Tell Me The Procedure On Doing This?

---

### Post by c.dric on 2007-01-03
Hey, 

According to [the list of supported wireless cards]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"), Version 3 of this card should work out of the box. 

Version 1 however needs ndiswrapper and the bcmw15a.inf driver

You could try the following command to get more info about your hardware

**sudo lshw -C network**

it should state if your card is a V1 or V3.

just ask here if you need more help.

---

### Post by ikegreg40906 on 2007-01-03
It's The Version 3 Driver.

---

### Post by c.dric on 2007-01-03
Lucky you :D 

the correct driver for your card should already be loaded and your card should appear as ra0 in your networking utility.

[here is a page]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500") with all the info to setup your card with wep or wpa, if you ever need it.

---


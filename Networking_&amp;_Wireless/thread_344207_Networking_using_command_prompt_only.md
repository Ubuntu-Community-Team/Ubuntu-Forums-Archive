---
title: "Networking using command prompt only"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by SDL on 2007-01-22
Hi

I'm very new to Linux and have been struggling to get the whole thing working. The pc crashes when I enter the GUI (if you can help with this problem I have another thread here: [http://ubuntuforums.org/showthread.php?t=343270]("http://ubuntuforums.org/showthread.php?t=343270")

Anyway, from browsing through the forums it seems like some of the things that I could do to help myself solve this problem would involve internet use. Can anybody help me set up a wireless internet connection using command prompt only please?

My network details are:
BT ADSL Wireless Router 1800HG for BT Yahoo Broadband
BT Voyager 1040 PCI Adapter

The current settings are:
WEP encryption
SSID broadcast disabled

I hope that I have included enough information.

Thank you very much for any help that you can give me.

Stephen.

---

### Post by chili555 on 2007-01-22
You will need ndiswrapper installed on your machine. You face a Catch 22: without internet access, how can you get the ndiswrapper packages, and ndisgtk which, IMO, make this all pretty easy, as well as the .inf files you need? Another computer and a USB thumb drive may be helpful.

Here is a site that will be helpful: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)

Especially, this:

Card Name: BT Voyager 1040

    * Ndiswrapper version: 1.2
    * Chipset name: Broadcom BCM4306KFB
    * PCIID: 00:09.0 Class 0280: 14e4:4320 (rev 03)
    * Windows driver location: Driver: [ftp://ftp.support.acer-euro.com/notebook/aspire_1500/drivers/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_1500/drivers/80211g.zip)
    * Other: Needs both *.inf files in same directory but use BCMWL5A.INF for ndiswrapper driver install. 

ndisgtk should let you configure the card just fine.

Let us know and come back if you need help.

---


---
title: "wpc54gs on 7.04"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by unknownerror on 2007-06-05
Has anyone gotten there linksys wpc54gs wireless card to work on 7.04 yet ... I looked around the forums for a bit and didn't find anything for 7.04 just a few things for older versions of Ubuntu.

---

### Post by kevdog on 2007-06-05
The answer is yes!!!!!

Please post the results of:
lspci

---

### Post by unknownerror on 2007-06-09
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by kevdog on 2007-06-09
Ok great --

The simplest solution for you (at least initially) is to install the bcm43xx drivers the the fw-cutter method.  This will get you up and running really quick.  Later if you want to install via ndiswrapper to take advantage of maximum 54 MB/s vs 11 Mb/s you can, but at least you will have a working network connection that you can use to download all the files for the ndiswrapper approach.

Here's the link that got me up and running:

[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

 You will need to download some of these files on a different computer, put them on a USB stick, and then bring them over to Ubuntu.  Specifically use the wl_apsta.o driver instead of any linksys cd for the driver.

---

### Post by unknownerror on 2007-06-09
I can go online via wired connection how would I go about installing the drivers using ndiswrapper, sorry still kind of new at this.

---

### Post by kevdog on 2007-06-10
Im going to point you to two links:

1. Im helping this other guy with the same exact problem -- he has a different card than you, so you will need a different driver than his.  It should be fairly evident if you read the post how you can find your card.  Here is the link to the other post:  (You might want to skip about the first page and a half -- its a bunch of people b**chin' -- really annoying!)
[http://ubuntuforums.org/showthread.php?t=468269](http://ubuntuforums.org/showthread.php?t=468269)

2. Most of my post's instructions are taken directly of the ndiswrapper website itself.  Here is the link to the installation instructions.  They are actually very easy to follow.  This site combined with previous post should most likely get you going.
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

Word of warning -- use drivers as found on ndiswrapper website and not your own from linksys disc.

---


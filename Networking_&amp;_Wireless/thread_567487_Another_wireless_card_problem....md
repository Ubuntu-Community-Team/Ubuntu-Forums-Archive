---
title: "Another wireless card problem..."
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by johnjust on 2007-10-04
I'm not sure what's going on here, but my first format (from windows xp to ubuntu 7.04) yielded absolutely no problems whatsoever.  EVERYTHING worked, but then I installed Kubuntu ontop of Ubuntu (and not through apt-get install kubuntu-desktop), and things started acting up.  Now, 3 Kubuntu reformats later, and this final Ubuntu reformat is leaving me crying inside.

My wireless worked the first time with NO problems, so what's the deal?  Moreover, I know that this HP laptop uses a Broadcom driver, and lspci lists NOTHING with "Broadcom" in it.  The HP website has a service pack driver for my laptop, which I downloaded and extracted to find...

::drumroll::

our old friends, bcmwl5.inf and bcmwl5.sys.

Here is my output from lspci:

```

justin@justin-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
justin@justin-laptop:~$ 

```

Now, I'm wondering if the "Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)" is my wireless.  I've installed ndiswrapper, followed many a tutorial both here, and around the net, including ndiswrapper's tutorial, and I still have zero results.

So, where's a good place to start?  This is, technically, my first Linux solo experience (although it's really my 5th) and I really want it to work...  Any suggestions?

---

### Post by kevdog on 2007-10-04
Seems like your card is a prism card that uses the prism drivers.  Are you sure it used to say Broadcom??

Can you post 
lshw -C network??

---


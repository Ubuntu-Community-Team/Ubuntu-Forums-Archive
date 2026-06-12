---
title: "Broadcom Wireless Adapter - Any Fix Yet? (Ubuntu Studio on HP 530 Laptop)"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by dconstruct on 2008-03-17
Hi, I just upgraded to Ubuntu Studio 7.1 on my HP 530 laptop.  I've been searching around for awhile now on a fix for the wifi problem.  I originally had Ubuntu Gutsy and after some tweaking, it worked fine, but I needed some of the software packages that came with Studio so I upgraded and now I'm having trouble getting it to work.

Originally, all I did was go into the Restricted Drivers Manager and check off the wireless adapter and everything worked fine.  This time, I tried that and it installed everything, but the LED still wouldn't turn on.  And, after some MORE tweaking, I was able to turn it on, but the Network Manager icon that was in the top-right corner of my screen in Ubuntu was no longer there, and so I didn't know where to go to select the wireless networks.

I've tried installing NDISwrapper and all that did was remove my "Wireless Connection" from the list of "Wired Connection" and "Modem Connection" in the Network Manager.  So, now that's not even there anymore.  Does anyone have any solid ideas for a fix to this problem?  Is there one yet?  I've been looking all over and nothing I've found seems to work quite right yet.

Here is my lspci info:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 01)
10:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

Let me know if you need anything else.

Thanks!

---

### Post by horatiotigre on 2008-03-17
Hiya,
I'm a new Ubuntu/Linux user and as such, ran into this problem right away with my Dell Truemobile Card, which is a BCM4306. You will want to look at this website:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

This is one of the new Broadcom fixes; drivers made exclusively for Linux. I believe this is as far as the Broadcom chipset is supported as of yet. Unfortunately, I'm not 100% sure if this will work for you as you have the BCM94311MCG. The fix is for BCM43xx.

Regards,
Daniel

---

### Post by dconstruct on 2008-03-17
Through an extensive session of coding and rebooting and coding, I managed to get the blue LED back on, so it's recognizing the card.  I even have my Wireless Connection back in my connections list under my Network Manager application.  But, now, I don't know what I need to do to get my available connections listed in the top-right corner like it was in my previous version of Ubuntu.  Is there some sort of available application that I can get that can allow me to connect to searchable networks?  Or does that not come pre-installed in Ubuntu Studio?

Thanks!

Adam

---

### Post by dconstruct on 2008-03-18
It's fixed now.  I'm online on my wireless connection.  I fiddled around with some stuff and it works.  But, I still don't have any kind of connection manager icon in the top status bar like before.  It was pretty nifty.  Anyone know how I can get that back?

---


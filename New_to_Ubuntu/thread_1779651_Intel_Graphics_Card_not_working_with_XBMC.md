---
title: "Intel Graphics Card not working with XBMC"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by jhazard112 on 2011-06-10
Hi All,

I am trying to get XBMC to work with my XBOX, and I am having some issues. I have an Acer Aspire 7741Z-4433 which has an Intel HM55 Express graphics card. I am trying to install my XBMC to act as my Media Server for a number of reasons, but when I try to run it I get the following error "XBMC needs hardware accelerated OpenGL rendering. Install an appropriate graphics driver." Then gives a site for supported hardware and quit button. I honestly cant tell if my card is on the site or not. It doesnt pop out at me, so first does anyone know if this card is supported? And secondly, if it is how do I get a driver for it? As always thank you so much in advance.

This is from running "lspci":

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 1
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 1
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
04:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)


I hope this helps, one thing that it doesnt show is HDMI which I have and is working. 

hazard

---

### Post by LowSky on 2011-06-11
This is it:
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 1
```

you shouldn't need any driver installed. Intel doesn't have any closed source drivers, and openGL is supported. It should "just work."

Are you running Unity (ie taskbar on the left)?

If so log out, switch to ubuntu classic (no desktop effects) and try again.

---

### Post by jhazard112 on 2011-06-12
Nope not running Unity...hadn't even heard of it before you mentioned it...I figured it would just work as well...is there a possibility that the driver didn't get downloaded or installed properly?  Maybe I need to try and install it or reinstall it...yet another issue not sure how to do that...any more assistance is greatly appreciated.

---


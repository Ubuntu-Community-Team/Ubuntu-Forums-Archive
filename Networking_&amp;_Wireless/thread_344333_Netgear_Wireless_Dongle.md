---
title: "Netgear Wireless Dongle"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by Cholin on 2007-01-22
Hi! I am completely new to Linux based systems and am having a few issues with my wireless. I am using a Netgear Wireless USB Adaptor Model wg111t, as my primary internet connection device. Unfortunately, Ubuntu doesn't automatically recognize the adaptor. The light doesn't even flash. I am looking for a step by step guide on what to do from here. Another thing is that my desktop only has one optical drive, which I use to run the Ubuntu Live CD, so I cannot just install the cd and search for the drivers and my only source of internet is the wireless adaptor. Luckily I have my laptop handy and can search for help this way. Any and all help that you can provide would be great! When I type lspci this is what I get: 
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 00:1f.0
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (HUB #1) (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (HUB #1) (rev 05)
00:1f.5 Muiltimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 120 Pro Ultra TF
02.0a.o Communication controller: Conexant HSF 56k Data/Fax/Voice/Spkp Modem (rev 01)
02.0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139c/8139C+ (rev 10)

---

### Post by funkadelic on 2007-01-22
I have the exact same dongle...

You need to use ndiswrapper - there a tons of tutorials.

TO get things working in Edgy, I had to compile ndiswrapper from source... the repository version didn't work (perhaps this is fixed now)...

Be sure to unplug and re-plug the dongle before you load (modprobe) ndiswrapper.

---


---
title: "Wireless help!"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by Taylorrice16 on 2010-09-12
Hi, I installed ubuntu about 3 days ago. I have been tinkering back and forth trying to get my wireless to work

I cannot seem to figure out a way to handle this issue. Any help is nice!

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 8800M GTS] (rev a2)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
03:00.0 Mass storage controller: Silicon Image, Inc. Sil 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
0c:06.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)

That is my lspci or whatever Idk how it will help but I see people posting it all over the place... so there ya go


help if you can please!

---

### Post by Saint_ on 2010-09-12
Have you tried installing the network manager Wicd?

---

### Post by 3rdalbum on 2010-09-13
> **Saint_ said:**
> Have you tried installing the network manager Wicd?

Don't bother trying this yet... if ever. Someone posted about this card a few days ago, it seems that you need to download the firmware for the card and put into /lib/firmware. Try Google.

If there is no firmware, then installing Wicd and breaking your networking will not help.

---

### Post by Saint_ on 2010-09-13
> **3rdalbum said:**
> Don't bother trying this yet... if ever. Someone posted about this card a few days ago, it seems that you need to download the firmware for the card and put into /lib/firmware. Try Google.

If there is no firmware, then installing Wicd and breaking your networking will not help.

Well according to the thread she started right below this one on page 1, she already has her wireless working, she just can't connect to WPA encrypted connections. I've read threads where wicd can handle WPA whereas the network manager applet on ubuntu has trouble, however as you said who knows, could break everything.

---


---
title: "Broken PCMCIA Card or Ubuntu Prob?"
date: 2005-05-10
forum: Networking &amp; Wireless
---

### Post by sb73542 on 2005-05-10
Hello,

I have Ubuntu 5.04 on an IBM Thinkpad 600.  I bought a Trendnet TEW-421PC 802.11g card, which reportedly works well with ndiswrapper.  However, I'm having major problems.

I have verified that both PCMCIA card slots work with Ubuntu with both my ethernet card and a borrowed 802.11g card.  However, my new Trendnet card is giving me major problems.  It doesn't show up under the PCMCIA devices in hal-device-manager as the others do.  When I insert it, I get this dmesg line: "PCI: device 0000:05:00.0 has unknown header type 7f, ignoring."  And ndiswrapper only tells me that the driver is installed, not that the hardware is present.  

This is my second Trendnet card, I returned the first one (mail order!!) for the same reason, and now the replacement is behaving the same way.  I just find it hard to believe that a reputable company would be selling junk at such a high rate that I happen to get a broken one two times- I wonder if I'm doing something wrong.  Any ideas please?

Thanks for your help!

---

### Post by az on 2005-05-10
I think this card works with the ac111 driver?  Does the module load with hotlug?  Trying to load both the ndiswrapper module as well as the acx111 module can be problematic...

---

### Post by sb73542 on 2005-05-11
[QUOTE=azz]I think this card works with the ac111 driver?  Does the module load with hotlug?  Trying to load both the ndiswrapper module as well as the acx111 module can be problematic...[/QUOTE]
 Thanks for your reply!  Actually, the problem is not yet a driver problem, because I can't get the device itself to be recognized.  Here's lspci:


0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 02)
0000:00:02.0 CardBus bridge: Texas Instruments PCI1250 (rev 02)
0000:00:02.1 CardBus bridge: Texas Instruments PCI1250 (rev 02)
0000:00:03.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 01)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 01)


And here's lspci -n

0000:00:00.0 0600: 8086:7192 (rev 02)
0000:00:02.0 0607: 104c:ac16 (rev 02)
0000:00:02.1 0607: 104c:ac16 (rev 02)
0000:00:03.0 0300: 10c8:0004 (rev 01)
0000:00:07.0 0680: 8086:7110 (rev 01)
0000:00:07.1 0101: 8086:7111 (rev 01)
0000:00:07.2 0c03: 8086:7112 (rev 01)
0000:00:07.3 0680: 8086:7113 (rev 01)


Any ideas?  The problem is trying to prove to the company that the card is broken, since they don't support it on Linux.  Very irritating.  Thanks!

---


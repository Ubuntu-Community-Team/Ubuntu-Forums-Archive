---
title: "SD/MMC card reader doesn't work on my Dell Inspiron 1525n"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by Unikraken on 2009-03-09
I tried posting this in the Dell portion of this forum and got no responses. I searched the forums and everyone else who asked this question also got no responses. Is this question some sort of "the first rule of Dell Inspiron 1525n's is that you don't talk about SD/MMC readers"?

[INDENT]I have a Dell Inspiron 1525n that I have installed the "Dell OS Factory Recovery 8.10 DVD ISO" from here:

[http://linux.dell.com/wiki/index.php/Ubuntu_8.10](http://linux.dell.com/wiki/index.php/Ubuntu_8.10)

I don't know if the SD/MMC card reader worked prior to this with the actual OS that came preinstalled on it, I tried to dual boot with Windows XP and ended up deleting the partition because the XP disc wasn't recognizing the hard drive. Thus I had to install the recovery disk from the dell wiki above. I know it was stupid but I think I've learned my lesson from that now.

The SD/MMC - MS/Pro card reader won't recognize any of my sd cards, whether they be a fairly old 32 Mb card, a newer 128 Mb card, or my newest 1 Gb micro card in an adapter. So it's not the card. The list of known issues doesn't list any problems with the SD card reader that I could find. I could really use some help! Thanks for reading my plight!

I did the command lspci and got this below:
> 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

Which suggests that my computer sees the card reader. Why on earth would it see the card reader but not detect when I put in a card? Is there a way I can manually mount the cards?[/INDENT]

---

### Post by Nxion on 2009-03-09
I replied to you :)
[URL="http://ubuntuforums.org/showthread.php?t=1091652"]
http://ubuntuforums.org/showthread.php?t=1091652[/URL]

---

### Post by Unikraken on 2009-03-10
Ok, Well for some reason my card reader just started working again. For those poor souls who might come across this thread looking for a similar issue, when you push the card in, keep it pushed in for just a second before you let it catch. That's the only thing I did and now the cards are recognized just fine. I'm perplexed!

---


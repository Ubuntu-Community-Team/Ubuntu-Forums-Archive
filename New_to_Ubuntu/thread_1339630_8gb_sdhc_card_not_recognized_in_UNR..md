---
title: "8gb sdhc card not recognized in UNR."
date: 2009-11-27
forum: New to Ubuntu
---

### Post by jarongg on 2009-11-27
running unr on my msi wind u100. is there some package i need to install to be able to use the card reader in my netbook? i am a noob at this type of thing. thanks in advance.

---

### Post by sandyd on 2009-11-27
if your using a ricoh memory card reader, you need sdricoh_cs

---

### Post by jarongg on 2009-11-28
yea, i need to figure out what kind of card reader i have. i don't know where to find that. bump!

---

### Post by eltonw on 2009-11-28
> **jarongg said:**
> running unr on my msi wind u100. is there some package i need to install to be able to use the card reader in my netbook? i am a noob at this type of thing. thanks in advance.
Normally the memory card should mount as a regular storage device / 'hard drive'. [COLOR=DarkRed]You should NOT need any special drivers to use a card reader with linux.[/COLOR]

Are you having problems 'seeing' the card? Perhaps it is not properly formatted, or damaged?

Go to 'Files and Folders' and below, you ought to see the SD card mounted in the 'Volumes' folder. The icon is the same regardless whether it is an SD card or a USB stick

I have a cheap USB card reader that attaches to my Asus netbook, and I have no problems with Ubuntu NBR. The Asus EEE 1000 PC also has a built-in SD slot that reads all my cards, even the micro-SD ones (with adaptor).

[COLOR=DarkRed]Your problem may be something as simple as an improperly inserted card especially if using a 'MULTI-format' card reader.[/COLOR] In that case, check that that the card is not inserted upside-down or in the wrong slot :KS(memory cards and USB sticks should NOT be forcibly inserted). IF you find that you have to use any force, it is an indication that you are incorrectly inserting the card / stick.

HTH;)

---

### Post by tom66 on 2009-11-28
To find out what card reader you have, open Terminal, type "lspci". For my Studio 15, with a Ricoh card reader, I get these results (note the red highlight).

```

thomas@orion:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
[COLOR="Red"]09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)[/COLOR]

```

---

### Post by jarongg on 2009-11-29
found the fix here: [http://filthypants.blogspot.com/2009/03/ubuntu-904-jaunty-jackalope-on-acer.html?showComment=1241059980000#c2470565798415%20208624]("http://filthypants.blogspot.com/2009/03/ubuntu-904-jaunty-jackalope-on-acer.html?showComment=1241059980000#c2470565798415%20208624")

---

### Post by satipera on 2009-12-04
Thanks Jarrong that link worked for my mini as well.

---


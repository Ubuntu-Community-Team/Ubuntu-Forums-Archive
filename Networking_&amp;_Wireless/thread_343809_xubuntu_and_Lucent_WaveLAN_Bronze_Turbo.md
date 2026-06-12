---
title: "xubuntu and Lucent WaveLAN Bronze Turbo"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by antidespotic on 2007-01-22
Hey all,

I recently installed the most stable recent release of xubunto on my Toshiba Satellite  (96mb RAM, 266 MHz Pentium MMX). I would like to get this system working with my equally antique Lucent WaveLAN Bronze Turbo 802.11 card.

This card is probably the oldest card manufactured that is supported by current 802.11 standards. It was a very popular card for several years and was ubiquitous in many places. I believe that it uses an old version of the Hermes1 chipset, and has a throughput of about 2 Mb/sec. It is a "true" PCMCIA card, not a Cardbus card.

This card is known to run with linux but I have not seen any current drivers. Lucent released a Linux driver for it at one point (I think around 1998 or so), but it required merging the driver with the PCMCIA controller drivers in some kind of hideous frankestein procedure.

I tried getting card info using lspci -v | less, but this just gives me information on my PCMCIA bus and a bunch of unrelated hardware hanging off of the pci bus (USB, video card, IRDA port, etc.) The card itself is identified as "Unknown Device 0001"

Has anyone else had any success in getting this card to work with their systems? Is there a universal Lucent driver that I could try? I have heard of people using Ndiswrapper with Windows drivers- something that I attempted with a previous installation of Damn Small Linux- but Ndiswrapper doesn't like the most recent Windows 2000-era drivers for this thing (it shipped with Windows 3.1 and 95 drivers!)

Many thanks.

---

### Post by ingo on 2007-01-23
to get more info on the card remove it, put it in again and run

sudo dmesg

the last few lines are what you are looking for

---


---
title: "What PCMCIA card to buy for Ubuntu?"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by V2JTB on 2009-04-07
What PCMCIA card to buy for Ubuntu for out the box?

---

### Post by Dynaflow on 2009-04-07
It depends heavily upon what you want that card to do.  =)

Are you talking about a wireless card, memory, or what?

---

### Post by V2JTB on 2009-04-07
Wireless card for Internet use with the Ubuntu boot cd

---

### Post by Dynaflow on 2009-04-07
This should tell you what you need to know:  [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by V2JTB on 2009-04-07
Im sorry to be a pain but I am using the Ubuntu CD and can't load drivers.  I already bought a card that was "supported" and It did not work.  I am asking what do people use that woks?

I have spent hours/Days on this forum and have come to the conclusion that I need to buy a card that works.

---

### Post by Therion on 2009-04-07
Hardware Compatibility List to the rescue...

[http://www.ubuntuhcl.org/browse/search+wireless-networking?category=25](http://www.ubuntuhcl.org/browse/search+wireless-networking?category=25)

---

### Post by V2JTB on 2009-04-07
OH my god why is this so hard......Been through both links and I just need a PCMCIA card that people know that works form the CD.

Why is it so hard to use Wifi from the boot CD?

---

### Post by V2JTB on 2009-04-07
Help.................

---

### Post by Dynaflow on 2009-04-08
If all else fails, grab an ethernet cable and plug the sucker directly into a router.

---

### Post by Therion on 2009-04-08
> **V2JTB said:**
> OH my god why is this so hard......Been through both links and I just need a PCMCIA card that people know that works form the CD. 
You mean like the seventh one down on that list I gave you?

---

### Post by gn2 on 2009-04-08
When asking for hardware recommendations, it's important to mention where you are, as what's available varies hugely from one country to another.

If you're in the UK:

[http://tinyurl.com/ca3k2q](http://tinyurl.com/ca3k2q)

[http://www.linuxemporium.co.uk/products/wireless/#pid88169](http://www.linuxemporium.co.uk/products/wireless/#pid88169)

---

### Post by V2JTB on 2009-04-08
I have been through both lists and I can't see new PCMCIA cards that will work "Out the Box" without the need for drivers.

As I want to use the bootable CD.

I am in thr UK (Glasgow)

---

### Post by KIAaze on 2009-04-08
Unfortunately, I don't have a Live-CD at hand right now, but I never had to install a driver for my wireless card:
[edit]It works out of the box with the Ubuntu 9.04 Live-CD! I'm using it right now (with WPA/WPA2). :) Desktop effects working out of the box too by the way. :)[/edit]
```
Digitus
2.4 Ghz 802.11g/b 108Mbps
Product name: wireless cardbus adapter
Model No: DN-7031-A

```

It uses an Atheros chipset, which apparently is a good indication that a card will work under GNU/Linux (at least that's what the vendor told me when I bought it).

The card also works with aircrack for wireless cracking (requires driver patching however). ;)

"sudo lspci -vvnn" output:
```
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01)
	Subsystem: Atheros Communications Inc. Device [168c:1051]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 168 (2500ns min, 7000ns max), Cache Line Size: 128 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at 34000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=2 PME-
	Kernel driver in use: ath5k
	Kernel modules: ath5k

```

> I have been through both lists and I can't see new PCMCIA cards that will work "Out the Box" without the need for drivers.
I'm not sure if any hardware can work without drivers. (I am no hardware specialist though.)
If the list mentions drivers, it might be so you know what driver it works with, not that you have to install the driver manually.
Ubuntu comes with lots of drivers by default I think.

_Other lists:_
[http://www.linuxhcl.org/](http://www.linuxhcl.org/)
[http://hardware4linux.info/](http://hardware4linux.info/)
[http://www.linux-drivers.org/](http://www.linux-drivers.org/)
[http://www.linuxquestions.org/hcl/index.php](http://www.linuxquestions.org/hcl/index.php)

_Online-shops selling GNU/Linux compatible hardware:_
[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)
[http://www.tuxhardware.de/category47_67/default.html](http://www.tuxhardware.de/category47_67/default.html) (German)

---

### Post by V2JTB on 2009-04-08
Thank you so much I have bought the RALINK WIRELESS G PCMCIA WIFI CARD VISTA/LINUX (UBUNTU)from Ebay.   Fingers crossed.

---

### Post by Methuselah on 2009-04-08
> **V2JTB said:**
> I have been through both lists and I can't see new PCMCIA cards that will work "Out the Box" without the need for drivers.

As I want to use the bootable CD.

I think you are under the misconception that since you're using the boot CD the card needs to work *without* drivers.

In general, NO hardware works without drivers.
However, if the card is supported 'out of the box' then the drivers are already included and you do not need to do anything.

For example, the link below provided by another poster says that the referenced card works 'out of the box' since the ancient Ubuntu 6.06 (you're probably installing 8.04 or 8.10).
Sure, he also mentions that it uses the 'madwifi' driver but if it works out the box that driver is already on the CD and you should not have to worry about it.
[Note that I don't personally own this device]
[http://www.ubuntuhcl.org/browse/product+atheros-airplus-xtremeg-dwl-g650-wireless-pcmcia-adapter?id=6538](http://www.ubuntuhcl.org/browse/product+atheros-airplus-xtremeg-dwl-g650-wireless-pcmcia-adapter?id=6538)

HTH

EDIT: I started writing this an hour ago and got distracted before submitting.
I see you've picked a card. Hope it works out.

---

### Post by V2JTB on 2009-04-08
Thank you, Yes I do appreciate that I need drivers.  I just want to learn Linux and to try running it from the boot CD.

To try and use windows from the kick off is very straight forward.  I assumed that Ubuntu would be similar.  To try and load drivers and wrap programes is a bit too much for me just now.  To try and add drivers to a CD is way out just now.

Hence the reason that I am looking for a PCMCIA card that will work from the box.  I have found the lists very confusing when it comes to PCMCIA cards.  

However thanks to the forum I have never thought of buying cards from Ebay, so fingers crossed that I get my card and that my card works "Out of the box".  Thanks gn2.

I understand that to most people this might sound a bit thick, but I need to start some where and I don't want to remove my Vista just yet.

I do apprecaite everyones patience and again thank you.

But buy god its frustrating.......

---

### Post by V2JTB on 2009-04-11
Hi All,

I finally got the Boot CD working straight out the box.

I got the WiFi card from Ebay.

MSI CB54G2

Ralink 2560 PCI rt2500pci

---

### Post by RetchingRabbit on 2009-04-11
> **V2JTB said:**
> 
To try and use windows from the kick off is very straight forward.  I assumed that Ubuntu would be similar.  To try and load drivers and wrap programes is a bit too much for me just now.  To try and add drivers to a CD is way out just now.


Heh. 
Spoken like a man who's never installed Windows.
Build a machine.
Install Windows, your choice of flavors.
You want to talk about driver issues... 
I recommend the exercise for anyone who thinks Linux is difficult....

---

### Post by 3rdalbum on 2009-04-12
> **V2JTB said:**
> To try and use windows from the kick off is very straight forward.

Windows doesn't ship with any wireless drivers included at all. In fact, it doesn't ship with any Ethernet drivers, or sound drivers, or graphics card drivers. Windows XP doesn't ship with any SATA drivers.

You've got the right idea though, about buying Linux-compatible hardware. I applaud that - so many newbies are more willing to buy a $250 upgrade to Windows Vista than a $50 Linux-compatible wireless card :-)

---


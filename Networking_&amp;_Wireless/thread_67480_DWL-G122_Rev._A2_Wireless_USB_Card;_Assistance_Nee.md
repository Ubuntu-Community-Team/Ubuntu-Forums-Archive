---
title: "DWL-G122 Rev. A2 Wireless USB Card; Assistance Needed!"
date: 2005-09-20
forum: Networking &amp; Wireless
---

### Post by OldSchoolNinja on 2005-09-20
Alright, I'm fairly new to Linux and ubuntu, but I don't have much trouble following directions and Googling for answers, but I'm out of ideas. I have a Toshiba Satellite laptop and a D-Link wireless card, and I can't get my wireless to work on ubuntu. I've read almost every thread in this forum about my card, and tried about every set of directions that I could find, and nothing seems to work. I'm using ubuntu 5.04, and my lspci is: 

0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #2) (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #3) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corp. 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801CAM IDE U100 (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corp. 82801CA/CAM AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go] (rev a3)
0000:02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:02:08.0 Ethernet controller: Intel Corp. 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
0000:02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 32)
0000:02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 32)
0000:02:0c.0 System peripheral: Toshiba America Info Systems TC6371AF SmartMedia Controller (rev 03)
0000:02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)

I'm not sure which of these is the card, but since I've been getting various reports on which chipset this card actually uses, I can't get ndiswrapper or the linux-ng drivers to do anything useful at all (though this could certainly be from lack of know-how!). Anyway, I'm just hoping someone on here could help me out. Thanks in advance!

---

### Post by ranf on 2005-09-22
[QUOTE=OldSchoolNinja]Alright, I'm fairly new to Linux and ubuntu, but I don't have much trouble following directions and Googling for answers, but I'm out of ideas. I have a Toshiba Satellite laptop and a D-Link wireless card, and I can't get my wireless to work on ubuntu. I've read almost every thread in this forum about my card, and tried about every set of directions that I could find, and nothing seems to work. I'm using ubuntu 5.04, and my lspci is: 

0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #2) (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #3) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corp. 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801CAM IDE U100 (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corp. 82801CA/CAM AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go] (rev a3)
0000:02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:02:08.0 Ethernet controller: Intel Corp. 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
0000:02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 32)
0000:02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 32)
0000:02:0c.0 System peripheral: Toshiba America Info Systems TC6371AF SmartMedia Controller (rev 03)
0000:02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)

I'm not sure which of these is the card, but since I've been getting various reports on which chipset this card actually uses, I can't get ndiswrapper or the linux-ng drivers to do anything useful at all (though this could certainly be from lack of know-how!). Anyway, I'm just hoping someone on here could help me out. Thanks in advance![/QUOTE]
 Hmm. I don't see a D-Link in this output.
If it is a USB adapter you should post the output of "lsusb".

---

### Post by OldSchoolNinja on 2005-09-23
Ahh, my mistake. It is a USB card. Ok, my lsusb is:

Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 2001:3704 D-Link Corp. [hex]
Bus 002 Device 002: ID 06cb:0003 Synaptics, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

So, it shows up, obviously, but I can't get it to work, for the above named reasons. Help would be appreciated!

---

### Post by davidknibb on 2005-09-24
It seems as if you will need to get the card running using NDISWRAPPER. What this does is to take a relevant windows driver and then WRAP it up in a Linux coat.
I did this recently for my Linksys PCI card, and much to my surprise it only took a few minutes to get it all working perfectly.
The instructions look intimidating - but actually they are fairly stright forward.
Go to
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu#Install](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu#Install)
and go from there.
But before you start print out all of the instructions, and those in the included link referring to Install Windows Driver & Configure Inerface.

David

---

### Post by OldSchoolNinja on 2005-09-26
I've tried to do the ndiswrapper thing, and I don't seem to be able to find the actual driver for my card. When the card is plugged in, ndiswrapper doesn't detect the hardware. I also get varying reports on whether my card uses Prism2 or Prism54 or some other chipset, so I can't even be sure if I have the right driver or not. I spent about 8 hours straight trying to get ndiswrapper to work for me, and I'm just confused as to what I acutally need. I have it installed and ndiswrapper-utils and all that, it just doesn't pick up my card.

Update (9/26/05, 9:10 PM): I got ndiswrapper to say driver and hardware detected, but I still don't have a wlan0, even after doing

ndiswrapper -m
modprobe ndiswrapper

so, I'm still confused.

---

### Post by Yourname on 2006-10-22
Did you ever get this to work?

---

### Post by OldSchoolNinja on 2006-10-24
I have since upgraded to Dapper, and the standard procedure described elsewhere on this forum worked fine. The lights on the dongle work appropriately as well, and the wireless tool (can't remember the name off the top o' my head) picks up networks like a champ.

If you're asking because you wanted to help, I thank you.

If you're asking because you need some help, please let me know.

If you're just asking, well, there you go =D

---

### Post by syphron12 on 2007-05-20
Hey I have the same usb dongle, the D-Link DWL-G122 Rev.A2. I don't know anything about Linux, and am looking to use Ubuntu as a full time desktop operating system. I am unwilling to switch if I cannot get my wireless connection to work. If you could send me a list of things that you did that would be very helpful. I am using Ubuntu Feisty Fawn 7.04.  Please email to [email]j.k@rogers.com[/email]. Thank you.

---

### Post by OldSchoolNinja on 2007-05-20
Actually syphron12, with Feisty, the dongle Just Works (tm). Wireless support in this version is vastly improved, and the new network manager makes it really simple. I haven't tried plugging the dongle in after boot up, but I do know that if it's plugged in before you power on, it'll work like a charm. If you find that this isn't the case, then I'm sure someone on the forum will be glad to help you, whether it's me or someone more knowledgeable about wireless. Happy Ubuntu-ing!

---


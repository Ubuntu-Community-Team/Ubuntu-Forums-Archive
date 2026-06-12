---
title: "I have no idea how to even explain this problem"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by sonhadorpr on 2009-11-12
Hello my fellow Ubunteros of the world!

I have been having these problems with the video refresh, of my Ubuntu 9.10 Karmic Koala, which, I must say it has been a pain to install and operate; nothing seems to work right!
Let me try to explain in words, but I guess the best way is for you to see for yourself, since I may not know what the problem may be, and if I say something, and it just might happen to be something else...so...somebody once said that "a pictures is worth a thousand words". Click [here]("http://www.facebook.com//photo.php?pid=4248685&id=620453227#/album.php?aid=174199&id=620453227") for pictures.

1 problem.
When I grab a window and move it in the desktop, it goes invisible.
I have to run my mouse over it, or better, minimize and maximize window again, in order for it to come back.
If I run a window on top of another app window, they mix icons, and words and letter are "garbled", lines come up and they also sometimes disappear.
Another problem is:
When inside the web-browser, when I scroll up/down, all the pictures, words, lines, flash video, it all gets mixed together.
I will let you see the pictures, and let me know how to fix this problem.
I know it has to be related to video...but I do not know if it has to do with the xorg.conf or what else could it be?...plus, I´m a newbie....so...DKS :-)
Thank you for your time and help.

---

### Post by bawilson2 on 2009-11-12
So sounds like the video drivers aren't setup quite right.  What video card or adapter are you using?  One option might be to just disable Visual Effects in System->Preferences->Appearance->Visual Effects.

---

### Post by lidex on 2009-11-12
Can you post the output of this command?
```
sudo lshw -C video
```
and this one? 
```
lspci
```

Is this x32 or x64 ubuntu? What kind of PC? Clean install or upgrade? What do you see in "system>administration>hardware drivers"?

*Edit: If you don't know how to enter commands, just go to your main menu under "accessories" and click on "terminal". Copy/Paste the commands - one at a time - into terminal and press enter.*

---

### Post by sonhadorpr on 2009-11-12
> **lidex said:**
> Can you post the output of this command?
```
sudo lshw -C video
```
and this one? 
```
lspci
```

Is this x32 or x64 ubuntu? What kind of PC? Clean install or upgrade? What do you see in "system>administration>hardware drivers"?

*Edit: If you don't know how to enter commands, just go to your main menu under "accessories" and click on "terminal". Copy/Paste the commands - one at a time - into terminal and press enter.*

My mistake, I thought I had posted all the specs of my machine.

PC Configuration:
Compaq® Presario™ SR1417CL
1 AMD® Sempron™ 3000+ 
@ 1.81 GHz, Socket 754 (single-core not 64-bit, but just 32)
MB Asus K8S-LA
Compaq motherboard name: Salmon-GL6E 
Bios V3.15 10-19-2005
Chipset: Integrated Audio/Video/Lan SiS 760/964 
1024 RAM PC3200 DDR1 @ 400Mhz
1 Internal WD 320GB HDD Master
1 Internal Maxtor 120GB HDD Slave
1 External SeaGate 500GB USB2.0 HDD
Running Dual-Boot
MicroSoft Windows XP Pro® SP3
Ubuntu 9.10 Karmic Koala

Let me go ahead and do the commands you gave me, and I´ll post again.
Thank you for your willingness to help a newbie!
Ubuntu FOReVER!!

---

### Post by cariboo on 2009-11-12
Even though you didn't do as the previous poster asked, posting the specs helped. The SIS 760 is not very well supported, Can you tell us what driver you are using. Press Alt-F2 and type:

```
gksudo gedit /etc/X11/xorg.conf
```

paste the complete output in your next post.

My suggestion would be to start looking for a video card that is supported better. My choice would be nvidia

---

### Post by sonhadorpr on 2009-11-12
> sudo lshw -C video

*-display UNCLAIMED     
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 cap_list
       configuration: latency=0
       resources: memory:e0000000-e7ffffff(prefetchable) memory:ed000000-ed01ffff ioport:9000(size=128)

**********************************************************************
lspci

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
*********************************************************************
I was in Windows when I rcvd reply to the posts; I had to come back to Ubuntu, and now, it seems to be working fine, until if f%#@$ up again.
Oh, to answer your other question, It is an upgrade from a 9.04 clean install.
The 9.04 was perfect, the 9.10 has been the problematic one.
I guess, I GUeSS...next time, I can just wait a few more months to make a new upgrade; to wait for small kinks to work themselves out, or get fixed.
I DoN'T HAVe To UPGRAde ALl The Time!!

---

### Post by sonhadorpr on 2009-11-12
> **cariboo907 said:**
> Even though you didn't do as the previous poster asked, posting the specs helped. The SIS 760 is not very well supported, Can you tell us what driver you are using. Press Alt-F2 and type:

```
gksudo gedit /etc/X11/xorg.conf
```

paste the complete output in your next post.

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

My suggestion would be to start looking for a video card that is supported better. My choice would be nvidia
********************************************************************

Yeah, most certainly I will consider Nvidia, since you are the 100th person to suggest that brand.

Thank you all for your help.

---

### Post by lidex on 2009-11-12
I would stick with Jaunty for now in your case. Seem to be a lot of issues with upgrading also. Probably better to do clean install. +1 (or +101) for nvidia.

---

### Post by sonhadorpr on 2009-11-12
> **lidex said:**
> I would stick with Jaunty for now in your case. Seem to be a lot of issues with upgrading also. Probably better to do clean install. +1 (or +101) for nvidia.

Well, I don't have an Nvidia card, so...I think I'll leave it alone, until I can get the card, and maybe just wait for Lynx 10.04.
Isn't that gonna be LTS?
Anyway, thanx!

---

### Post by lidex on 2009-11-12
> Isn't that gonna be LTS?
yes:wink:

---


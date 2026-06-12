---
title: "Adjusting Screen Resolution"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by darkeye123 on 2009-10-25
Hello again,

I'm having some trouble adjusting the screen resolution to fit my monitor. I am using an old CRT Samtron 76V monitor, with a max resolution of 1280X1024. However, when I go into System>Preferences>Display, the monitor is unknown, and will only let me change the monitor up to 800X600.

Any Suggestions?

---

### Post by dv3500ea on 2009-10-25
Do you have any graphics drivers installed and what is the model of your graphics card?

---

### Post by darkeye123 on 2009-10-25
As far as I know, I do not have any graphics drivers installed. I'm not sure what graphics card I have, but I the one I have is factory installed and I think is part of the motherboard. Here is the output of lspci:

00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

---

### Post by dv3500ea on 2009-10-25
Do you know the make and model of your desktop/laptop?

---

### Post by darkeye123 on 2009-10-25
No since I got it from a friend. However I do know the motherboard if that helps at all: ECS L7VMM2 REV 1.1 and I have the windows CD with all the drivers on it.

---

### Post by darkeye123 on 2009-10-25
I did a little bit of searching and found out that I have the S3 Pro Savage VT8375.

---

### Post by darkeye123 on 2009-10-25
bump

---

### Post by halitech on 2009-10-25
[color="red"]01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266][/color] <<- video card

S3 uses the openchrome drivers. Look here for more info:

[http://ubuntuforums.org/showthread.php?t=1297349&highlight=openchrome](http://ubuntuforums.org/showthread.php?t=1297349&highlight=openchrome)


also, unless the driver cd has linux drivers on it (highly unlikely) it is pretty much useless to you. Might as well use it for a coaster to put your drink on.

---

### Post by darkeye123 on 2009-10-26
Thanks a lot!

Turns out I needed to run:

sudo apt-get install xserver-xorg-video-via

in order to get the files that supported my Video Adapter.
I think I will use the cd as a coaster!

Thanks again!

---


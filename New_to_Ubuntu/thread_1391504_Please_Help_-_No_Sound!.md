---
title: "Please Help - No Sound!"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by startrekkie96 on 2010-01-26
I have had a dual boot running on my PC for some time, and when Windows went belly up, I've been using Ubuntu more because I'm too lazy to fix it.
BUT: I cannot get Ubuntu to play sound. In fact, I don't even know how to tell you what version I'm running. I think it's 8.04, but have no way to be sure. Anyway, I can't get the computer to play sound, except at login, when it repeats the system beep, a warning beep type of thing. This just loops again and again. It also only plays in my head phones, it won't play on my speakers. This is really ruining the Ubuntu experience for me, and any help would be appreciated a lot! Thank you!

---

### Post by 311005901 on 2010-01-26
Let's see if I can help. :)

First: You can find out which version of Ubuntu you're using by clicking on the top left panel in "System>About Ubuntu".

Second: Open up Terminal (Applications>Accessories>Terminal) and type in ```
lspci
``` Copy and paste the whole text readout.

With that, we might be able to fix your problem. :D

---

### Post by white_ghost on 2010-01-26
What does the lspci show?

I used to have this problem (until about Ubuntu 8.10). On my Toshiba A215-S7422

As I remember, I had to insert 
 
snd-hda-intel model=toshiba

Into the  /etc/modprobe.d/alsa-base?

Someone let me know if I am wrong on this one?

I believe that snd-hda-intel model=
Has alternate models you can pass in place of Toshiba (Ie; acer, dell, etc...), Not sure though.

---

### Post by lyall on 2010-01-26
open System Monitor from System > Administrator 
it show the release, Kernel and which Gnome
hardware : memory and processor
system status - available disk space

look at the following link it might help you solve your sound problem
[https://wiki.ubuntu.com/DebuggingSoundProblems]("https://wiki.ubuntu.com/DebuggingSoundProblems")

good luck and have fun learning

---

### Post by startrekkie96 on 2010-01-26
Lyall: Already tried that link, didn't find anything helpful

From lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9200M GS (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
06:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
06:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

```
When I open "About Ubuntu" I get this:
"Thank you for your interest in Ubuntu 9.04"
So I guess I have 9.04.

---

### Post by 311005901 on 2010-01-27
Thanks for the readout. I'm looking up your issue.

---

### Post by kronictokr on 2010-02-14
try this, has various fixes included, works like a charm

[http://swiss.ubuntuforums.org/showthread.php?t=1395089](http://swiss.ubuntuforums.org/showthread.php?t=1395089)

---


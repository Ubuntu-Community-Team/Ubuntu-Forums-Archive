---
title: "Problems with wireless install - Netgear WG111 (ser# wg72....) &amp; belkin F5D9050"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by mayojs on 2007-04-25
Hi Forum,

I have hacked around unix for many years but this is first serious attempt to do something constructive.

I'm trying to install Linux MCE. I prepped a suitable system and loaded Ubuntu 6.10 . This allows loading of LMCE 1.0, however I cannot get network up.

I'm trying to use Netgear WG111 usb adapter. The adapter I have is a "inbetween" model which starts with serial number WG72xxxxxx. I've read various forum articles, have tried using ndiswrapper and followed other examples but I get errors which I can't get past. I'm trying to use the same driver which works in Windows

I went out and purchased a belkin F5D9050 in the hope that this may work but sadly not. Same issues.

I loaded ubuntu 7.04 which has a better network tool, and the netgear comes up straghtaway which is progress of sorts, however Linux MCE installer is for 6.10 only and the installer happily ignores attempts to load under 7.04.

The main issue seems to be that "if wlan0 up" or any such commands give error "no such device" . For some reason when the netgear is detected by ubuntu it is as eth2.

ndiswrapper stated device present and driver loaded but that's about as far as it gets.

I don't know whether to wait until LMCE becomes available for ubuntu 7.04, or whether to continue down the road of getting a wireless adapter to work with ubuntu 6.10.

I didn't really want to have to get into compiling modules and getting ever deeper into unix, it almost makes me want to give up and put Bill's software back in, however I saw a demo of LMCE and I'm keen to try and make this sucker work.

Any pointers, clues or help greatly appreciated,

John Mayo

---

### Post by mayojs on 2007-04-25
OK, I managed  to make progress myself.

I used the RT73 driver and the Belkin F5D9050, and the following guide

[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

This must be followed meticulously, as I made a few shortcuts and screwed up some of the directory locations, however so far I am installing LMCE and I'm on the internet.

I have yet to reboot to check install OK on reboot and boot config parameters but there is light at the end of the tunnel!!

---


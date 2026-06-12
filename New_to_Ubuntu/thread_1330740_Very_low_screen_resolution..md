---
title: "Very low screen resolution."
date: 2009-11-18
forum: New to Ubuntu
---

### Post by vertigolf on 2009-11-18
Hi everyone!

I have just recently installed Ubuntu 9.10 (dual boot with XP on another hard drive - love having both OS).  The only problem I'm running into right now is that the screen resolution won't go past 800X600.  I have much higher resolution running XP, so it's not a hardware issue.  I've seen a few other problems with this in the forum, but none of the various suggestions have helped so far.  I have installed all the updates available through the update manager, also.

A common thing I've seen requested is the result of lspci, so here is mine.

> 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
05:02.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet (rev 03)
05:04.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)Again, I am very very new with linux.  Experienced computer user, but Windows my entire life.  If you can help me out, I would greatly appreciate it!  Just be aware you may have to explain it to me like I'm 8, since I don't have a very good feel for all this Ubuntu stuff yet. ;)

---

### Post by spikyjt on 2009-11-18
Looks like you might need to try this
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
but you will need to replace references to "jaunty" with "karmic". Shame they don't seem to have fixed the bug that appeared over 6 months ago, but that is a very old GFX card.

---

### Post by vertigolf on 2009-11-18
For some reason, this didn't work for me.  When I replaced the jaunty references with karmic, and followed the instructions, everything worked fine until I typed 

sudo apt-get install xserver-xorg-video-intel-2.4

It came back with an error (sorry, I didn't save the error for a reason you'll soon see) saying that the package couldn't be found.  So I got the bright idea (:roll: or something like that :D)to keep the jaunty references and repeat.  Everything worked great! Until I rebooted.  Then I couldn't get anything at all to display. Booted into windows, wrote down the rollback instructions, and did that, so I was back to square one.

However! Good news, this fix worked great:
[http://www.rushmessageboard.com/cpmb/index.php?showtopic=33283](http://www.rushmessageboard.com/cpmb/index.php?showtopic=33283)
Ran across it in another post, and creating/editing the xorg.conf file seemed to do the trick.  I can now set my display to normal 1024X768 mode.

Thanks for the help! :D

---


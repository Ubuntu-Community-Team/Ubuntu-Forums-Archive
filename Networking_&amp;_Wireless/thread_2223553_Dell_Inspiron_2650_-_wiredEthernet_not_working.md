---
title: "Dell Inspiron 2650 - wired/Ethernet not working"
date: 2014-05-11
forum: Networking &amp; Wireless
---

### Post by Doranwen on 2014-05-11
So this couple asked me to put Linux on two of their laptops.  I already putting Lubuntu on the older one, and am doubting my ability to get it to work:  [http://ubuntuforums.org/showthread.php?t=2222349](http://ubuntuforums.org/showthread.php?t=2222349)

But they'd still like me to get Linux on the faster laptop they have (which is still old).  It's a Dell Inspiron 2650, with 512 mb RAM.  So this time I grabbed the regular desktop version of Lubuntu and fired up the live environment to test.  It loaded, filled the full screen (I was so relieved, after my trouble with the other one), but my first sign of trouble was not being able to get the mouse pointer to work.  Apparently it didn't recognize the touchpad (or keyboard, either).  So after yanking a mouse off another desktop in the house, I started clicking around.  And discovered that Firefox would not load a single website.  With the wired cable plugged in.  I know there's nothing wrong with the cable or the network, because just a few days before I'd been testing the **older** laptop with the same setup, and despite its graphics issues, it had no trouble getting the network to work.

Just to be sure, I tried booting off a Puppy Linux disc I'd had for testing the other laptop--and everything worked, Internet, mouse, keyboard, etc.  But I don't know Puppy Linux (I've only worked in Debian-based environments) and am not comfortable trying to support that.  I'd **like** to get Lubuntu working.  But without working Internet to **start** with, I'm doubting this.

Since network and hardware are separate in these forums (and I can pick up a basic keyboard somewhere else without any trouble), I figured I'd ask for help solving the 'net issue first.  I do not want to try to install Lubuntu on this if I can't even get the 'net working as they do use this computer, and would need to continue using it.  So I need to be able to guarantee that I've found a solution for the 'net before I actually install Lubuntu, or I'll have to look elsewhere for a Linux solution.

This is the output of lspci (which I could access thanks to Puppy Linux):

00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 05)
00:1d.0 USB controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation NV11 [GeForce2 Go] (rev b2)
02:01.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:04.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller


**EDIT:**  Both my computer and this laptop were on the same switch, and mine had 'net the whole time, so it really has me wondering what just happened, as rebooting from the Lubuntu disk the **second** time, the Internet is working.  Still no keyboard/mouse, but using alternates for now, and I'll post in the correct forum for that if I can't figure it out with the help of a friend online.

---

### Post by chili555 on 2014-05-11
> Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)This is a relatively rare device, so, in the manner of Rick in *Casablanca*: "Of all the Linux forums, in all the towns, in all the world, she walks into mine." Oh, well, let's take a look at:```
lspci -nn
```Is your 3Com enumerated as 10b7:9200? If so, it uses the driver *3c59x*. Did it load?```
lsmod | grep 3c59x
```If not, load it:```
sudo modprobe 3c59x
```Was an ethernet interface created, ideally eth0?```
ifconfig
```Or, as I actually suspect, are you unable to connect because the Network Manager icon is mysteriously missing in lubuntu 14.04? Please do:```
nm-applet &
```Does the icon appear and allow you to connect? 

We'll proceed once we know a bit more here.

---

### Post by Doranwen on 2014-05-12
Oh, sorry, didn't see you had replied--at this point, I really have no clue what caused it to not work the first, but since it IS working (albeit mysteriously), I'm not going to complain?  Thanks for trying to help!

---


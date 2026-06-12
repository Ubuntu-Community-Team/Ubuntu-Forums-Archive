---
title: "[SOLVED] ZEW2500P hates Ubuntu"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by jabagawee on 2008-01-17
It seems that everytime someone posts a new thread about the ZEW2500P, people ignore it, or it dies a slow and painful death. I'll be subscribing this thread and will bump it continuously until we find a solution. Here's the specs of the machine, if it ever matters: E2140 @ 1.6GHz, 1 GB of RAM, X3100 Intel Graphics Media Accelerator. In physical order on the hard drive, I have XP on /dev/sda1 (5GB), Ubuntu 7.10 on /dev/sda4 (10GB), /home on /dev/sda2 (233 GB), and swap on /dev/sda3 (2GB). On my other hard drive, I have /dev/sdb1 (400 GB) mounted at /stuff. Network card: a USB dongle known as the Zonet ZEW2500P. God knows if it's rt2570 or rt73; there seems to be some confusion about that. I just want sweet, sweet wireless fidelity (aka. wifi) to work on this contraption. I don't care about free drivers. I don't care about the Restricted Drivers Manager. I don't care about ndiswrapper. I'm not afraid of the command line. I'm willing to try anything. I've already reinstalled Ubuntu countless times, so don't worry about messing up; we'll just do it again.

The problem is as follows: The Zonet ZEW2500P contains a Ralink chipset, most likely a RT73 chipset. Ralink is known to be a supporter of Linux. When booting from the Live CD, users are greeted by a list of wireless networks available through Network Manager. However, after a while, network connectivity is lost and cannot be regained without a reboot into the Live CD environment. After install of Gutsy Gibbon, the hard disk environment will not have wireless access through Network Manager. Zonet and Ralink both lack the .inf files in their drivers to make ndiswrapper work. There is no definitive guide to getting this to work. Any suggestions?

---

### Post by Hightide on 2008-01-18
Kevdogs  tutorial may help as a starter.

[http://ubuntuforums.org/showthread.php?t=571188&highlight=kevdog](http://ubuntuforums.org/showthread.php?t=571188&highlight=kevdog)


:)

---

### Post by jabagawee on 2008-01-18
Thanks for the hint, already saw that thread though. I'm going to try the thread at [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236) for RT73. Wish me luck!

---

### Post by jabagawee on 2008-01-19
And whaddya know? Turns out the ZEW2500P is RT73 based. I'm now happily typing wirelessly and downloading kubuntu-desktop whilst I'm at it.

---

### Post by #Reistlehr- on 2008-03-01
did you get it to work without using ndiswrapper?

---

### Post by jabagawee on 2008-03-01
not once did i touch ndiswrapper. i used only the tutorial i linked to.

---


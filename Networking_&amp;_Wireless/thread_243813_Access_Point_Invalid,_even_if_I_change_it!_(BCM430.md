---
title: "Access Point: Invalid, even if I change it! (BCM4306)"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by AzraelUK on 2006-08-25
Hi,
I'm having troubled with my BCM4306 wireless card. I've tried bcm43xx and ndiswrapper, can't get either to work:

BCM43xx seems to be working better. But, on iwconfig, it says [FONT="Courier New"]Access Point: Invalid[/FONT]. so, I type [FONT="Courier New"]sudo iwconfig eth0 ap any[/FONT], but it still says Invalid. I also tried setting it to the HWAddr as specified by ifconfig, (I think that's what you're suppposed to do), but it still won't change from Invalid.

PS. I'm using the bcm43xx-drivers, or whatever it's called, bcm43xx-fwcutter 004 says something about the md5sum of wl-apsta.o being incorrect, I dowwnloaded wl_apsta.o from the link on the ubuntu help page (drinus.net?)

NDISwrapper seems to fail at the first hurdle. I have the module, and ndiswrapper-utils with the driver from my driver CD. I've modprobe'd ndiswrapper, rmmod'd bcm43xx, and it doesn't show up in iwconfig.

This is a fresh install of ubuntu, not an upgrade.

---

### Post by AzraelUK on 2006-08-25
I've found a wl_apsta.o on a Broadcom Wireless cards howto on the forums, I'll try that now.

---

### Post by AzraelUK on 2006-08-26
[COLOR="White"]bump![/COLOR]

---


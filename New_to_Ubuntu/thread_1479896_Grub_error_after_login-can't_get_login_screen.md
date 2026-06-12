---
title: "Grub error after login-can't get login screen"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by belochkka on 2010-05-11
Okay, so after *successfully* installing the GMA500 driver on my eeePC1101HA (with the regular version of LL) I've come up with another problem:
I used synaptic with default settings to update all relevant packages. During installation, I was asked (in a GUI window) something along the lines of 
Update-Configure GRUB 
I pressed "Forward", but nothing happened for 2+ hours. (The only way to get past this was to select the checkbox of NOT configuring GRUB, and having the rest of the stuff get installed). After reboot, the OS "choosing" menu loads, and I can select either the default 
Ubuntu Linux 2.6.32-22 or Ubuntu Linux 2.6.32-21. The first (default) will start loading (I get the Ubuntu logo, with the driver for the GMA loading properly), but then the screen goes blank, after flashing me (twice, ~0.5s) a 
> ***something***
login:
message (can't read the first phrase, as it flashes by too fast):confused:

Loading the Ubuntu Linux 2.6.32-21 is OK, and everything seems to work, but I would very much like to fix the upgraded install (or to delete it from being default), and *most of all* to figure out what I did wrong so as not to make the same mistake in the future.

Thank you in advance!

---

### Post by cap10Ibraim on 2010-05-11
-You can uninstall a kernel from synaptic package manager 
-I use startup-manager from the software center to choose the default os and the waiting time 
-but I can't help you with the main issue (why this happened?)

---

### Post by belochkka on 2010-05-11
> -but I can't help you with the main issue (why this happened?)
And the thing is - I've managed to have this happen - twice. Last night I decided that this occurred because I somehow improperly installed the poulsbo driver, and *just* reinstalled the system. However, I managed to do this again today, and judging by screen resolution/etc the driver is working perfectly!

> -You can uninstall a kernel from synaptic package manager
Should I uninstall just the one file or several (I have some idea of what I'm doing, but not much - hence I'd much rather ask than just delete files I think I should):

I have the following files:
**linux-generic ** (Installed version 2.6.32.22.23)
**linux-headers-2.6.32-22** (version ~.33)
**linux-headers-2.6.32-22-generic** (ver ~.33)
**linux headers-generic** (version l2.6.32.22.2)
**linux-image-2.6.32-21-generic** (Installed version ~.32)
**linux-image-2.6.32-22-generic** (Installed version ~.33)
**linux-image-generic **(Installed version 2.6.32.22.23)
**linux-libc-dev **(Installed version 2.6.32-22.33)

Which should stay and which should go?

And, if this is in any way relevant, I have the following versions/packages "containing" the word grub installed:
grub-common (installed version 1.98-1ubuntu6)
grub-pc (1.98-1ubuntu6)
memtest86+ (4.00-2ubuntu3)
*which might help answer WHY this happened!*

Note on system setup:
I'm running a dual-boot with Ubuntu under Wubi (but I haven't loaded Winndows in days, so I doubt it's screwing with the installation)
I have an eeePC 1101 HA, with the GMA graphics driver that guys on this forum came up with 2 days ago (but it isn't the problem, because it a) works b) is ok even on the old kernel configuration)

---


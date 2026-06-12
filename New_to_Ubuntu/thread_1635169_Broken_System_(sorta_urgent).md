---
title: "Broken System (sorta urgent)"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by duegogo on 2010-12-01
I installed a PPA for Nvidia, upgraded, and then when I rebooted, the thing just hangs on the loading screen.  To fix it, I tried to go into failsafe graphic mode from my rescue bootup, and from there I ppa-purged the PPA in question.  This did nothing, and so I did some research and removed xserver-xorg as well.

After this, the screen just turns black when I bootup normally, instead of hanging on the loading screen.  So then a "friend" of my after this told me to remove X as well, in order to make it boot in the default graphics system for my main bootup, so that I can reinstall the graphic drivers that came with 10.10.

But after I removed X, and I boot normally, I just end up at a command-line.  When I try to boot from the failsafe graphic mode, now it cannot produce a GUI and instead says:  "Fatal server error: no screens found"

---

### Post by Linux_junkie on 2010-12-01
If you haven't got any documents / files in your home directory (folder) then if I were you I'd re-install from the CD from scratch, otherwise you are going to need to install the Xserver from the CD.

---

### Post by duegogo on 2010-12-01
Hmm, but the problem is I don't quite know how to install Xserver from the CD.  And if I go to my main bootup and do "sudo apt-get install xserver-xorg," it tells me that it is already at its newest version.

So reinstalling from scratch: is there any way to back up my files to an external via the command line, and then doing it from scratch?

---

### Post by Linux_junkie on 2010-12-01
You can use the cp (copy) command or mv (move) command

---

### Post by coffeecat on 2010-12-01
There's one thing that you can try but I can't guarantee it will work. You need to have an ethernet connection because it involves booting into the recovery console and you will need internet connectivity.

Choose recovery mode from the grub menu, and then when you get the secondary menu choose 'drop to root shell with networking'. When you get the '#' prompt you have full root powers, so take care not to make any typos.

The idea is to reinstall the meta-package 'ubuntu-desktop' which has as primary or secondary dependencies the whole of the Ubuntu gnome desktop and all the packages needed for the xserver. Hopefully, that will reinstall the bits of the xserver you've taken out. At the command prompt, try:

```
apt-get --reinstall install ubuntu-desktop
```If that does no more than reinstall the package ubuntu-desktop, try:

```
apt-get --fix-broken install ubuntu-desktop
```Then:

```
reboot
```... to reboot and see if the system boots into a GUI.

---


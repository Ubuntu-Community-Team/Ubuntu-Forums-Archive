---
title: "Safe to remove old kernels?"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by cat2005 on 2009-09-03
According to synaptic I have several kernels: 

linux-image-2.6.28-11-generic
linux-image-2.6.28-14-generic
linux-image-2.6.28-15-generic

I also have their respective headers.

Since "15" is presumably the most recent, is it safe to uninstall both "11" and "14" as well as their respective headers?

---

### Post by k33bz on 2009-09-03
Yes it is pretty much safe to get rid of the older kernals. However for troubleshooting reasons, I always keep the most current one and the kernal before that one.

---

### Post by drs305 on 2009-09-03
Yes, although you should probably keep a 'backup' that you know works.

You can remove them via Synaptic, which automatically removes them from the grub menu.
You can hide them from the grub menu by editing the menu.lst file manually or allowing StartUp-Manager to edit the file for you. SUM is a great GUI utility that tweaks lots of grub menu settings.

Here is a guide for using SUM, as well as how to manually edit menu.lst and how to remove the kernels if you prefer.

[HOWTO: Grub Menu Kernel Display Options ]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by bumanie on 2009-09-03
It is safe to get rid of old kernels, however it is good practice to keep one older kernel that you know works, just in case an update to the present kernel provides some sort of incompatibility to your system. Having an old kernel will allow you to boot, by choosing it in the grub menu.

---

### Post by Geoff918 on 2009-09-03
I usually just edit out the GRUB menu entries and forget about it. When I installed 9.10 it removed all the kernels previous (up to and including -15). So maybe the new version out at the end of October will do some clean-up for you anyway, if you're patient?

---


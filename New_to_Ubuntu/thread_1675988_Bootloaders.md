---
title: "Bootloaders"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by catquarks on 2011-01-26
Hi! This is my first post, although I have often solved many of my Ubuntu problems by reading this forum...

I just have a question about boot loaders: A few weeks ago I got myself a new netbook that already had Windows 7, so I partitioned the hard drive so I could have Ubuntu 10.04 on the other half (not the netbook flavor). Whenever I boot up, there are always two identical options for loading Windows 7 and two options for loading Ubuntu (not counting the "safe modes").

Everything functions just fine, but does anyone know why there would be two options for each OS, instead of just one each?

---

### Post by JRV on 2011-01-26
That is strange.

Run "sudo update-grub" to see what happens.

---

### Post by oldfred on 2011-01-26
Windows often has a vendor recovery partition that is an image of your drive that you should write to a DVD and/or recreates your drive as purchased - deleting all updates and data since you bought it. Usually it was a Vista recovery even with XP or Vista. Perhaps with win7 it cannot tell the recovery from the main install.

With Ubuntu you get new entries with every kernel installed. You should keep one old that you know works just in case.

Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
HOWTO: Remove Older Kernels via GUI Tweak
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

There is a newer tool to configure grub also:
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---


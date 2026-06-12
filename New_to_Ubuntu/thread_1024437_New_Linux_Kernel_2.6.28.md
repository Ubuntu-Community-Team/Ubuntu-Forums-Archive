---
title: "New Linux Kernel 2.6.28"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by Cryptopolka on 2008-12-29
How long does it normally take for a new kernel to become part of the 
repository? The new Linux kernel is out and I can't help but be excited, especially because of ext4 support and GEM. :D

---

### Post by IanW on 2008-12-29
It _may_ get backported to 8.10 Intrepid, but most likely we'll have to wait until 9.04 Jaunty (late April).

---

### Post by igknighted on 2008-12-29
It won't be in Ubuntu 8.10.  You can build it yourself if you like, but to install Ubuntu on ext4 you will need the jaunty installer.  Ditto with GEM, it needs DRI2 and the latest intel drivers, neither of which are in Ubuntu.  These can be built, of course.

If you want it sooner, you might be able to get it from Sidux/Sid.  However with Debian in freeze in anticipation of Lenny, that might not even work.  Fedora will release 2.6.28 for Fedora 10 at some point, but I don't think they have new enough stuff for GEM.  Ext4 is supported (even in the 2.6.27 kernel they shipped with... they backported the code) already, though.

If you really want to play with this stuff, bring in the jaunty packages.  I can't in good faith help you with this in Beginner Talk, but if you want to try this, start a thread about it in General or somewhere else and PM me the link and I would be happy to help.

---

### Post by cariboo on 2008-12-29
The latest Ubuntu kernel version is kernel 2.6.28-4-generic, which is available in the Jaunty repositories, but as far as I know ext4 is supported, but I'm not sure about GEM. The big problem with ext4 is that it is not supported in grub, so you have to install grub2 to be able to boot from an ext4 partition, and so far grub2 is  far from being usable for a normal user.

Jim

---


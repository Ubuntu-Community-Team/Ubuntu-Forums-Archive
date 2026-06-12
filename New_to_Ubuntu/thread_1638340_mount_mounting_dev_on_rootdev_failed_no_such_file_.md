---
title: "mount: mounting /dev on /root/dev failed: no such file or directory"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by naomibrown on 2010-12-05
We had no problems with Lucid Lynx since installing it on a desktop machine and didn't install or change anything yesterday, however this morning we got the following error messages when we chose the installation from GRUB. I've tried all the different options, including the recovery version, but I get the same error message each time.

...
killed
mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1unbuntu5) built-in shell (ash)
enter 'help' for a list of built-in commands

(initramfs) [2.224166] firewire_core: created device fw0:GUID 00e01800009cb982, S400

I've tried rebooting several times. Windows is working as well as usual. We're now trying to reinstall ubuntu using a live disk, but this is failing at the "Preparing to install Ubuntu" screen.

Any ideas? Thanks :)

---

### Post by naomibrown on 2010-12-05
I've just read some of the other posts and tried doing the boot info script from here:

[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

It's stopped at "Searching sdb1 for information ..."

---


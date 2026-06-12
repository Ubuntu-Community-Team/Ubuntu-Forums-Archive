---
title: "how do you edit the kernel configuration file in ubuntu 10.04?"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by al.adab on 2010-05-06
I tried *sudo gedit /boot/grub/menu.lst* but the file is empty...

Might need to compile the file according to [http://manpages.ubuntu.com/manpages/...4freebsd.html](http://manpages.ubuntu.com/manpages/...4freebsd.html) (as long as it's safe?). 

This is related to a message that appears at start-up, something along the lines of "mmc0 unknown controller version - you may experience problems" (Ubuntu 10.04 on a Dell Vostro 1310)

I've already tried to edit edit */etc/modprobe.d/blacklist.conf*
and insert the following

[I]blacklist sdhci-pci
blacklist sdhci
blacklist mmc_core[/I]

and the message is gone, but I don't really know what the implications of this are - ie, I haven't checked that everything works after doing this. I think some people reported their SD was affected.

---

### Post by muteXe on 2010-05-06
menu.lst is no longer used.
10.04 uses grub2

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by philinux on 2010-05-06
Also see [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---


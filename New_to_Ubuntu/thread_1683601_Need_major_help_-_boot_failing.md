---
title: "Need major help - boot failing"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by bobmac on 2011-02-07
Folks,

I have a dual  boot system 

I updated all the latest updates. On completion, after the intall process I was asked to reboot.

During the reboot (fairly early) my system stopped with the following:

mount: mounting /dev/disk/by-uuid/e4a29af8-44fa-4cde-9495-f602bc537be3 on /root
failed: invalid argument
mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init
No init found. Try passing init=bootarg

Bysybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)

I have no idea what this means, what went wrong or how to fix it.

Please help

Regards,

Bob

---

### Post by drs305 on 2011-02-07
If this is a normal installation, please download and run the boot info script from the following site:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")
Run the script and post the contents of the RESULTS.txt the script generates.

From the LiveCD, you could also run a check of the filesystem. Make sure the / partition is not mounted when you run the following command. Change XY to the appropriate values (such as sda1, sda5, etc).

```
sudo e2fsck -pfv /dev/sdXY
```

If this is a Wubi installation (within Windows) please take a look at *Rubi1200's* [Wubi Megathread]("http://ubuntuforums.org/showthread.php?t=1639198")

---

### Post by bcbc on 2011-02-08
I saw a problem like this recently. After a kernel update the initial ram disk wasn't created properly. If you have an older kernel, try booting into that. If that works okay, then you can try rebuilding initd.img for the latest kernel.

---


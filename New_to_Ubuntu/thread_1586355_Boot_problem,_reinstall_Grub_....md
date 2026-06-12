---
title: "Boot problem, reinstall Grub ..."
date: 2010-10-01
forum: New to Ubuntu
---

### Post by cwmoser on 2010-10-01
I cloned my main HD and it would not boot the partition with Ubuntu 10.04.  Looks like Grub on my PC was on another HD.  I found the easies way to reconfigure Grub and reinstall it was to use the Recovery Mode in the Ubuntu Studio 10.04 CD.  It worked like a snap.

But, I was wondering how do you reinstall and reconfigure Grub2 from the command prompt?

Carl

---

### Post by andrewthomas on 2010-10-01
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by drs305 on 2010-10-01
If you are running from a normal boot, you can install it with *:

To the current installation from that installation:
```
sudo grub-install /dev/sd**X**
```

If you want it on another partition, from the current installation or LiveCD:
```
sudo mount /dev/sd**XY** /mnt/mountpoint
sudo grub-install --root-directory=/mnt/mountpoint /dev/sd**X**

```

If it doesn't work, use the "--reinstall" switch:
Example: sudo grub-install --reinstall /dev/sda

If you need or want to completely remove and reinstall Grub2, use the procedures in this link from the LiveCD:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD ]("http://ubuntuforums.org/showthread.php?t=1581099")

From within the installation or from a chroot'd LiveCD, run "sudo update-grub" after making any changes to incorporate them into the Grub2 configuration script (/boot/grub/grub.cfg).

You can also reset the boot partition and linux kernel options by running this command from within the installation:
```
sudo dpkg-reconfigure grub-pc
```

* sd**XY** - sda1, sda5, sdb3, etc
  sd**X** - sda, sdb, etc

---


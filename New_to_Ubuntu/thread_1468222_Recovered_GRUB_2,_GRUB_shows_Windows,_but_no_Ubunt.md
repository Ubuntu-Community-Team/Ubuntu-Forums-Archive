---
title: "Recovered GRUB 2, GRUB shows Windows, but no Ubuntu"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by UnknownFear on 2010-05-01
I followed a tutorial that walked me through with recovering GRUB and listing Windows 7 in the GRUB menu. However, after I did everything, it lists Windows, but no Ubuntu.

**NOTE: /sda1 is Ubuntu, /sda2 is Windows 7!!!**

Here is what fdisk outputs:
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007964b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       17560   141049676   83  Linux
/dev/sda2   *       17561       37843   162923197+   7  HPFS/NTFS
/dev/sda3           37844       38914     8589313    5  Extended
/dev/sda5           37844       38914     8589312   82  Linux swap

```

Here is what I followed:

*UbuntuWiki - Recover GRUB 2 using LiveCD*
```

Recover Grub 2 via LiveCD

    *

      First, grab a copy of the latest Ubuntu LiveCD and boot it.
    * Open a terminal and type 

$ sudo fdisk -l

    * Now, you need to remember which device listed is your linux distribution, for reference, /dev/sda1 will be used. Now we need to mount the filesystem to /mnt 

$ sudo mount /dev/sda1 /mnt

    * If you have /boot on a separate partition, that need's to be mounted aswell. For reference, /dev/sda2 will be used. 

$ sudo mount /dev/sda2 /mnt/boot Make sure you don't mix these up, pay attention to the output of FDISK

    * Now mount the rest of your devices and some other things needed in the chroot 

$ sudo mount --bind /dev /mnt/dev
$ sudo mount --bind /proc /mnt/proc
$ sudo mount --bind /sys /mnt/sys

    * Now chroot into your system 

$ sudo chroot /mnt

You should be chroot'd into your system as root, you can now run commands as root, without the need for sudo.

    *

      Now you need to edit the /etc/default/grub file to fit your system 

$ nano /etc/default/grub

    *

      When that is done you need to run update-grub to create the configuration file. 

$ update-grub

    *

      To install GRUB 2 to the MBR, next you need to run grub-install /dev/sda 

$ grub-install /dev/sda

    *

      If you encounter any errors, try grub-install --recheck /dev/sda 

$ grub-install --recheck /dev/sda

    * Press Ctrl+D to exit out of the chroot.
    * Once you exit back to your regular console, undo all the mounting, first the /dev and others 

$ sudo umount /mnt/dev
$ sudo umount /mnt/sys
$ sudo umount /mnt/proc

    * Now you can unmount the root system. (But if you have a separate boot partition which you mounted earlier, you have to unmount this first, or you will get a "device busy" error message.) 

$ sudo umount /mnt

    * And you should be free to restart your system right into GRUB 2 and then into your system installation. 

If you had alternate OS entries, update-grub might say "Cannot find list of partitions!". Ignore it and continue - once you can boot into your linux installation, do so and then rerun update-grub and grub-install /dev/sda as root.
```

I'm thinking I might of unmounted Linux to appear in the boot menu by accident. Any help?

---

### Post by Sealbhach on 2010-05-01
Looks lke something went wrong with the os probe stage. 

Try reinstallling Grub using the Live CD with this simpler method:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

.

---

### Post by UnknownFear on 2010-05-01
> **Sealbhach said:**
> https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD[/url]

I followed the simpler guide and, after I rebooted the computer and went back into the LiveCD to update the grub, this is what I got from the terminal:

```

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

```

Any help with this? This is really frustrating! All I want to do is dual-boot Ubuntu 10.04 and Windows 7.

---

### Post by UnknownFear on 2010-05-01
I've decided to start all over but this time, I am installing Windows 7 first, than I will install Ubuntu 10.04 and hopefully this way will work perfectly.

---

### Post by ranch hand on 2010-05-01
The best thing to do is boot your live CD and run this script.  It will deposit a results text on the desktop of the Live Session.  Post it here.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---


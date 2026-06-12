---
title: "Error 17"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by uppidada on 2011-07-24
I've installed ubuntu and then re-started the system.
Then i could find grub and booted into windows for some work.
While i was working the power went off(UPS wasn't working).

When i tried to start system later ,error 17 comes and i could do anything.

I've booted from Live CD
the outputs of [COLOR="Red"]fdisk -l[/COLOR] is

[B]Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x305f305e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6629    53247411    7  HPFS/NTFS
/dev/sda2            6630       60801   435136590    f  W95 Ext'd (LBA)
/dev/sda5            6630       13003    51199123+   7  HPFS/NTFS
/dev/sda6           13004       22557    76742473+   7  HPFS/NTFS
/dev/sda7           22558       32755    81915403+   7  HPFS/NTFS
/dev/sda8           32756       42954    81923436    7  HPFS/NTFS
/dev/sda9           42955       55702   102398278+   7  HPFS/NTFS
/dev/sda10          55703       59828    33142063+  83  Linux
/dev/sda11          59829       60801     7815591   82  Linux swap / Solaris
[/B]



 "/boot/grub/menu.lst"   is  a blank file



what am i supposed to do?

---

### Post by Sef on 2011-07-24
What version of Ubuntu do you have?

---

### Post by oldfred on 2011-07-25
Did you attempt to reinstall grub and reinstall grub legacy not grub2?

Error 17 is only from grub legacy. And grub legacy uses menu.lst. But grub2 uses grub.cfg.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---


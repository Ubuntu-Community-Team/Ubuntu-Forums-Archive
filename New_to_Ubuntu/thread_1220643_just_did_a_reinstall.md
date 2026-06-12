---
title: "just did a reinstall"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by catroaring on 2009-07-23
ok, i have a 500GB drive partitioned in half XP on one and other nothing.  Another 1TB drive for media.  I just installed the latest ubuntu on what i thought was the other half of the 500GB drive.  It did not install where i wanted it to(other half of the 500GB drive).  So, how can i tell were it(ubuntu, which shows up in grub. and boots) is installed.  And delete(without disturbing xp).  

thanks

---

### Post by mapes12 on 2009-07-23
For working on partitions I run a GParted live CD

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

A simple GUI application.

However, I have no experience of working with a dual boot system so if you delete your Ubu partitions be careful not to mess up your windoze MBR otherwise your system will not start. May be someone else can help you out with this latter point.

---

### Post by x33a on 2009-07-23
first boot off a live ubuntu CD.

then, post the output of
```
sudo fdisk -l
```from a terminal.

this'll help us determine your ubuntu partition.

note: after deleting ubuntu, the bootloader will be removed too, so you'll have to restore windows' bootloader.

download and burn supergrubdisk for that, before doing anything else.

---

### Post by catroaring on 2009-07-23
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a431a42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30341   243714051    7  HPFS/NTFS
/dev/sda2           30342       60801   244669950    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x080fe07c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121275   974141406    7  HPFS/NTFS
/dev/sdb2          121276      121601     2618595    5  Extended
/dev/sdb5          121276      121579     2441848+  83  Linux
/dev/sdb6          121580      121601      176683+  82  Linux swap / Solaris

---

### Post by x33a on 2009-07-23
ok, so ubuntu is installed on your 2nd hard drive.

just open gparted from ubuntu live CD.

from the menu, click gparted -> devices -> sdb.

right-click on swap and delete it, then do the same for root (ubuntu partition).

after that delete the extended partition and format it to ntfs (for use with windows).

now reboot.

since grub is wiped out, you won't be able to boot into windows, either.

so, use the supergrubdisk to restore windows bootloader and now you can boot into windows with ubuntu and grub  deleted.

---

### Post by philcamlin on 2009-07-23
> **x33a said:**
> ok, so ubuntu is installed on your 2nd hard drive.

just open gparted from ubuntu live CD.

from the menu, click gparted -> devices -> sdb.

right-click on swap and delete it, then do the same for root (ubuntu partition).

after that delete the extended partition and format it to ntfs (for use with windows).

now reboot.

since grub is wiped out, you won't be able to boot into windows, either.

so, use the supergrubdisk to restore windows bootloader and now you can boot into windows with ubuntu and grub  deleted.

i was just going to say that :P

yes this is the right way to do it :popcorn:

---


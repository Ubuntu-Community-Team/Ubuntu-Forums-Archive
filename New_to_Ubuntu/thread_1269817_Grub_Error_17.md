---
title: "Grub Error 17"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by ocajublinky on 2009-09-18
reinstalled ubuntu after some hardrive cleaning and rearranging on my system and got Error 17

fdisk rvelaed [HTML]To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0bad253

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff0f2342

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       52957   425371644    7  HPFS/NTFS
/dev/sdb2           52958       91201   307194930    5  Extended
/dev/sdb5           52958       89752   295555806   83  Linux
/dev/sdb6           89753       91201    11639061   82  Linux swap / Solaris

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd6b52f45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       77825   625127424    7  HPFS/NTFS

Disk /dev/sdd: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         984     7897056+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(982, 254, 63) logical=(983, 36, 13)
ubuntu@ubuntu:~$ sudo fdisk/dev/hda
sudo: fdisk/dev/hda: command not found
ubuntu@ubuntu:~$ sudo fdisk/dev/hda
[/HTML]

where do I go from here? 64-bit Ubunut 9.04 btw, dual booting with Vista ulitmate 64-bit on a custom system.

---

### Post by Zoot7 on 2009-09-18
Try this:
```

sudo grub
find /boot/grub/stage1
```

it'll then return something along the lines of (hd1,4) etc.
```

root (hd1,4)
``` - whatever the last command returned
lastly
```
setup (hd0)
```
That'll re-install Grub to the MBR.

Failing that check out the Super Grub Disk:
**[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")**
I've never had to use it myself, but from what i gather it's a pretty handy tool for dealing with Grub problems.

---


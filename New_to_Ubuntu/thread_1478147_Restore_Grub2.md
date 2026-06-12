---
title: "Restore Grub2"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by steigerjb on 2010-05-09
I just installed Ubuntu on my portable hard drive. I think it created it's own grub menu, erasing the one on my regular hard drive. To get on my computer, I have to have the portable hard drive plugged in so I get a grub menu.

How do I restore sda2 or is it sda5? as the default grub?

```
sudo fdisk -l
```

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6254    50235223+   7  HPFS/NTFS
/dev/sda2            6255       19458   106054657    5  Extended
/dev/sda5            6255       18916   101699584   83  Linux
/dev/sda6           18916       19458     4354048   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b6649

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18706   150253568   83  Linux
/dev/sdb2           18706       19458     6034433    5  Extended
/dev/sdb5           18706       19458     6034432   82  Linux swap / Solaris
joe@joe-laptop:~$ 


---

### Post by Brandon Williams on 2010-05-09
If you can boot into the version of Ubuntu on /dev/sda5, do that, and then run:
```
sudo grub-install /dev/sda
```
This should revert the grub2 MBR installation to one that looks on /dev/sda5 for its stage 2 and config files.

If that's not enough for some reason, then read over the options [here](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202) for various methods to fix things when they've gotten seriously screwed up.

---

### Post by steigerjb on 2010-05-09
> **Brandon Williams said:**
> If you can boot into the version of Ubuntu on /dev/sda5, do that, and then run:
```
sudo grub-install /dev/sda
```
This should revert the grub2 MBR installation to one that looks on /dev/sda5 for its stage 2 and config files.

ok, it says:

> joe@joe-laptop:~$ sudo grub-install /dev/sda
Installation finished. No error reported.
joe@joe-laptop:~$ 


let's go check...

---

### Post by steigerjb on 2010-05-09
> **Brandon Williams said:**
> If you can boot into the version of Ubuntu on /dev/sda5, do that, and then run:
```
sudo grub-install /dev/sda
```


yep, it worked. Boy that was easy. For some reason when I used the live cd mounted sda5 and did sudo update grub it didn't work.

---


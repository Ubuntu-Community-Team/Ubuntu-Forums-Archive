---
title: "External drive seems to be the boot drive"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by bobmac on 2010-09-13
Folks,

I've got an external drive that I use for backups. However, when I disconnect it ubuntu doesn't seem to be able to find the boot stuff.

I'm running 10.04 LTS with all the latest updates. 

I've no idea on how to fix this problem.

Regards,

Bob

---

### Post by sandyd on 2010-09-13
> **bobmac said:**
> Folks,

I've got an external drive that I use for backups. However, when I disconnect it ubuntu doesn't seem to be able to find the boot stuff.

I'm running 10.04 LTS with all the latest updates. 

I've no idea on how to fix this problem.

Regards,

Bob
boot up ubuntu, and post the output of
```

sudo fdisk -l
```

---

### Post by bobmac on 2010-09-13
sandyd,

Here's the result

calban@ubuntu-desktop:~$ sudo fdisk -l
[sudo] password for calban: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69906990

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10200       19454    74340787+   7  HPFS/NTFS
/dev/sda3           20192       38913   150384403    5  Extended
/dev/sda5           38157       38913     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x339469aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       22558   181194168+   7  HPFS/NTFS
/dev/sdb2           22558       38914   131376129    5  Extended
/dev/sdb5           22558       38244   125997056   83  Linux
/dev/sdb6           38244       38914     5378048   82  Linux swap / Solaris
calban@ubuntu-desktop:~$

---

### Post by oldfred on 2010-09-13
If sdb is your external then when you disconnect it you do not have any linux partitions except for a swap partition on sda to boot.

---

### Post by bobmac on 2010-09-14
Oldfred,

While what you say is probably correct, my problem is how to fix it.

Regards,

Bob

---

### Post by amjjawad on 2010-09-14
> **bobmac said:**
> Oldfred,

While what you say is probably correct, my problem is how to fix it.

Regards,

Bob

If what oldfred wrote is true then you have two options:

A- Keep your External Drive plugged in

B- Or install Ubuntu again on your Internal HDD only. You can choose where to install (which drive) in Step 4 if I'm not wrong!

---

### Post by bobmac on 2010-09-14
amjjawad,

But how do I know that I'm installing it on my hard drive. Do I disconnect the external drive first or what?

Regards,

Bob

---

### Post by sandyd on 2010-09-14
> **bobmac said:**
> sandyd,

Here's the result

calban@ubuntu-desktop:~$ sudo fdisk -l
[sudo] password for calban: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69906990

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10200       19454    74340787+   7  HPFS/NTFS
/dev/sda3           20192       38913   150384403    5  Extended
/dev/sda5           38157       38913     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x339469aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       22558   181194168+   7  HPFS/NTFS
/dev/sdb2           22558       38914   131376129    5  Extended
**/dev/sdb5           22558       38244   125997056   83  Linux**
/dev/sdb6           38244       38914     5378048   82  Linux swap / Solaris
calban@ubuntu-desktop:~$

> **bobmac said:**
> amjjawad,

But how do I know that I'm installing it on my hard drive. Do I disconnect the external drive first or what?

Regards,

Bob
Yup. you disconnect the drive first.

---

### Post by bobmac on 2010-09-14
Sandy,

Many thanks for your info. So that I never make the same mistake again, have you any idea how this could have happened in the first place?

Regards,

Bob

---

### Post by oldfred on 2010-09-14
I never have had any trouble but you do have to be careful which drive you select to install and where you install grub with the advanced button. Did you partition in advance or use the automatic installer? I think it may not be as clear with the auto installer. If you have Vista or 7 besure to use the windows tools to resize the windows partition to make room for Ubuntu.

I prefer to partition in advance, make sure windows still boots & has run its chkdsk to see a smaller size and then use manual install to select & format the partitions.

---


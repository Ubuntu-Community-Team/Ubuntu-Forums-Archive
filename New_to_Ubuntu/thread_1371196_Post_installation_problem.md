---
title: "Post installation problem"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by peluchino on 2010-01-03
Hi,

I've got a Athlon 64-based PC which dual-boots between Win2k and WinXP. These installations are on partitions which use up about 50GB of my 120GB IDE drive. I've also got a 500GB SATA drive which has one large extended partition which I use just for backup purposes.

I did an installation of Ubuntu 9.10 from the CD, utilising the free space on the IDE drive. All seemed to go just fine until the very end: I rebooted expecting some sort of new boot menu to appear, but was greeted with the same Windows bootloader as before and so now I don't know how to access Ubuntu!

I re-ran the installation but with the same result. How do I get the boot menu to appear which presumably will give me the option of booting into Ubuntu or Windows?

Thanks for any help.

---

### Post by Methuselah on 2010-01-03
It sounds like the GRUB boot loader was either not installed or installed on the wrong drive.

Wish I could tell you how to correct that but maybe my bump will attract someone who knows.

I do know that at installation there should be an 'advanced' option to tell GRUB where to install itself.

---

### Post by peluchino on 2010-01-03
Hi Methuselah,

I was also thinking it probably put it on the wrong drive.

I remember trying out Suse Linux a long time ago and getting an option during installation asking if I wanted the bootloader on a floppy disk or hard drive, and was expecting something similar here.

---

### Post by WhiteHorse on 2010-01-03
Boot to the liveCD and tell us your partition table and drive layout. Just run GParted from the liveCD and it will list all your drives and partitions, write them down and let us know.

---

### Post by Methuselah on 2010-01-03
or 

```

sudo fdisk -l

```

Then you can just copy the output here.

---

### Post by peluchino on 2010-01-03
This is the output from fdisk:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d97083f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sda5               2       60801   488375968+   7  HPFS/NTFS

Disk /dev/sdb: 120.1 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24b0e5d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2640    21205768+   7  HPFS/NTFS
/dev/sdb2            2641       14596    96036570    5  Extended
/dev/sdb5            2641        5897    26161821    7  HPFS/NTFS
/dev/sdb6            5898        9173    26314438+   7  HPFS/NTFS
/dev/sdb7            9174       14368    41728806   83  Linux
/dev/sdb8           14369       14596     1831378+  82  Linux swap / Solaris

---

### Post by Methuselah on 2010-01-03
That would be helpful if I knew much about GRUB.
I'm hoping someone else will be able to use this info to assist you.

---

### Post by peluchino on 2010-01-03
OK thanks - hopefully someone here will know :-)

---

### Post by peluchino on 2010-01-03
<Bump> Does anyone have any ideas please?

---

### Post by peluchino on 2010-01-04
I managed to solve the problem by going into Advanced Options just before file copying starts. Although 'install bootloader' was already ticked and showed 'hd0', I re-selected the same hard drive and this time it worked!

---

### Post by Methuselah on 2010-01-04
> **peluchino said:**
> I managed to solve the problem by going into Advanced Options just before file copying starts. Although 'install bootloader' was already ticked and showed 'hd0', I re-selected the same hard drive and this time it worked!

Great, I knew of the option but wasn't sure which HD to tell you to select.
Glad you were able to get it sorted.

---


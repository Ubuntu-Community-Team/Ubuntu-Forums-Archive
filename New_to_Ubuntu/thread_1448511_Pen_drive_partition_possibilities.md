---
title: "Pen drive partition possibilities"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by nnjond on 2010-04-06
Hi,

I would like to partition a pen drive, so as i have my os on one p. and access to storage  on a 2nd p.from that os and, which i can also access that same storage from my desktop pc os. Is that possible? 

I hope I've made myself clear.

---

### Post by srs5694 on 2010-04-06
Yes. Partition it like a hard disk. One caveat: If by "desktop pc os" you mean Windows, be aware that Windows will only recognize the first partition on a USB flash drive. Thus, if you want to make some files accessible to Windows, be sure to make that partition (FAT or NTFS, of course) the first one on the disk.

---

### Post by Shpongle on 2010-04-06
yes it should be possible , you could try gparted on the live cd , or its in the repos, be careful when partitioning it will be something like /dev/sda or /dev/sdb

---

### Post by 2hot6ft2 on 2010-04-06
> **nnjond said:**
> Hi,

I would like to partition a pen drive, so as i have my os on one p. and access to storage  on a 2nd p.from that os and, which i can also access that same storage from my desktop pc os. Is that possible? 

I hope I've made myself clear.
Yes, it works fine on mine and the storage partition is NOT the first partition and windows can access it just fine.

---

### Post by srs5694 on 2010-04-06
> **2hot6ft2 said:**
> Yes, it works fine on mine and the storage partition is NOT the first partition and windows can access it just fine.

That's weird. What version of Windows are you using? Could you post the output of "sudo fdisk -l /dev/sdb" (or whatever your USB flash drive is)? I've done a moderate amount of testing on this, and I've never gotten Windows (mostly Vista) to recognize anything but the first partition on a USB flash drive. (Note that "first" in this context means "first used entry in the partition table", not necessarily /dev/sda1 and not the first in data location on the disk.)

---


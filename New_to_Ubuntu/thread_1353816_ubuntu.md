---
title: "ubuntu"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by Drenriza on 2009-12-13
Long ago i installed an version of ubuntu, on my computer along besides windows vista. The ubuntu version havnt been used for a while now.

But how can i remove the ubuntu desktop version WITHOUT removing/courupting anything on my vista operating system.

Regards
:KS

---

### Post by Troll_the_Great on 2009-12-13
> **Drenriza said:**
> Long ago i installed an version of ubuntu, on my computer along besides windows vista. The ubuntu version havnt been used for a while now.

But how can i remove the ubuntu desktop version WITHOUT removing/courupting anything on my vista operating system.

Regards
:KS

Hmm.... How did you installed Ubuntu? Inside windows, using WUBI, or on a separate partition?
Give us more info on the subject and we will try to help you.
Cheers!

PS: post the output of
```
df -h
```

---

### Post by Drenriza on 2009-12-13
The ubuntu (linux) version is installed on a driffent partition. Using the ubuntu live cd (downloaded and burned to a cd).

---

### Post by coffeecat on 2009-12-13
If you remove the Ubuntu partitions (there will be at least two, including a swap partition) before repairing the Windows MBR, you will make Vista unbootable, because stage 2 of the grub bootloader is in the Ubuntu root partition.

So, in order to repair the mbr you need to use either the Vista installation DVD and run fixmbr, or use [SuperGrubDisk]("http://www.supergrubdisk.org/").

If your Vista DVD is not a Microsoft one, then you will need to use SuperGrubDisk, which is quicker and easier anyway. Download the SGD ISO, burn it to a CD and boot with it. There are two Windows entries in the menu - one to boot into Windows and the other to fix the mbr and then to boot into Windows. Once you have run the repair and boot option, the mbr will be repaired and you will be able to boot directly into Vista without going through the grub menu, and without using the SGD disc. Now you can simply delete the Ubuntu partitions and reformat the freed space. You can use Vista's own disk management utility for this, or you can boot up with an Ubuntu live CD and use System > Administration > Gparted (Partition Editor).

---

### Post by Iowan on 2009-12-13
I haven't tried them...
[Here]("http://www.techspot.com/vb/topic135487.html") is one How-To I found (XP Wubi). 
[This]("http://computersight.com/operating-systems/ubuntu/ubuntu-how-to-remove-ubuntu-windows-vista/") one is for Vista.
[Another]("http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html") - to round things out.

---


---
title: "Have problem reinstalling Ubuntu"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by Cosmofan on 2010-06-02
Dear all, kindly asking for yr help as my own knowledge and experience are not enough to solve the problem. I'm using ThinkPad x61 tablet with XP professional, Ubuntu as a second OS. Decided or reinstalling from blank Ubuntu 10.4. While trying to remove GRUB first I was trying to boot from WinXP CD then pressed R for Recovery Console. But I got a message saying there was no hard disk in my system. Could anyone give a hint on what else I should try. Thanks in advance.

---

### Post by Gone fishing on 2010-06-02
If your reinstalling Ubuntu there is no need to remove grub. Just install and Ubuntu will re-write grub. Presumably in partitioning you may wish to format the old / partition.

Windows boot disk may not see the hard  drive if for example its an old Windows XP install CD as it may not be able to use SATA drives without using a floppy disk with the drivers at the beginning the install asks if you need to add custom SCSI drivers add the floppy then.

XP is old you may need a floppy drive.

---

### Post by Cosmofan on 2010-06-02
My hard drive is 120 g, 20 g for Ubuntu, but now I want a bit more. So, I'm about to delete ext3 partitions and add them to my ntfs. Then I started Partition Magic in XP and received an error (117 or smth), so I cannot work with my hard drive from there. That's why I decided to repair my MBR first (fixboot, fixmbr in Recovery Console, WinXP boot CD). It did not work because my hard drive was not detected.
Thanks for the idea about drivers - I will search further.

---

### Post by 3rdalbum on 2010-06-02
You can actually use the 'ms-sys' utility on Linux to create a new Master Boot Record. Unfortunately, ms-sys is no longer in the Ubuntu repositories, but if you don't mind installing build-essential on the live CD and compiling the program, you can use it to create your MBR without booting into Windows XP.

---

### Post by Cosmofan on 2010-06-02
> **3rdalbum said:**
> You can actually use the 'ms-sys' utility on Linux to create a new Master Boot Record. Unfortunately, ms-sys is no longer in the Ubuntu repositories, but if you don't mind installing build-essential on the live CD and compiling the program, you can use it to create your MBR without booting into Windows XP.

Is it safe enough to use this utility? as I would rather not harm my hidden WinXP partition.

---

### Post by Gone fishing on 2010-06-02
You can delete your Ubuntu partition resize your Windows partition add a home partition (recommended). There is still no need to remove grub when you reinstall Ubuntu it will rewrite grub into the MBR.

The only reason to remove grub would be if you install Ubuntu after XP and decided to remove Ubuntu and just have XP and what a strange  decision that would be.

---


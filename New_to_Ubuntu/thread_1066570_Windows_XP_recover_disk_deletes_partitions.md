---
title: "Windows XP recover disk deletes partitions?"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by Crasken on 2009-02-11
I know that this might not necessarily have much to do with ubuntu, but I want to be able to dual boot my computer from ubuntu and xp. When I use my XP recover disk, the only option is to delete my existing partitions (which I obviously don't want to do). Is there a way to use the XP recovery disk to install Windows in a separate partition from ubuntu?

---

### Post by gmagogsfm on 2009-02-11
> **Crasken said:**
> I know that this might not necessarily have much to do with ubuntu, but I want to be able to dual boot my computer from ubuntu and xp. When I use my XP recover disk, the only option is to delete my existing partitions (which I obviously don't want to do). Is there a way to use the XP recovery disk to install Windows in a separate partition from ubuntu?
 It may delete your existing partitions,which means your hard disk will be set back to default states

---

### Post by davidsrsb on 2009-02-11
Is it really deleting the partitions or is it just overwriting the MFT at the disk root? If so you can then recover grub using an ubuntu cd

---

### Post by Crasken on 2009-02-11
It only lets me download windows xp by deleting all of the partitions currently on the hard disk. I don't want to re-install ubuntu from windows xp and lose all of my themes + documents + games + other random stuff. Is there a way to use the windows xp recovery cd so that I can just install windows into its own partition?

---

### Post by kansasnoob on 2009-02-11
Have you used Gparted to create an unallocated partition for XP?

Look here:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

NOTE: Create a primary partition for Windows!

---

### Post by Crasken on 2009-02-11
I already have two partitions, my hard drive size is 160GB and I gave 60GB to ubuntu, leaving about 100GB for me to install and use Windows in. The problem is that the recovery cd ONLY gives the option of DELETING both my partitions. Please note that the recovery cd is different from the install cd. I'm sure that there's some way to use the recovery cd to install windows into it's own partition instead of deleting both partitions and then installing windows into the entire hard disk.

---

### Post by kansasnoob on 2009-02-11
> **Crasken said:**
> I already have two partitions, my hard drive size is 160GB and I gave 60GB to ubuntu, leaving about 100GB for me to install and use Windows in. The problem is that the recovery cd ONLY gives the option of DELETING both my partitions. Please note that the recovery cd is different from the install cd. I'm sure that there's some way to use the recovery cd to install windows into it's own partition instead of deleting both partitions and then installing windows into the entire hard disk.

But, the way XP is, it want's "unallocated" space! So you'll have to use Gparted to delete the excisting XP partition before reinstalling! Even if you've created a blank partition and designated it as NTFS the XP installer sees it as used!

The XP installer basically sees each each partition as a separate drive! Or you have a system specific disc that says NO!

---

### Post by Crasken on 2009-02-11
There is no existing windows xp partition, there's only an ubuntu partition and 100GB of blank, empty space. The recovery cd specifically says that it will delete all partitions on the drive, which is why I'm concerned.

---

### Post by davidsrsb on 2009-02-11
XP installation can get very confused by any drive bigger than 137GB

---


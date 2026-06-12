---
title: "Hard Drive Partitions"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by Ranavalona on 2010-09-12
I'm just a bit confused about partitioning on Hard Drives... if I have a Windows OS on one partition, and Ubuntu on another, are they able to access the same files(music, vids, etc.)?

---

### Post by abs_kkk on 2010-09-12
yes ubuntu can access windows files, if u mount the drive on which the files r thre.

edit: but windows cannot access the files in ubuntu partition.

---

### Post by fancypiper on 2010-09-12
In order for the Microsoft OS to access Linux files, you need to install something like [Explore2fs for Windows 7 - tool for accessing ext2 and ext3 filesystems ](http://www.windows7download.com/win7-explore2fs/vlvegefb.html).

---

### Post by coffeecat on 2010-09-12
If you have the current version of Ubuntu, then your Ubuntu root partition will probably be formatted ext4. As far as I know there is no Windows driver for ext4, although there is for the earlier ext2 and ext3 filesystems - the previous poster has linked you to one. 

Ubuntu can indeed access files on your Windows partition - simply go to the Places menu in Ubuntu. However, you can also write to the NTFS filesytem that Windows uses, which means you can write to the Windows C: partition. This is not a good idea. Vista and W7 can react badly to this.

One good solution for Windows/Ubuntu dual-boots is to create a separate partition, formatted with NTFS, for your data. This avoids the potential danger of writing to the C: partition. The data partition will be seen as drive E: or F: or whatever in Windows, and is easily mounted from the Places menu in Ubuntu. Or you can set things up to have the NTFS data partition mounted automatically on bootup.

One thing to be aware of. If the data NTFS partition filesystem needs repair, you need to use Windows chkdsk for this. There are Linux NTFS maintenance tools but they are not as comprehensive as chkdsk.

---

### Post by Ranavalona on 2010-09-12
Right, sorry, but I really don't want to mess up. Not sure how to say this with words, but I attempted at a diagram. So if I have one partition for all the Win7 OS files, one for the Ubuntu OS files, and another for everything else, would both OS' be able to work with the files in the "everything else" partition?

---

### Post by sandyd on 2010-09-12
> **Ranavalona said:**
> Right, sorry, but I really don't want to mess up. Not sure how to say this with words, but I attempted at a diagram. So if I have one partition for all the Win7 OS files, one for the Ubuntu OS files, and another for everything else, would both OS' be able to work with the files in the "everything else" partition?
yes.
as long as its formated as NTFS/FAT

---

### Post by garyed on 2010-09-12
Probably the easiest would be to format the "everything else" partition ntfs.

---

### Post by Ranavalona on 2010-09-12
> **garyed said:**
> Probably the easiest would be to format the "everything else" partition ntfs.
And both will be able to access it?

---

### Post by garyed on 2010-09-12
> **Ranavalona said:**
> And both will be able to access it?

yes

---

### Post by Ranavalona on 2010-09-12
Mm, cool. Thanks, man.

---


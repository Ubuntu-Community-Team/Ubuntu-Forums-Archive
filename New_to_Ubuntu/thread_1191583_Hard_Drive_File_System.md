---
title: "Hard Drive File System ?"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by KLF on 2009-06-19
Good day :D
 
I am a brand new (hope to be user of Ubuntu) and to start i would like to use Ubuntu as a dual boot with Windows XP Pro on my home built desktop PC, i intend installing Ubuntu to my second HDD first partition and my question is do i leave the partition as NTFS or do i need to format the partition to FAT32 ?, any answers appreciated.
 
K

---

### Post by indytim on 2009-06-19
Linux requires either ext3 or ext4 for the operating system.  The installer will take care of the format for you unless you opt to pre-configure the partitions before installation.

IndyTim

---

### Post by KLF on 2009-06-19
Thank you very much for your quick reply and help indytim, i will let the install take care of the format :D
 
K

---

### Post by tarps87 on 2009-06-19
> **indytim said:**
> Linux requires either ext3 or ext4 for the operating system.  The installer will take care of the format for you unless you opt to pre-configure the partitions before installation.

IndyTim

It can be configured to run on various formats including ntfs and fat but I would recommend using either ext3 or ext4 as stated above as it is designed to used these formats and you will get better performance. You will also need a partition formatted as swap. As this is your first install I would recommend using the auto partition option, just point it to the hard drive and set the amount of space you want to do, the rest will be done for you

---

### Post by KLF on 2009-06-19
Thank you tarps87, I will let the auto partition option do its work as you advise :D
 
K

---

### Post by The Cog on 2009-06-19
The auto-partition option is to "Use the largest available free space", if I remember rightly. This option requires that you have enough free (unpartitioned) space of course. It has the advantage of generally doing the right thing, and avoids the possible mistake of telling it the wrong name when installing over an existing partition, so should be safer for new users. It will also create a swap partition, which everyone who wants to pre-partition the drive seems to forget.

The disadvantage is that it ends up putting all the system and user data in the same partition so that reinstalling (should you ever want to) runs the risk of losing all your user data. But hey - just restore from yesterday's backup.

I believe there are un-resolved lockup issues with ext4, so if you do go for a custom partitioning scheme, I advise using ext3 for now.

---


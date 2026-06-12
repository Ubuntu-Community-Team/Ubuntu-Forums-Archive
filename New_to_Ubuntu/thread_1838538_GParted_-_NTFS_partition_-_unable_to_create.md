---
title: "GParted - NTFS partition - unable to create"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by avnd on 2011-09-03
Hello!

I have an old PC which has 2 80 GB hard disks. I wanted to partition it in such a way that it has 3 partitions.

1. NTFS - for Windows Xp
2. ext4 - for Lubuntu
3. NTFS - for Data (so it could be accessible to the rest of my family who still use Windows)

I tried partitioning both the hard drives with GParted from a Puppy Linux (Lucid) live CD. Whenever I create a NTFS partition, the program tries it and then produces some kind of error saying that the process failed. The error wasn't even descriptive (that's why I forgot to make note of the exact wording). But if I create a FAT32 partition in exactly the same place, it is created perfectly, but it wouldn't let me label the partition though.

The same thing happened in both the hard disks.

I referred in a few other websites. Two people suggested 'zero'ing my hard disks. I wiped my hard disks with 'Active Kill Disk' and 'WDClear' (both from Hiren's Boot CD). I tried creating the partition after wiping with 'Active Kill Disk' but it didn't work. So tried again with 'WDClear'. That didn't work either.

I'd love any suggestions.

Thanks.

---

### Post by tsucol11 on 2011-09-03
By 3 partitions over 2 drives are you talking about raid or having Lubuntu & XP on the same drive??

I installed XP Pro on the first HD and Ubuntu 10.04 on the second HD. XP pro was installed first, using the Windows XP CD to initially format the XP partition to 30 gigs. The remaining 50 gigs was partitioned & formated to NTFS using XP Pro disk manager (right click on My Computer / manage). I then installed Ubuntu 10.04 on the 2nd HD (including Grub2), using the Ubuntu CD.  The remaining 40 gigs was then formated to NTFS using Gparted.

In my case I installed Gparted to Ubuntu (HD) & then formated the second partition on the second HD.

I did note that while formating, using Gparted on a small drive, that NTFS would not work unless "round to cylinders was checked off. Everything then  worked OK.

I am not a big fan of having 2 bootable systems on the same HD. Preferring  to choose the booting HD from bios (Asus motherboard use "F8") 

Using the EXT4 file system on Ubuntu.

Brian 

> **avnd said:**
> Hello!

I have an old PC which has 2 80 GB hard disks. I wanted to partition it in such a way that it has 3 partitions.

1. NTFS - for Windows Xp
2. ext4 - for Lubuntu
3. NTFS - for Data (so it could be accessible to the rest of my family who still use Windows)

I tried partitioning both the hard drives with GParted from a Puppy Linux (Lucid) live CD. Whenever I create a NTFS partition, the program tries it and then produces some kind of error saying that the process failed. The error wasn't even descriptive (that's why I forgot to make note of the exact wording). But if I create a FAT32 partition in exactly the same place, it is created perfectly, but it wouldn't let me label the partition though.

The same thing happened in both the hard disks.

I referred in a few other websites. Two people suggested 'zero'ing my hard disks. I wiped my hard disks with 'Active Kill Disk' and 'WDClear' (both from Hiren's Boot CD). I tried creating the partition after wiping with 'Active Kill Disk' but it didn't work. So tried again with 'WDClear'. That didn't work either.

I'd love any suggestions.

Thanks.

---

### Post by Mark Phelps on 2011-09-04
What I would recommend is partitioning the two drives such that XP and the Data partition are on one drive, and Lubuntu is on the other drive.

To do this, have only the Lubuntu drive connected when you install Lubuntu.  Then, when done, reconnect the XP drive, boot into Lubuntu, open a terminal, and enter "sudo update-grub".  That will regenerate the boot menu and add an entry for XP.

After that, when you reboot, you will get a menu that will allow you to choose between XP and Lubuntu.

---


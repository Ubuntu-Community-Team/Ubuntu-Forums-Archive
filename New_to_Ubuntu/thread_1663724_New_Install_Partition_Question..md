---
title: "New Install Partition Question."
date: 2011-01-10
forum: New to Ubuntu
---

### Post by OldBoy44 on 2011-01-10
I am at present commencing a new install. I wish to get rid of Windows altogether.
I choose the manual partitioning option and was able to get rid of the NTFS file O.K. but I am unsure what to do about the first entry /Dev/sda
Could somebody kindly explain what I should do about this entry. I feel confident that I will be able to create the root, home and swap partitians. 

Thanks in advance,  :)

---

### Post by user1397 on 2011-01-10
> **aussiebean said:**
> I am at present commencing a new install. I wish to get rid of Windows altogether.
I choose the manual partitioning option and was able to get rid of the NTFS file O.K. but I am unsure what to do about the first entry /Dev/sda
Could somebody kindly explain what I should do about this entry. I feel confident that I will be able to create the root, home and swap partitians. 

Thanks in advance,  :)
This is what I always do.

On the ubuntu live CD, if you go to system > administration > gparted, you can view your hard disks and their partitions.  From there, you can edit, delete, or create new partitions.

Once you are done with gparted, you can start installing ubuntu, and once you get to the partitioning portion you say manually edit partitions, and then all you have to do is configure the mount points correctly.


I like gparted because I think it is visually easier to understand than the partition editor built-in the installer, although to give it credit it has improved vastly.

---

### Post by OldBoy44 on 2011-01-10
Does /Dev/sda stay where it is with Gparted?

I found out for myself about correct partitioning. 

  :)

---


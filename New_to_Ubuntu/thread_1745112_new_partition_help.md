---
title: "new partition help"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by natman on 2011-04-30
Hello,
I am planing on installing Kubuntu 11.04 on my laptop ( currently win 7 ). I want to have separate partitions for / and /home and a shared fat32 partition that both win and linux can read/write.

When i go to install using the manual option i get the partition table as follows:
sda 1 ntfs size(208 ) used (69)
sda 2 ntfs size(474389 ) used (51776)
sda 3 ntfs size(25399 ) used (21683)
sda 4 fat32 size(108 ) used (33)

Now i know the big partition is the main win one, and the rest are recovery partitions and other crap that was pre installed on the machine ( hp ). So how do i go about making a new table with / , /home and shared fat32 - i want to split up sda2. The options are "new partition table","add","change" and "delete".

thanks:

---

### Post by Ken UK on 2011-04-30
Becareful whatever you do and make sure you are fully backed up!

The idea is you create free space in the manual setup which you can then reassign as new partitions. If you know one of those partitions is ok to delete just select it and click delete then click add. You want to add a /home partition, a swap partition (abit bigger than your RAMM size), your FAT32 partition and your root partition (/) one after another using Add which should eventually fill all the free space up.

Im not an expert on Windows 7 so forgive me but doesnt it run across multiple partitions? Does it require it by default or is it optional? Just make sure you understand whats what first.

Good luck.

---

### Post by natman on 2011-04-30
Well i guess wat i need to do is resize the big partition but i just dont know how to go about doing that- and yes im fully backed up

---

### Post by Ken UK on 2011-04-30
Im not an expert on partitioning either to be honest lol
But will it not allow you to change the partition size by selecting it and selecting 'change'?

Im sure I was able to with Windows XP but not Vista. There isn’t a tool inside Windows 7 for doing that is there?

---

### Post by idoitprone on 2011-04-30
what partition able do you have? If you have mbr, you may have to delete a partition and put all of ubuntu on a logical partition

---

### Post by Quackers on 2011-04-30
As stated above, if you are on an mbr partitioned disc (which is likely if it's not on a Mac) you currently have the maximum of 4 primary partitions on your disc. If you try to create another partition Windows will change its partitions to "dynamic disks". That's BAD!!! if you want to install any other operating system.
In order to create more partitions you will need to delete one of your current primary partitions then in its place create an extended partition. This extended partition can hold as many logical partitions as you wish. Linux systems can boot from logical partitions, but, unless a separate boot Windows boot partition is present, Windows cannot boot from a logical partition.

In addition the Windows Disk Management Console can shrink or delete Windows type partitions.

---


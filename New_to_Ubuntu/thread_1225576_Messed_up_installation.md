---
title: "Messed up installation"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by linuxdummy on 2009-07-28
HI folks
 
Completely new to Linux, I saw Ubuntu in action recently on YouTube  so I decided to download it and burn it to disc (version 9)
 
All went well, I have Vista Premium, grub did the dual boot - but I had selected that the two operating systems operate side by side.
 
Now Vista has hogged most of the disk space and Ubuntu only has a couple of gb.
 
What do I do to expand the Ubuntu partition to something like 60gb?
 
I have 175gb for Vista, I know I can access the partitioner via the Live CD, but how do I adjust the partitions to allow Ubuntu to have 60gb.?
 
As far as I can see, the partitioner will only let me work on Vista's NFS file, and when I click on the linux swap file etc, delete is greyed out.
 
Your help would be appreciated.
 
Thanks

---

### Post by Terry of Astoria on 2009-07-28
You may have to reinstall, but try running gparted 
```
sudo gparted
```
from the live cd.
Use it to shrink your NTFS partition (you may want to defrag from Windows first)
Then maybe "grow" the Linux partition after there is room on the disk for it. In any case once you have shrunk the NTFS partition, then installing Ubuntu to the remaining free space will be easier. If you have to reinstall, you may want to remove your too-small linux partiton first, and start fresh.

---

### Post by Sef on 2009-07-28
> You may have to reinstall, but try running gparted 
 	Code:
 	sudo gparted 
from the live cd.
Use it to shrink your NTFS partition (you may want to defrag from Windows first)

1) It is best to use Vista's partitioner to shrink its partition.

2) If you use [gparted]("http://gparted.sourceforge.net/news.php"), then read [this faq #9]("http://gparted.sourceforge.net/faq.php") first.

---

### Post by yeats on 2009-07-28
> 1) It is best to use Vista's partitioner to shrink its partition.

I absolutely agree.  This is a very helpful link as well:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

---

### Post by linuxdummy on 2009-07-29
Argh - I wish I didn't experiment so much. Where is the Vista partitioner?
 
I loaded the live CD and got some unallocated space sorted, but what a mess I've left.
 
Take a look at this ...
 
FAT16 DellUtility     217.45 mib
 
NTFS Recovery      10.00 gib
 
Unallocated            4.06 mib
 
NTFS OS                161.6 gib
 
Unallocated           56.56 gib
 
dev/sda4 extended  2.49 gib
 
sda5 ext3                2.32 gib
 
sda6                      Linux Swap   172.54 mib
 
Now how can I get all the allocated space together, either delete the linux partitions or expand them?
 
Is it best to let Vista's partitioner work on this (as I said, where is it?)
 
Nice wee puzzle for you LOL
 
Thanks for your input so far guys.

---

### Post by linuxdummy on 2009-07-29
It's ok folks - got off my butt and looked at the help pages of Vista - found the partitioner, deleted the linux partitions, made a total of 61gig unallocated space, installed Ubuntu, and it's running perfectly.

From the previous attempt at partitioning, I know that Vista will now verify the partition when I select it from the GRUB menu.

'bye (for now)

---


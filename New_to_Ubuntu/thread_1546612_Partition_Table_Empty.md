---
title: "Partition Table Empty"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by Tweep Cat on 2010-08-05
I was going to install ubuntu, but when I came to  the installer there were no partitions. I run a quick command, and it showed all of the partitions. The screenshot attached should explain it. What do I do?

---

### Post by oldfred on 2010-08-05
Were you using the auto install. It may have trouble since you really only have sda4 available and may not see that swap already exists in your extended partition. It will want to create 2 partitions.

Try manual install or setting up root & /home if you want in advance and manual install. You can use sda4 and/or extend the extended partition left to add another partition or more.

---

### Post by cjack007 on 2010-08-06
if gparted fails to identify your partitions then it show it as unallocated space this usually happens if your partition table is corrupt or wrongly set up

what i see is that your /dev/sda2 starts at 15 and end at 18943
but your                /dev/sda3 starts at 38056 and end at 38914

so i think here lies your problem. you should check your entire disk for errors
better if you have a windows installation disk because it will identify your partitions even if they are corrupt and run a chkdsk on your entire disk.

hope  it helps!!!!!!!!!!!

---


---
title: "Question about partitioning"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by ghosticmp19 on 2011-02-22
So I'm currently running windows 7. I am trying to dual boot ubuntu. When I run the Ubuntu cd it gives me an easy install where it just wants to partition ubuntu to a partition I have already on my hd called SWAP thats only like 11 gb (I'm not really sure what SWAP means). When I go to the advanced partitioning option I have like 150 gbs of "free space" that I want to partition ubuntu on but when I click on it. It asks me a bunch of questions I don't know what to answer to.

1st() Type for the new partition: (primary,logical).

2nd() Location for the new partition(beginning, end)
-this one I would assume is beggining.
3rd() Use as: (Ext4Journaling file system,and a whole bunch of others)
---this is the one that I'm most confused. Which one does ubuntu need?
4th() Mountpoint- ???:confused:

Help please :)

---

### Post by deconstrained on 2011-02-22
Whatever you do you don't want to delete that Windows partition or repartition the drive, since your goal is dual-boot. If the Windows partition is taking up the full disk, then do not run the installer; fire up gparted first and non-destructively resize the Windows partition, so that you have room for a Linux partition. Then install Ubuntu on the free space.

---

### Post by ghosticmp19 on 2011-02-22
I used CHDSK in windows to downsize my windows partition. So Now I have 150 gbs of free space. Thats what I clicked on to make a new partition. My windows partition is sepearte and its 130 gb.

---

### Post by ghosticmp19 on 2011-02-22
Ive been reading the partition guides and I think I need to set the free space to a partition: primary, from the beginning,(Space allocated = the total free space), and I believe ext3 as the file system.""ext3," which is the Linux journaled file system (See the Extended Partition section below)" Is that correct?

---

### Post by lisati on 2011-02-22
> **ghosticmp19 said:**
> I used CHDSK in windows to downsize my windows partition.
Huh? I read that as CHKDSK, which doesn't resize disks..... :confused:

---

### Post by ghosticmp19 on 2011-02-22
Ok....it doesn't matter if you right click the partition in chdsk in windows there's a shrink option. Which really has nothing to do with my question thanks.

---

### Post by deconstrained on 2011-02-22
Yes, make a partition or two with the empty space, and install Ubuntu on it. Doesn't have to be extended, primary will do fine, provided you have 4 or fewer total primary partitions on the drive. When going through the install process, select the manual partitioning method and you'll get a dialog/interface for creating new partition(s) for Linux.

ext3 is old but reliable. ext4 has some advantages like faster checking & journal replay, and support of it is pretty mainstream. I think it would also be safe to just make the whole thing ext4, no need for a separate boot partition.

---

### Post by lisati on 2011-02-22
> **ghosticmp19 said:**
> Ok....it doesn't matter if you right click the partition in chdsk in windows there's a shrink option. Which really has nothing to do with my question thanks.

A Google search for CHDSK pulls up a lot of information about CHKDSK, which is used to check disks, not to shrink them. If by CHDSK you mean Windows Explorer, then I totally get the reference to the Shrink option, which doesn't exist in all versions of Windows.

---

### Post by ghosticmp19 on 2011-02-22
So I put the partition as a primary, ext4( I wikipedia this and apparently it's like an updated ext3...so I used this) I used the max amount of free space, and then for the mount point I had no idea so I used the first option which was "/" . Its installing now so I guess I did something right.

---

### Post by ghosticmp19 on 2011-02-22
Ok your right I used chdsk to fix a corruption after using disc management where I shrunk the partition. Which still has nothing to do with my question. Thanks Deconstrained you've given me allot of great info :).

---

### Post by deconstrained on 2011-02-22
Yeah, / is root, you're on your way. Good luck!

---

### Post by Quackers on 2011-02-22
I hope you only had 3 or less primary partitions originally (NOT 4)!
4 primarys plus another is bad news!
You shrunk your C: partition with disk management console, I suspect. This is the best way to shrink Windows partitions - if it will allow it.
Did you defragment the C: partition before shrinking it? Have you rebooted Windows twice since you shrunk it?

---

### Post by The Cog on 2011-02-22
You probably want to make two partitions: 
1: A partition for the system - mount point is / and filesystem is probably ext4. This can take most of your free space.
2: A swap partition for use as virtual memory, equivalent to the windows page file. Filetype is Linux Swap and mout point os swap. This should probably be maybe twice the size of your RAM.

These partitions can be either primary or logical (or one of each if you like), but remember that the PC can only have 4 primary partitions in total. If you need more than 4 partitions then one primary partition has to be type "extended" whch then acts as a container for all the logical partitions. So you shouldn't really use the last primary partition for anything other than an extended partition.

---


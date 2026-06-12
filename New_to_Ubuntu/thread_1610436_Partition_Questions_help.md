---
title: "Partition Questions help"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by hunter99507 on 2010-10-31
I would like to install ubuntu on a partition. Currently i have 4 primary partitions (Windows 7, Data Drive, and 2 Acer Recovery partitions)  I would like to know how to install ubuntu on a partition but i cant figure out how to create one. I read that you could create a logical partition and that would work but i dont know how to do that.  Also i would not like to format any of my current partitions, (i would like to keep windows 7, my data partition and 2 recovery partitions)  Anyone have any ideas?  Thanks

---

### Post by coffeecat on 2010-10-31
> **hunter99507 said:**
> Currently i have 4 primary partitions

And that is all you can have in a mbr partition table scheme - which is what Windows hard drives use. If you need more partitions, you need to remove one primary and substitute an extended. You do not use an extended partition directly; it is simply a "container" for (almost) as many logical partitions as you want. Fortunately, Linux can boot from a logical partition, unlike Windows (unless you do something clever).

But Windows is happy for a data 'D:' drive to be a logical, so perhaps the best thing is to backup your data from the data partition, delete it, create an extended in the space and then as many logicals as you need, one of which can become the D: (or whatever) NTFS partition. You can do all your partitioning with Gparted on the live Ubuntu CD.

More here:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

If you need any help, boot up with an Ubuntu live CD and post the terminal output of:

```
sudo fdisk -lu
```**Edit** Afterthought: you probably don't have two Acer recovery partitions. One is probably the special Windows 7 boot/recovery partition which is a Windows thing, not Acer.

---

### Post by MSPdwalt on 2010-10-31
Do you have any unallocated space? (disk space that hasn't been assigned  to a partition? If you do not  you'll need to use a utility like  [gparted]("http://gparted.sourceforge.net/download.php") to shrink/re-arrange some of your partitions. (liveCD)

Here is some [helpful info on hard drive partitioning]("http://en.wikipedia.org/wiki/Disk_partitioning"), it should help you get a better idea of what you should/want to do.

Once you have unallocated space you should be able to create the appropriate partitions for Ubuntu in the install wizard.

---

### Post by MSPdwalt on 2010-10-31
Also, if you're just looking to try Ubuntu you could always do a [wubi]("https://wiki.ubuntu.com/WubiGuide") install or vmware/virtualbox to create a VM.

A little simpler and less risky than messing around with all of those partitions.

---

### Post by lucifer1 on 2010-10-31
all what you have to do is defrag  the vista partition and then boot with your Ubuntu cd till you reach the level of choosing the partition choose the partition where the vista is installed and choose the ext3 size and make big like 30 gb if you can to not be in trouble later and leave the installation by default that mean install ubunt side by side with vista like this you will not lose any data and you will have ur ubuntu

---

### Post by coffeecat on 2010-10-31
> **lucifer1 said:**
> all what you have to do is defrag  the vista partition and then boot with your Ubuntu cd till you reach the level of choosing the partition choose the partition where the vista is installed and choose the ext3 size and make big like 30 gb if you can to not be in trouble later and leave the installation by default that mean install ubunt side by side with vista like this you will not lose any data and you will have ur ubuntu

@lucifer1, did you read any of this thread before you posted? The OP has four primary partitions and cannot do what you describe.

---


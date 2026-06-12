---
title: "how to delete the file system leaving an unformatted partition?"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by anon0 on 2009-01-27
Just want to strip the ext3 file system away.

---

### Post by bumanie on 2009-01-27
Boot an ubuntu live cd - when at desktop, open terminal> sudo apt-get install gparted Then go to System --> Administration --> Partition editor. When the GUI opens right click on the partition you want to clear and choose delete, the partition will then become unallocated. This can also be done with the gparted live cd if you prefer.

---

### Post by -kg- on 2009-01-28
> **bumanie said:**
> Boot an ubuntu live cd - when at desktop, open terminal Then go to System --> Administration --> Partition editor. When the GUI opens right click on the partition you want to clear and choose delete, the partition will then become unallocated. This can also be done with the gparted live cd if you prefer.

Why would you need to sudo apt-get gparted?  It's already on the Ubuntu Live CD by default.

Also, after you choose Delete from the menu, you need to click the "Apply" button for the change to actually be made.

Bumanie is also correct about the [GPartEd Live CD]("http://gparted.sourceforge.net/").  It would be worth downloading that tool whether you ever intend to come back to Linux or not.  It's a fine partition editor and it's free.

---

### Post by anon0 on 2009-01-28
is the live CD's gparted different from the non-live version? When I delete a partition in gparted the leftover partition is joined with free space nearby, changing the parititon size.

---

### Post by anon0 on 2009-01-28
alternative question: can you create a partition without a file system but with a precise size in bytes or sectors? Gparted can do the former but not the latter, while parted can do the latter but not the former, apparently.

---

### Post by -kg- on 2009-01-28
> **anon0 said:**
> is the live CD's gparted different from the non-live version? When I delete a partition in gparted the leftover partition is joined with free space nearby, changing the parititon size.

It shouldn't.  GPartEd does what you tell it to do.  You tell it to delete a partition, it deletes that partition and nothing else.  In place of the deleted partition you should have free unallocated space, unless you had the deleted partition inside of an Extended partition...then it would leave free, unallocated space inside the Extended Partition.  In order to expand the remaining partition, you would have to delete the Extended partition as well and it does not automatically combine two different operations; only what you set up.

At any rate, it should not expand the remaining partition into the free space unless you tell it to in a separate operation.

> **anon0 said:**
> alternative question: can you create a partition without a file system but with a precise size in bytes or sectors? Gparted can do the former but not the latter, while parted can do the latter but not the former, apparently.

Where are you using parted from?  If you think that's what runs from the Ubuntu Live CD, that's also GPartEd.  When you launch it, look at the top of the Partition Editor window...it says GPartEd.  I don't know why you would want to use parted.  Parted is a command line partitioner, while GPartEd uses the GTK+ Graphical frontend (the GUI).  From the [Parted User's Manual:]("http://gnu.huihoo.org/parted-1.6.1/html_mono/parted.html#SEC10")

> Parted has two modes: command line and interactive. Parted should always be started with:

# parted device

where device is the hard disk device to edit. (If you're lazy, Parted will attempt to guess which device you want.)

In command line mode, this is followed by one or more commands. For example:

# parted /dev/sda resize 1 52 104 mkfs 2 fat16

Options (like --help) can only be specified on the command line.

In interactive mode, commands are entered one at a time at a prompt, and modify the disk immediately. For example:

(parted) resize 1 52.0005 104.5
(parted) mkfs 2 fat16


You can do both with both, but GPartEd is a lot easier to use.

In order to create a new, unformatted partition of a specific size with GPartEd, either click on the free space (select it) on the graphics bar and click the "New" button at the top, or right-click on the line associated with the free space below the graphic bar and select new from the drop down menu.

You will be presented with the "Create New Partition" pop-up.  Click on the "Filesystem" button, scroll all the way to the bottom, and you will find "Unformatted," which you would select.

In order to set the exact size of the partition, you can either drag the partition to the desired size or manually type in the new size in the "New Size (MiB)" box, or alter either the "Free Space Preceding" or "Free Space Following" boxes, or both.

I don't understand your line of questions, though.  What exactly is it you're trying to do?  If you're using Vista and want to create another partition specific to the Vista ntfs, I would just delete the ext3 partition(s) and use Vista to create it's own.  Vista (or any other Windows version that uses ntfs) will recognize and use an ntfs partition created by GPartEd, and if you're using an earlier (FAT32) version, you can create one of those as well.

If you need further help with partitioning operations, please see:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by anon0 on 2009-01-30
Well, the context was for cloning a source partition for RAID1. Before creating an array, mdadm would give a warning message if a partition is formatted. Maybe this is safe to ignore, but I'm not sure so I'm asking how to prepare a unformatted partition. In GParted when I delete a partition, it becomes unallocated and mdadm can't see it anymore. GParted can't unformat an existing partition; there's no "format to unformatted" option. It can only create an unformatted partition. This leads to the next issue: for partition size Gparted uses MB in two decimal places, but for RAID I don't think that's good unless both partitions are exactly the same size down to the number of bytes. Parted can do this, but it can not create an unformatted partition.

---

### Post by -kg- on 2009-01-31
> **anon0 said:**
> Well, the context was for cloning a source partition for RAID1. Before creating an array, mdadm would give a warning message if a partition is formatted. Maybe this is safe to ignore, but I'm not sure so I'm asking how to prepare a unformatted partition. In GParted when I delete a partition, it becomes unallocated and mdadm can't see it anymore. GParted can't unformat an existing partition; there's no "format to unformatted" option. It can only create an unformatted partition. This leads to the next issue: for partition size Gparted uses MB in two decimal places, but for RAID I don't think that's good unless both partitions are exactly the same size down to the number of bytes. Parted can do this, but it can not create an unformatted partition.

I did a little research on the subject and found [this page]("http://www.ibm.com/developerworks/linux/library/l-raid2/index.html") on the subject.  You might want to check out the first article in this series, as it shows you step by step how to set up a RAID0 and RAID1 array.  From that article:

> you can shut down your machine, plug the drive in, boot up, wipe the drive, create a new RAID autodetect ("FD") partition to add the array (of the correct size, of course -- **at least as big as the partition it's replacing**) and then add this brand-new partition to the array.

What I put in bold type I would assume to mean that you don't have to match the partition byte per byte, as long as it is *at least* the same size (or bigger).

---

### Post by anon0 on 2009-02-04
> **-kg- said:**
> What I put in bold type I would assume to mean that you don't have to match the partition byte per byte, as long as it is *at least* the same size (or bigger).

Thanks for the reply. I have only seen the autodetect option in fstab, if I recall correctly. Not sure if that's related to being able to have different sized partition. However, I was unable to use unequal sized partitions when creating a RAID5 array:

```
root@ubuntu:/home/user# mdadm --create /dev/md2 --level=5 --raid-devices=4 /dev/sda1 /dev/sdd1 /dev/sdc3 /dev/sdb3
mdadm: /dev/sda1 is too small: 0K
mdadm: create aborted
```

This problem went away when equal sized partitions were used.

But then, one must be able to use larger partitions in order to expand or grow an array. Perhaps what I experienced was only a restriction when creating a new array but not growing it, or I missed something.

I also found that simply using the same number of bytes on a new drive could cause warnings (by programs such as sfdisk, when cloning) if the partition on the new drive does not end at a "cylinder boundary". A way of dealing with this is to turn on "round to the cylinders" in GParted. That in turn means having to use the same whole-number size in MiB in GParted for all partitions in the intended array.

---


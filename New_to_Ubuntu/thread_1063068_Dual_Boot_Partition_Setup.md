---
title: "Dual Boot Partition Setup"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2009-02-07
Ok here is where I am stumped:

partitioning remainder of drive for Linux

status:

loaded MS XP onto 50 gig SDA1 partition; leaving 200 gig free space
i want to use remainder of free space for Ubuntu...

Loaded Ubuntu 8.10 from CD and proceeded to partition setup under install program:

i selected "manual" as opposed to "guided" options and was next shown screen with /dev/SDA1 partition of 52 gig and 197 gig free space. i highlighted free space line and selected new partition...

 create a new partition 

Type for new partiton:       primary         or     logical (x)
New partiton size in megabytes:     197628
Location  "     "    :       beginning (x)   or     end
Use as:                      Ext3 journaling file system   ?
Mount point:                 ???

I do not know what correct answers are to these fields.
Help,

Ed

---

### Post by sleepyjon on 2009-02-07
It looks like you're just making 1 partition for ubuntu, so you want the mount point to be /

---

### Post by ozark_hillbilly on 2009-02-07
thanks for mount point info...
any other suggestions on primary versus logical and beginning versus end, if it actually matters ?

Ed

---

### Post by avtolle on 2009-02-07
You should also select ext3 as the file system. On the size, you should also have a swap partition, and I'd recommend you leave some room for it (mount point /swap); recommended size is 1.5 to 2x RAM, but IMHO, if you have 1gb or greater of RAM, the swap may be no larger than 1gb. 

On primary vs. logical, logical makes sense. You already have at least one primary partition used for the Windows partition; the extended partition under which the logical partition(s) are/will be created is another primary partition. IIRC, there is a 4 primary partition limit on a HDD with Windows installed. If you have a recovery partition for your Windows installation, with the extended (as noted above) you already have 3 primaries, so use of logical partitions under the extended partition gives you more flexibility (again from memory, a maximum of 15 logical partitions on an IDE drive {or was that SCSI; memory fails to serve} so you could also reserve some of the available space for a separate home partition, with mountpoint /home, helpful if you need to reinstall).

---

### Post by beatgr on 2009-02-07
> Loaded Ubuntu 8.10 from CD and proceeded to partition setup under install program:
IF this PC already has WinXp installed -- It is usually easier just to take the quick guided tour. Of course you should clean-up (de-frag) the WinXP installation first -- before adding any version of Linux.

beatgr

---

### Post by -kg- on 2009-02-07
What I, personally, would do is to create an Extended partition to enclose all the free space you have.  Linux will boot and run from an extended partition, and it will enable you to create any number of Logical partitions within (well, not ***any*** number, but enough that you're not likely to exceed the limit). Then create the partitions for Ubuntu within it.  I have to assume that, if you choose to create a Logical partition, it will either create or extend an existing Extended partition.

Of course, creating one partition for Ubuntu won't work, since you will need a swap partition as well.  So you can't use the entire space for your / (also known as root) partition.  You will need to create a swap partition.

The swap partition will need to be at least the same size as your RAM, and since you have some plenty of room, I would go ahead and make it twice the size.  Anyway:

> Type for new partiton: primary or logical (x)
New partiton size in megabytes: 197628
Location " " : beginning (x) or end
Use as: Ext3 journaling file system ?
Mount point: ???

1st, make a logical.  I have to assume that the extended partition will be automatically created, otherwise you would have first had to make a choice between Primary or Extended, the Extended in which you would create Logical partitions. (See the link, "How To Partition," below)

This is the reason I set my hard drive up before I started my installation.  As I remember, it got a little confusing, and as I have some years of experience at hard drive partition operations, it was easier for me to set it up, then set it up the rest of the way during installation, setting the mount points and all.

For the first partition I would create the swap partition.  As I said, around twice the amount of RAM installed in your computer should be more than a great size.  So if you have 2 GB of RAM, make the size around 4 GB.  You will want to put this partition at the end of free space, and "Use as" would be swap.

Now, it has been often suggested that you create a separate / (root) and /home partitions.  This is to make it easier to upgrade your installation without losing your files and settings.  You can do this if you want, or if you're not very knowledgeable on a computer and want the simplest method possible for your installation, you can create just a / (root) partition, and home will be created in it.  If you want to create the separate partitions, ask about it and we'll tell you.

If you choose to just have a root partition, you can go ahead and create a partition using the rest of free space.  In this case, I don't need to tell you the size, because it will be in the remaining free space.  I likely won't have to tell you beginning or end for the same reason.

In this case, yes, you want to use the ext3 journaling file system.  It is Linux native and the default file system type for an Ubuntu installation.  Mount point will be "/" (root).  Understand that when I put (root) after the forward slash, it means that when you see a forward slash, that is generally called the root partition.  If you already knew this, sorry...I sometimes deal with people who get confused and am used to explaining every little thing. :)

A good page to read about basic partitioning operations is:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

There are other places in the community documentation that will explain a lot of the concepts, and of course, if you have any other questions, everyone here will be more than happy to help.  Just ask!

---


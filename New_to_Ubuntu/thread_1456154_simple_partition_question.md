---
title: "simple partition question"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by c0nrad on 2010-04-16
Hey,

So awhile ago I installed ubuntu from tutorial, and since it was my first time, I sort of just did what it was saying without really thinking about it much. And now that I'm kind of curious what I did, I can't find it. :(

But anyways, I was wondering if anyone could explain in simple terms what the different partitions I have are used for and what they could possibly be used for.

```

conrad@conrad-laptop:/dev$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe239a202

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29164   234259798+  83  Linux
/dev/sda2           29165       30401     9936202+   5  Extended
/dev/sda5           29165       30401     9936171   82  Linux swap / Solaris

```Thanks,
C0nrad

---

### Post by ratcheer on 2010-04-16
You have put almost everything into a huge root partition, and all of the rest into an extended partition that contains only your swap space. So, all of your Linux files and directories are on the big partition (sda1). The swap space is just used by the system. All of your eggs are in one basket, so to speak. That is not really terrible, but not very flexible, either.

Tim

---

### Post by c0nrad on 2010-04-16
If I was to split it up, what sort of configuration would you recommend?

---

### Post by quadproc on 2010-04-16
> **c0nrad said:**
> Hey,
...
But anyways, I was wondering if anyone could explain in simple terms what the different partitions I have are used for and what they could possibly be used for.

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29164   234259798+  83  Linux
/dev/sda2           29165       30401     9936202+   5  Extended
/dev/sda5           29165       30401     9936171   82  Linux swap / Solaris

```Thanks,
C0nrad
Very briefly, you have a simple and straightforward file system set up on drive sda.  It is only possible to have a maximum of four partitions on a disk so the file system creates logical partitions in the file system to allow for more partitions.  Your first two physical partitions are numbers 1 and 2; number 3 and 4 are not presently in use.  Partition #5 contains your swap area and is on a logical partition.  This logical partition is consuming all of partition 2.

The operating system is on partition 1.  The fdisk report does not show where your other files are, but they have to be on the same partition because there is no other place for them.

The swap area on partition 5 is where the system stores things temporarily if the memory becomes full.  You might think of it as a bucket to hold overflow from the memory "tank".

All of your user files, your home directory and everything in it, any programs that you install, any temporary files, the system's log files, and basically anything else will all go into partition 1.

The swap area will only be used for swapping things in and out of memory, or if you hibernate the system then this area will be used to remember everything that was in memory at shutdown time.  Therefore the swap area needs to be at least as large as your RAM size.

If you want, you can change partition sizes later.  The process is somewhat risky and should not be undertaken lightly; you might lose everything on the disk and have to start over with a Live CD or a USB drive and restore all of your files and system setups from an external source such as a backup drive.

You could also add another drive of some sort to the system.  Many people move their /home/<username> directory to a partition on a different drive; this has the advantage that it is independent of the operating system's drive and is generally unaffected by a version upgrade.

quadproc

---

### Post by theozzlives on 2010-04-16
read this [http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/")

---

### Post by c0nrad on 2010-04-16
Sweet understand now. Thanks quadproc and ratcheer.

---

### Post by ratcheer on 2010-04-16
> **c0nrad said:**
> If I was to split it up, what sort of configuration would you recommend?

Every person you ask will probably tell you something different. :P

But, I like my swap partition to be primary and to be the first partition on the disk. This is said to be better for performance, but I don't really know. I have just always done it this way.

That leaves a maximum of three more primary partitions. With Ubuntu and most modern Linuxes, even the root partition can be in an extended partition. So, if you wanted, you could make the rest of the disk be an extended partition and create as many sub-partitions in it as you needed. And you would still have two possible primary partitions remaining for other OS's, or whatever.

From there, things can be as simple or as complicated as you want (or need). It is hard to get very specific with someone else's system. That said, many users like to put /home in its own partition. On business systems, I have seen things separated into root, home, var, usr, and opt filesystems, and that did not include the filesystems used for the majority of the data. Of course, some of these systems had hundreds of disk drives.

I hope this actually helps and is not too confusing. Like everything with systems, the design should depend on what you need to use it for, not vice versa.

Tim

---

### Post by theozzlives on 2010-04-16
If you can do it without losing data, do:
/ 10 GB primary
swap twice your RAM, logical
/home everything left, primary

---

### Post by c0nrad on 2010-04-16
Lol yeah.

I think I'll just stick with the way it is. It has been working perfectly fine so far. I think I'll try the separate home thing the next time I reinstall thought.

Thanks a lot for all the info,
c0nrad

---

### Post by c0nrad on 2010-04-16
> **theozzlives said:**
> If you can do it without losing data, do:
/ 10 GB primary
swap twice your RAM, logical
/home everything left, primary

If you only have 10gb in /, should I be installing your software somewhere else? At the moment I install in /usr/local/src/

c0nrad

---


---
title: "Can Someone Explain Partitions/Filesystems?"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by Penguin Guy on 2009-04-04
I opened GParted and have attached what I saw to this post.

**fat16 - /dev/sda1:**
This is possibly for restoring your computer in the case of an accident.
fat16 is a simple filesystem.
[B]
ntfs - dev/sda2:[/B]
This is my Windows partition.
ntfs is a filesystem.
The explanation mark is a warning of some kind.
[B]
extended - dev/sda3:[/B]
This contains all the Linux stuff
Hard to explain why it is needed. See [here]("https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics").
[B]
ext3 - dev/sda5:[/B]
ext3 is a type of filesystem.
Mountpoint is where the filesystem 'lives' - for example  '/home/user/music'
The key icon means that the partition is locked and cannot be edited (usually because it is in use)

*Thanks!*

---

### Post by Dr Mac 24 on 2009-04-04
See

[http://www.tldp.org/HOWTO/Partition/intro.html](http://www.tldp.org/HOWTO/Partition/intro.html)

or 

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

or search

---

### Post by lovinglinux on 2009-04-04
[http://en.wikipedia.org/wiki/Fat16](http://en.wikipedia.org/wiki/Fat16)
[http://en.wikipedia.org/wiki/Ntfs](http://en.wikipedia.org/wiki/Ntfs)
[http://en.wikipedia.org/wiki/Extended_partition](http://en.wikipedia.org/wiki/Extended_partition)
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)
[http://en.wikipedia.org/wiki/Swap_(computer_science](http://en.wikipedia.org/wiki/Swap_(computer_science))

If you are using Firefox, then you search bar already comes with a Wikipedia search engine, which is very useful to search for technical terms.

---

### Post by Penguin Guy on 2009-04-04
I know what partitions are, I just don't know about formatting/mountpoints/etc. Thanks for the links anyway.

---

### Post by Penguin Guy on 2009-04-04
> **lovinglinux said:**
> [http://en.wikipedia.org/wiki/Fat16](http://en.wikipedia.org/wiki/Fat16)
[http://en.wikipedia.org/wiki/Ntfs](http://en.wikipedia.org/wiki/Ntfs)
[http://en.wikipedia.org/wiki/Extended_partition](http://en.wikipedia.org/wiki/Extended_partition)
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)
[http://en.wikipedia.org/wiki/Swap_(computer_science](http://en.wikipedia.org/wiki/Swap_(computer_science))

If you are using Firefox, then you search bar already comes with a Wikipedia search engine, which is very useful to search for technical therms.
Thanks.

---

### Post by lovinglinux on 2009-04-04
> **Penguin Guy said:**
> 
**fat16 - /dev/sda1:**?

Is it for Windows? - yes
What is it used for? - probably windows swap, but I'm not sure because fat16 is kind of old and you have only 54Mb space there

> **Penguin Guy said:**
> 
[B]
ntfs - dev/sda2:[/B]

This is my Windows partition. - yes
What does the explanation mark icon mean? - I don't remember but I guess it is the boot partition.

> **Penguin Guy said:**
> 
[B]
ext3 - dev/sda5:[/B]

What is the mountpoint? - In Linux the directory structure is very different. You can mount any folder using different partitions. For example, you could use a spare hard drive or another empty partition to mount the home directory. Then the mountpoint will be /home. When you browse the directory structure with the file manager, home will be under /, but the data is stored on another partition. This is very useful to preserve your personal data after a re-install, because the /home partition will be preserved, if you do not format it but mount it again as /home. As another example, you could mount a spare hard drive to store all your videos. So the mountpoint will be /home/user/videos.

You can learn more about this at [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/5022-linux-directory-structure-overview.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/5022-linux-directory-structure-overview.html)

[http://en.wikipedia.org/wiki/Mount_(computing](http://en.wikipedia.org/wiki/Mount_(computing))

> In Unix-like systems, the mount point is the location in the operating system's directory structure where a mounted file system appears. For example, many modern Linux distributions automatically mount the CD drive as /media/cdrom, so the contents of the CD drive will appear in the /media/cdrom directory.

> **Penguin Guy said:**
> What happened to dev/sda4?

I think you didn't formatted it, so its unallocated. You need to format it and create a new mount point for it. Don't use an existing folder with data to do this. If you want to mount it as /home/user/videos then rename the video folder first to avoid loosing data.

---

### Post by Bölvaður on 2009-04-04
> **Penguin Guy said:**
> 
**fat16 - /dev/sda1:**
Is it for Windows? 
What is it used for?
What is fat16?

it is the most basic and kind of crappy file system. it's big brother fat32 is the most common file system for removable media like flash sticks. fat16 used to be common for small flash sticks though.
ms has patents over this format even though it is stupifyingly simple and trivial.

This partition was probably made before you bought it preinstalled. It may contain setup files or something for windows. If you dont have windows or you set up your computer user self, this partition is a waste of space.

> **Penguin Guy said:**
> 
** ntfs - dev/sda2:**
This is my Windows partition.
What is ntfs?
What does the explanation mark icon mean?

the current windows filesystem type.
the sign is an "ATTENTION" sign. might not be too important as this is ntfs.


> **Penguin Guy said:**
> 
** extended - dev/sda3:**
This contains all the Linux stuff
Hard to explain why it is needed. See [here]("https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics").
 
Normally you are only able to have 4 partitions, but you can make one partition (extended partition) contain more partitions. In turn this is used in automatic installations and when you have many partitions.
So you will be able to have more partitions.

 > **Penguin Guy said:**
> 
** ext3 - dev/sda5:**
What is ext3?
What is the mountpoint?
What does the key icon mean?
  
**/ **as a mount mount is root, that is the top level in a file system tree. Mount point is what part of the file system this partition is. Like I have partition mounted to /data
many have /home partition
**key icon means it is locket (**probably because it is mounted)


  > **Penguin Guy said:**
> 
What happened to dev/sda4?
   
a user (a program) must have deleted it. for me it only happens when I chose to delete the partition and press accept or confirm on deleting it.
this also could happen when the partition gets trashed by faulty HDD or something on that line.

---

### Post by Penguin Guy on 2009-04-04
So would it be possible to set a mountpoint for Windows by changing the  mountpoint of '/dev/sda2' to '/home'?

If so, do I change the mountpoint to '/home', '/home/', 'home/', or simply 'home'?
And is this advisable?

---

### Post by Penguin Guy on 2009-04-04
> **Bölvaður said:**
> a user (a program) must have deleted it. for me it only happens when I chose to delete the partition and press accept or confirm on deleting it.
this also could happen when the partition gets trashed by faulty HDD or something on that line.
yes that was probably me when i was messing around installing/uninstalling different versions of Linux.

---

### Post by lovinglinux on 2009-04-04
> **Penguin Guy said:**
> So would it be possible to set a mountpoint for Windows by changing the  mountpoint of '/dev/sda2' to '/home'?

If so, do I change the mountpoint to '/home', '/home/', 'home/', or simply 'home'?
And is this advisable?

NO. If you mount it as home, then you will mess with your home directory, which already exists. 

> **Penguin Guy said:**
> If so, do I change the mountpoint to '/home', '/home/', 'home/', or simply 'home'?
And is this advisable?

/home

It's not advisable. Mounting a partition in use is not a good idea. You could move the home directory to the unallocated partition. Follow this tutorial [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

Before messing with partitions and mount points, make sure you backup important data and make sure you understand the procedures.

---

### Post by Penguin Guy on 2009-04-04
Ah, I see, so would '/home/windows' work? And yes, I will check the link. Thanks again.

---

### Post by lovinglinux on 2009-04-04
> **Penguin Guy said:**
> Ah, I see, so would '/home/windows' work? And yes, I will check the link. Thanks again.

Read this:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by Penguin Guy on 2009-04-04
Thanks!

---

### Post by kpatz on 2009-04-04
Just to clarify:

/dev/sda1 (the fat16 partition) is probably a recovery partition for Windows.  Is this an OEM machine (e.g. Dell, HP, Gateway)?  They often contain a small partition containing information to allow you to restore/reinstall Windows.

/dev/sda2 is your Windows partition.

/dev/sda3 is an extended partition that houses your remaining partitions.  Without an extended partition you can only have 4 partitions.

The unallocated partition is what would be /dev/sda4.  You can format and put a filesystem here (e.g. /home).

/dev/sda5 is your Linux root partition.

/dev/sda6 is your Linux swap partition.

Like others have said, you can format that unallocated partition (/dev/sda4) with something like ext3 and then mount it somewhere.  If you create a new directory for a mountpoint you can mount and start using it right away.  If you want to put an existing directory into the new filesystem (e.g. /home), you'll have to boot up in recovery mode or from a LiveCD so you're not using /home, mount the new partition somewhere else (e.g. /mnt), move all the files/directories in /home over to /mnt, update /etc/fstab to mount /home automatically on boot, then reboot and you'll have /home in the new partition.

Also, if you use a directory that has files in it as a mountpoint, the files in that directory aren't lost, they're just inaccessible until you unmount the directory.  That's why it's best to use an empty directory as a mountpoint.

---

### Post by CatKiller on 2009-04-04
> **Penguin Guy said:**
> I opened GParted and have attached what I saw to this post.

**fat16 - /dev/sda1:**
This is almost definately for Windows OS data.

It probably isn't. It's probably the "restore partition" created by the OEM that made your computer. Instead of giving you a proper Windows cd, they just give you a simple utility that nukes your existing partition structure and puts this data in its place, so that it's back to the way it was when you got it.

> 
** ntfs - dev/sda2:**
This is my Windows partition.
What does the explanation mark icon mean?
Yes it is.
The exclamation mark is a warning of some kind. I don't know what, though.

> [B]
extended - dev/sda3:[/B]
As has been pointed out, extended partitions are a way to get round the four-partition limit. It is a partition that contains other partitions. Deleting this partition will remove all of the other partitions that it contains. You can see from the GParted screenshot that this partition is a cyan box that contains sda5, sda6 and some unpartitioned space.

> 
**ext3 - dev/sda5:**
ext3 is a type of filesystem.
Mountpoint is where the filesystem 'lives' - for example  '/home/user/music'
The key icon means that the partition is locked and cannot be edited (usually because it is in use)
sda5 and sda6 are locked because they are mounted, and you can't fiddle with a partition that's mounted. They are mounted because you are running GParted from your Ubuntu install, which resides on sda5. If you want to change these partitions, you'll need to run GParted in a way which doesn't involve these partitions being mounted. This means running it from a live cd; either your Ubuntu disc or GParted's own live cd.

Your files are arranged as a tree that has / as its root with all the other files and directories as branches. These other files do not have to be on the same partition, or even on the same computer. The mount point is where you want your partitions to be attached to this tree. Some directory in /media (if you want this partition to be visible on your Desktop) or /mnt (if you don't) is a common place to attach partitions for general storage. Some places (like /boot or /home) have a special function. Some people like to have these functions carried out by using a different partition. It's not necessary, though.

Swap functions on Linux are generally carried out by a special type of filesystem, called SwapFS or Linux swap, although it is possible to use a Windows-style swapfile instead. If you use a different filesystem, then you necessarily have to use a different partition.

You don't have an sda4 because you only have three primary partitions (sda1, 2, and 3). Were you to create another primary partition, this would be sda4. The logical drives in an extended partition always start their numbering at 5, no matter how many other promary partitions you have when you create them, in case you create more primary partitions later up to your quota of four.

You can either (from a live cd, see above) move your / partition to the left and expand it to add that space to your / partition, or create a new partition in your unpartitioned space (which will become sda7) and mount this somewhere on your file tree.

Hopefully this clarifies some things for you.

EDIT: beaten by kpatz!

---

### Post by Penguin Guy on 2009-04-04
Thanks, I think that just about answers all of my questions!

---


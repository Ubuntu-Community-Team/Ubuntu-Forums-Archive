---
title: "Linux - Windows common file system?"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by dmurat on 2009-01-19
I will divide my hdd to 3 parts, one for Ubuntu 8.10, one for Windows Vista and the biggest partition, for all other data (music, video, etc...) and another one for swap (with the swap, totally 4 partitions)

What should the file system of the data part? I want to be able to transfer files from Linux to Windows and from Windows to Linux, using the data partition in the middle. (I hope im clear =) )

---

### Post by gvoima on 2009-01-19
There's not really much choice here. Windows can't write on *nix based filesystems (afaik). So you're better of with formatting it to NTFS and use [NTFS-3G]("http://www.ntfs-3g.org/") from the ubuntu side.

---

### Post by hyper_ch on 2009-01-19
or you can use ext2/3 drivers to write to the linux partition from windows [http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by emarkd on 2009-01-19
If you're building a dual-boot setup, which you probably are, gvoima is correct and you should probably go with ntfs.  If instead you're going to run both OS's at once using some sort of virtualization, you can format it ext3, mount it in ubuntu and share it with Windows using samba.

But if having direct access to the partition from Windows is important, ntfs is the way to go, unfortunately.

---

### Post by gvoima on 2009-01-19
> **hyper_ch said:**
> or you can use ext2/3 drivers to write to the linux partition from windows [http://www.fs-driver.org](http://www.fs-driver.org)

I'd rather use the ntfs-3g driver because of stability. And the FAQ on that page says, that it cannot mount the ext3 as journaling. So there will be problems if there is a crash and ongoing disk operations.

---

### Post by niteshifter on 2009-01-19
Hi,

You've three choices:

1) FAT32 - always works, sort of a universally understood file system. Has a 4GB limit on file sizes.

2) ntfs-3g - Most likely already installed on your Ubuntu system and ready to use. Caveats: Can read compressed files, but cannot write them, cannot deal with encrypted folders/files. Doesn't like unclean Windows shutdowns.

3) Ext2 IFS - Enables Windows to read/write GNU/Linux' ext2 / ext3 file system. Have never used it myself but others here speak highly of it. Their web site is [here]("http://www.fs-driver.org/").

---

### Post by kaibob on 2009-01-19
> **dmurat said:**
> What should the file system of the data part? I want to be able to transfer files from Linux to Windows and from Windows to Linux, using the data partition in the middle. (I hope im clear =) )
It depends on which OS will be used the most. I primarily use linux and very rarely use windows, so I would make the data partition ext3.

---

### Post by hyper_ch on 2009-01-19
> **gvoima said:**
> I'd rather use the ntfs-3g driver because of stability.
I'd rather use ext2/3 because it's all open source... ntfs is still a closed source filesystem and one never truly knows what's going on ;)

---

### Post by Archmage on 2009-01-19
Why is no one using the NTFS-Driver directly in Linux?

---

### Post by mlentink on 2009-01-19
> **Archmage said:**
> Why is no one using the NTFS-Driver directly in Linux?

I don't think I understand your question. Many people use ntfs-3g in a dual boot situation

---

### Post by marco123 on 2009-01-19
I've used both, never had a problem with the ntfs-3g driver writing to ntfs partitions/deleting files etc...   On the the other hand I've recently had to re-format one of my external ext3 hard drives because I was using the fs-driver in windows to write to and from it.

The fs-driver is best used for ext2 partitions/drives because it doesn't update the journal.  So I'd go for ntfs and use the ntfs-3g driver to write to it. (It's already installed in 8.04 and 8.10 so you don't have to do anything to enable write support.)

---

### Post by egalvan on 2009-01-19
> **marco123 said:**
> I've used both, never had a problem with the ntfs-3g driver writing to ntfs partitions/deleting files etc...   On the the other hand I've recently had to re-format one of my external ext3 hard drives because I was using the fs-driver in windows to write to and from it.

The **fs-driver is best used for ext2 partitions/drives because it doesn't update the journal.**  So I'd go for ntfs and use the ntfs-3g driver to write to it. (It's already installed in 8.04 and 8.10 so you don't have to do anything to enable write support.)

This is of no consequence. Journaling is a superset of ext3, and fully back-ward compatible with ext2.

An ext3 volume run without journaling is the same as an ext2 volume.
It will run exactly the same.

This is how an "older" kernel handles the "newer" ext3 volumes.
It merely opens it as ext2.


When an ext3 volume is shut down, the journal must be flushed. Otherwise, you have a dirty volume.
If the volume cannot be cleaned, it will not be mounted.

Since this will be run on a dual-boot machine, the Linux OS must be shut down before booting Windows, thus flushing the journal.
When Windows starts, it will mount the ext3 volume as an ext2 system.


I have used both sets of drivers (ntfs-3g & fs-driver), since 8.04 came out. No prorblems yet. over eight machines.

---

### Post by billgoldberg on 2009-01-19
I would use fat32.

---

### Post by szaka on 2009-01-19
> **hyper_ch said:**
> I'd rather use ext2/3 because it's all open source... ntfs is still a closed source filesystem and one never truly knows what's going on ;)
NTFS-3G is fully open source. We know how NTFS works. Please ask anything you would like to know, I would be very glad to answer you. Thanks.

---

### Post by dmurat on 2009-01-19
what i meant was, suppose i have three partitions
E: has win on it
D: has linux on it
C: has some data (music, documents movies etc.)
in a dual boot system.
i download an mp3 file when using windows. then i move it to C: and restart the pc and switch to linux. i want to be able to listen to this mp3 (or whatever) file stored in C: from linux.

i guess, as mentioned above, ntfs-3g would be the best choice for that?

---

### Post by hyper_ch on 2009-01-19
> **szaka said:**
> We know how NTFS works.

Pls show me the source of ntfs from microsoft :)

---

### Post by szaka on 2009-01-19
> **hyper_ch said:**
> Pls show me the source of ntfs from microsoft :)
It is not something you REALLY want to see it ;-) 

File system development is science, not wooodooo. The important things are the on-disk specification and interoperability with other NTFS implementations. None of them requires the Microsoft NTFS driver source code.

Let's not confuse real-world specification (so not incomplete, obsolete, written, documented specifications) with implementations!

---

### Post by hyper_ch on 2009-01-19
so you don't really know what ntfs does ;)

---

### Post by gandaran on 2009-01-19
> **billgoldberg said:**
> I would use fat32.
yeah, but a fat32 partition is limited to 32 GB, with ntfs I don't know if there are any limits!

---

### Post by Archmage on 2009-01-20
> **mlentink said:**
> I don't think I understand your question. Many people use ntfs-3g in a dual boot situation


If I have a ntfs-partition I just enter the entry with filesystem ntfs in my /etc/fstab and than it works. I had no need to install ntfs-3g and really see no benifit with it.

Therefore I'm asking if there is something better in ntfs-3g? I always had the impression that no one needs it now that we can use ntfs diretly in Linux.

---

### Post by HavocXphere on 2009-01-20
NTFS.

Win can access ext3 if you install drivers...but there is some issue with the inode size, especially since 8.10. The driver only supports ext3 with (I think) max 128 inode size...and 8.10 creates 256 inode sizes by default.(again, I think). I tried a few of the ext3 in Win tools...none of them worked for my setup.

---

### Post by hyper_ch on 2009-01-20
fat32 is not limited to 32gb... it's a lot more, however individual filesize is limited to 4gb.

---

### Post by RyanVanDiemen on 2009-01-20
I have WinXP and Ubuntu dual boot desktop with one HDD completely used for media and other stuff - formatted to NTFS. I guess that`s the same situation you have. Never had any problem with ntfs-3g. I think ntfs is really the way to go...

---

### Post by dmurat on 2009-01-20
alright then i thank you all =) 
solved.

*btw, i cant see the "mark this thread as solved" button? did it disappear?

---

### Post by wallis2812 on 2009-01-20
Please would one of the knowledgable persons from this conversation help me with a partitioning problem. 

I have installed Windows XP and Ubuntu on my computer. Initially I partitioned my harddrive with a partition for: Windows, Ubuntu, Linux boot and Linux swap (4 total). 

All my documents have been on the NTFS Windows partition and accessed there from Linux. However, this has been causing some problems and I would like to create a separate common partition, probably NTFS for my documents, which both Ubuntu and Windows can access. However, I do not have a spare partition space to create this partition, since 4 have already been used up. 

Is it possible to format either the boot partition or the swap partition (am thinking this would be the better one) and then turn it into an extended partition, where the original partition can be recreated along with the new partition. I can resize my Windows partition using GParted to create extra space. However, I have just been worried that when I format the swap partition and then recreate it in an extended partition it might cause problems.

I am trying to avoid reinstalling Ubuntu so want to know if this is possible.

Thanks very much for your help.
From someone who comes from the land where Ubuntu originates.
Ubuntu Ngemunutu Ngabantu

---

### Post by mlentink on 2009-01-22
@[wallis2812]("http://ubuntuforums.org/member.php?u=216882"):

It is probably best to start a new thread on your issue, since it is not really immediately related  to the original problem in this thread. 

Good luck!

---

### Post by szaka on 2009-01-22
> **Archmage said:**
> If I have a ntfs-partition I just enter the entry with filesystem ntfs in my /etc/fstab and than it works. I had no need to install ntfs-3g and really see no benifit with it.

Therefore I'm asking if there is something better in ntfs-3g? I always had the impression that no one needs it now that we can use ntfs diretly in Linux.
The ntfs type also uses the ntfs-3g driver :-)

---


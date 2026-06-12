---
title: "Installation problem: can't mount shared volume"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by Zenrunner92 on 2010-09-21
hi,

I have been trying to do a dual boot install of 32-bit Ubuntu 10.04 LTS on my laptop which has Win7 Premium 64 bit, and all goes well until I try to create a FAT32 shared folder with the remainder of my HDD space (about 400GB).  

Followed the instructions of the book "Ubuntu for Non-Geeks" to the letter but this problem won't go away...any ideas?  Am using the installation CD that came with the book.

Is this a problem with the live CD, or does it sound like there's something wrong with my BIOS or HDD?  Or is there something else that may be causing this issue?

Have been thinking of trying to do the same config install using my copy of Lime instead, see if that's any improvement, but I do prefer Ubuntu.  

Thanks,
ZR

---

### Post by Paddy Landau on 2010-09-23
You don't say what the error is, so we have no idea how to help. Can you give more information about what you tried, and what happened?

Here is a quick run-down of what you need to do:

[LIST]
[*]Create a partition on the empty space and format it. **Take care to partition and format the correct area, otherwise you'll lose your data!** I recommend using NTFS instead of FAT32, because it's significantly more efficient than FAT32. Both Windows and Ubuntu will handle it no problem.
[/LIST]
You can use Gparted to do this (System > Administration > GParted).

---

### Post by Zenrunner92 on 2010-09-24
> **Paddy Landau said:**
> You don't say what the error is, so we have no idea how to help. Can you give more information about what you tried, and what happened?


Thanks for your reply.

The error message was something along the lines of "Unable to mount vFat32 partition [\shared]"---this pops up at about step 7 or 8 in the Installation wizard running off my Ubuntu 10.04 CD, and sends me back to the step (3 or 4) where I am asked to allocate, name and format the various partitions on the HDD.  I tried giving the folder different names but that didn't help...haven't tried using a different file format yet.

I thought that NTFS is strictly for Windows, while FAT32 is compatible with both Windows and a Unix-based OS like Apple or Ubuntu?  The "Ubuntu for Non-Geeks" book was very insistent on using FAT32 for any shared folder, so that's what I was following.  Of course, if you are running a shared NTFS folder for both Ubuntu and Windows w/o any problems then I will assume the book's instruction was off.

---

### Post by Lateralis on 2010-09-24
NTFS support in Linux isn't so hot, as the specifications for the filesystem haven't been released by Windows.  The necessary modules used to access (read/write) NTFS partitions were created on the basis of backwards engineering.  As such, NTFS support in Linux is not 100% fool proof and the use of Windows "root" partition isn't recommended.  (Especially as Windows is a bit antsy and can freak out if changes are made without it knowing about it.)  It is probably for this reason that the book suggests using Fat32.  

However, NTFS support is perfectly usable and I've probably overstated the problems of NTFS use in Linux.  I use NTFS shared drives on all of my computers and I've yet to encounter a problem.  I would therefore recommend you use NTFS as it is a far superior format than the FATs.  Just be careful and try not to use the Windows OS partition (normally C:) as a shared/data partition.  

As for your problem, I think you might need to be more explicit.  I don't have access to a copy of "Ubuntu for Non-Geeks" - I'd never even heard of it until you mentioned it - and have no idea what steps they're proposing.  [This Ubuntu link]("https://help.ubuntu.com/community/Mount") describes how the mount command works; you should probably have a read.  

Essentially though, the mount command is very simple.  If you have the shared partition formatted and ready to mount, then the command

```

sudo mount /dev/sdXY <mount point>

```

should do the job.  This will tell **mount** to mount the device /dev/sdXY to the <mount point> location.  The XY values you have to determine - they uniqely idenfity the drive (X value and lower case letter, e.g. a, b, c...) and the partition on that drive (Y value a number, e.g. 1, 2, 3...).  To determine the XY value of the drive - if you do not know it - you can use either

```

blkid
or
sudo fdisk -l

```

Typical mount points are /mnt/<directory> or /media/<directory>, but you can also place it in your home directory /home/<your username>/<directory>.  

Also, the above command tells mount to automatically determine things such as the partition format.  You can be more explicit by stating:

```

sudo mount -t ntfs /dev/sdXY <mount point>   #for NTFS file system
sudo mount -t vfat /dev/sdXY <mount point>   #for FAT-type file systems

```

If after reading through the link I have provided and using the above commands you still cannot get the device to mount, you should tells us exactly what it is you have done and how you are trying to mount the device.  We can then help you properly. :)

---

### Post by Paddy Landau on 2010-09-24
> **Zenrunner92 said:**
> The error message was something along the lines of "Unable to mount vFat32 partition [\shared]"---this pops up at about step 7 or 8 in the Installation wizard running off my Ubuntu 10.04 CD, and sends me back to the step (3 or 4) where I am asked to allocate, name and format the various partitions on the HDD.
Um, I wonder why the installation disk was attempting to mount it? Did you include that partition as a home directory or whatever? If it's a shared partition (without an operating system), you'd want Ubuntu to ignore it completely.

> **Zenrunner92 said:**
> I thought that NTFS is strictly for Windows, while FAT32 is compatible  with both Windows and a Unix-based OS like Apple or Ubuntu?
I can't talk about Apple's operating system. I don't know which  file systems it supports. If you don't use Mac, then don't worry about  it.

Anyway, that comment about NTFS might have been true a few years ago. But for at least two years (since I started using it), Ubuntu has come with NTFS support included.

There is one problem. If the computer crashes and the NTFS partition is not cleanly unmounted (e.g. when Windows crashes, or if you hibernate from Windows), then Linux won't mount the partition. It's an easy problem to solve: Boot into Windows, and shut-down or reboot before going into Ubuntu.

Anyway, you don't even need to have a shared partition. Instead, access your Windows partition directly from Ubuntu -- it will do so easily and safely (as long as you stick to the data, and don't touch the Windows programs!).

Unfortunately, you cannot access your Ubuntu partition from Windows. No one has written a suitable driver for Windows.

---

### Post by Paddy Landau on 2010-09-24
> **Lateralis said:**
> Essentially though, the mount command is very simple.
The OP shouldn't need the mount command; everything can be done through the GUI, either the Places menu or Nautilus.

---

### Post by Zenrunner92 on 2010-09-26
OK, here are more specifics, hope it will help make this problem clearer...

I have been trying to install Ubuntu using the Live CD of it that came with the book, "Ubuntu For Non-Geeks."  Using the installation wizard that comes with the CD, I get to step 5 of 8 which is called "Prepare Partitions."  The partition table that I am trying to create looks like this:

/dev/sda
  /dev/sda4    swap                      4299MB
  unusable                                  11426MB
  /dev/sda2    ntfs      /windows    40000MB
  /dev/sda1    ext4     /                43000MB
  /dev/sda3    fat32    /shared     401380MB

*For some reason, the drop down menu for the "/dev/sda3" partition does NOT include NTFS as one of the available formats for me to choose.  The available choices are: 

ext4
ext3
ext2
Reiser FS
JFS
XFS
FAT16
FAT32
swap area
do not use this partition

So when I go through all 8 steps of the installation wizard, it begins to install Ubuntu...but about 40 seconds later, I get this message box:

"The attempt to mount a file system with type vfat in SCSI1 (0,0,0), partition #3 (sda) at /shared failed."

ARGH!!!

I have tried to create the same partition table using a Linux Mint Live USB Flash Drive, but got the same result.

So is it possible there's something wrong with my laptop's BIOS or HDD?

In starting this whole process, the computer has resized the Windows7 partition to 40GB from its original 125GB, and now when I boot up the laptop using Windows7 there are a number of hiccups, probably from some of the system files having been removed during this aborted installation/re-partition attempt.  

I really don't want to have to wipe the whole disk because I do want to keep Win7 as a secondary OS, plus the laptop didn't come with a Win7 recovery CD.

---

### Post by Lateralis on 2010-09-26
Why do you have 11 gigs of "unusable"?  Do you mean unused?  

Windows has partitioning tools.  If you want sda3 to be NTFS then I would leave that partition blank, then once Ubuntu is installed go into Windows and make the NTFS partition with the built in toosl.  

Also, it is strongly recommended that you move/resize any Windows partition using its inbuilt tools.  NTFS support in Linux is not 100% fool proof and aside from anything else, Windows 7 can get very touchy about having its files and partition fondled by something other than itself.

---

### Post by Paddy Landau on 2010-09-26
Oh dear, things don't seem quite right.

You say that you're using "the Live CD ... that came with the book". Unfortunately, we have no idea what that Live CD is, or how it differs from the standard Ubuntu installation disk.

Before we give you any further advice, we need to know your current status.

I strongly recommend the following to start with.

[LIST=1]
[*]Boot into Windows, and download the [standard Ubuntu Live CD]("http://www.ubuntu.com/desktop/get-ubuntu/download").
[*]Burn the Live CD to disk (or USB stick if you have one; it will be much faster).
[*]Now boot from the Live CD (or USB) that you created, and select "Try Ubuntu 10.04" (do not try to install at this stage).
[*]Go to System > Adminstration > Gparted.
[*]Save a snapshot of GParted (press Alt-PrintScreen) onto your Desktop.
[*]Start Firefox and post your snapshot.
[/LIST]
This will tell us not only which partitions you have, but also their order.

Then we can take it further.

I presume that you want a straightforward dual-boot with Windows 7 and Ubuntu?

---


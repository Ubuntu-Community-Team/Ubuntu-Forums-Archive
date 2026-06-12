---
title: "Bad Vista shutdown, can I recover data with live cd?"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Papa-san on 2008-12-30
My daughter has a Dell Inspiron 1525 and is running the Vista Virus.
She had a blue screen during her last shutdown, and now it won't re-boot into windows.
I booted it into an Ubuntu 8.04 live session, and would like to mount the windows partition to save some of her important data. 
Because of the bad shutdown, it doesn't want to mount it.
Does anyone know what I can do to force it to mount, and how to burn some of it's files to a cd or put them on a thumb drive?

We homeschool, and she does all of her schoolwork on her laptop. That data is backed up every other time the school program closes, so I know it has clean, recent backups on there... She also has a lot of her digital art that she has drawn and about half of a book she is writing...

All Dell will do is have me reinstall windows via a ghost image... Thus losing all of my data...

Halp! Plz!
:D

---

### Post by dark_harmonics on 2008-12-30
You should be able to mount the drive if you can figure out its device name.

First type:

```
sudo fdisk -l
```

You should see and NTFS partition listed with a device name like /dev/sda1 or /dev/hda1.

You can then mount it to a folder with 

```
sudo mount devicename mountpoint
```

an example of mounting something to  a folder in your home directory would be:

```
sudo mount /dev/sda1 ~/mount
```

Alternately you could use a winpe boot cd like bartpe or build one using the WAIK (Windows automated installation kit).

At my job i use a winepe usb drive and then map a network drive to write the files to.

---

### Post by The_Girl on 2008-12-30
Hey! I'm a newbie at linux but I had a similar problem recently. Knoppix solved it. It usually auto mounts the drive so you can back up your files on dvd's or the like. Remember I'm just a newbie, but hey, it saved my files. I hope it helps!
EDIT: wooops, I hadn't seen that someone else had posted before. Sorry.

---

### Post by cariboo on 2008-12-30
I would suggest you install ntfsprogs

From Synaptic:
> The Linux-NTFS project ([http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)) aims to bring full
support for the NTFS filesystem to the Linux operating system.

This is a set of tools targeted for people interested in working
with the NTFS support in the Linux kernel and using it.  The
following utilities are included:

ntfsfix - Fix common filesystem errors and force Windows to check NTFS.

mkntfs - Format a partition with an NTFS filesystem, optionally bootable.

ntfsinfo - Show some information about an NTFS partition or one of the
files or directories within it.

ntfslabel - Show, or set, an NTFS partition's volume label.

ntfsresize - Resize an NTFS partition without losing data.

ntfsundelete - Recover deleted files from an NTFS partition.

ntfscluster - Locate the owner of any given sector or cluster on an NTFS
partition.

ntfscat - Concatenate files and print them on the standard output
(without mounting the partition).

ntfsls - List directory contents on an NTFS filesystem (without
mounting).

ntfscp - Overwrite files on an NTFS partition.

ntfsclone - Efficiently clone an NTFS filesystem or a part of it.

ntfsmount - Mount an NTFS partition from user-space using libntfs and FUSE.

ntfsdecrypt - Decrypt NTFS-encrypted files (NOT INCLUDED).

ntfscmp - Compare two NTFS volumes and tell the differences.

ntfsprogs is in the repositories and you can use Synaptic Package Manager and of course the command line to install it.

Use ntfsfix to try and repair the disk. The other thing to try if you have a Vista install CD (which I doubt seeing as it's a Dell) :) you can boot from the VIsta install CD and repair the problem.

Jim

---

### Post by dark_harmonics on 2008-12-30
Actually your suggestion is a good one. I use knoppix on a usb stick as well :)

---

### Post by Papa-san on 2008-12-30
The bartpe page says it's for winXP.
Will it work on a Vista system?

---

### Post by dark_harmonics on 2008-12-30
It will still read an NTFS partition. I am assuming you just want to copy files to a USB drive? You could try the repair techniques listed above as well.

---

### Post by oilchangeguy on 2008-12-30
> **Papa-san said:**
> My daughter has a Dell Inspiron 1525 and is running the Vista Virus.
She had a blue screen during her last shutdown, and now it won't re-boot into windows.
I booted it into an Ubuntu 8.04 live session, and would like to mount the windows partition to save some of her important data. 
Because of the bad shutdown, it doesn't want to mount it.
Does anyone know what I can do to force it to mount, and how to burn some of it's files to a cd or put them on a thumb drive?

We homeschool, and she does all of her schoolwork on her laptop. That data is backed up every other time the school program closes, so I know it has clean, recent backups on there... She also has a lot of her digital art that she has drawn and about half of a book she is writing...

All Dell will do is have me reinstall windows via a ghost image... Thus losing all of my data...

Halp! Plz!
:D

the bsod usually occurs because of some change (mostly hardware) that the computer does not like (resource conflict) have you tried to start the computer in safe mode. not sure about vista, but in xp you press F8 repeatedly at startup. until a menu comes up, one of the options is safe mode.

---

### Post by Papa-san on 2008-12-30
I ran ntfsfix, and it allowed me to get into windows... kind of.

I got far enough to have it go into the 'Repair Windows' menu.
As it tried to make repairs, It has reported that the hard drive is failing. 
I get into windows and it locks up tight pretty quickly. 

I am downloading knoppix and bartpe.

EDIT: I tried all of the safe mode and restore options, and none would load up...

---

### Post by teh_yodeler on 2008-12-30
Perhaps the hard drive is failing indeed, and that is the root of these problems...

---

### Post by Papa-san on 2008-12-30
Well, It has been confirmed... The hard drive is shot.

Anyways, the use of ```
sudo fdisk -l
```Allowed me to find the name of the 2 NTFS partitions.
Once I had those, I used ```
sudo ntfsfix /dev/sda2
``` and```
sudo ntfsfix /dev/sda3
```
Those fixed the file system enough for me to be able to save my most important data to a thumb drive. 

Thank you all for your replies and help!

Now, I have people from Dell calling me back to discuss having these 3 Inspiron 1525 systems exchanged for different ones... These are absolute JUNK!

On 2 of them, I have had the motherboards replaced *twice each* in less than 9 months. The third has had it's replaced once. I have had a LCD go bad on one. Media bar failed on two. Hinges nuked on two. DVD burner/drive went on one, and now the hard drive on one... I wonder how long it will take for the others to go bad?

The ones that I bought for my daughters actually shock them in their ears through the earbuds, and on their hands from under the chassis. (I'm betting this is why the hard-drive went bad... And why the others will probably follow...)

Mine doesn't shock me too frequently because It just kinda lives on the table, but when I do need to move it, It will give a good zap...

---

### Post by dark_harmonics on 2008-12-31
One time i froze a bad hard drive (yes in the freezer) and set it vertically not horizontal to get data from it. The hard drive had bad bearings and as soon as i turned it horizontal again it completely crashed.

Edit: Missed the second page before i posted that. Good news! At least you got your data.

---

### Post by gn2 on 2008-12-31
A [Vista Recovery CD]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") might help.

---


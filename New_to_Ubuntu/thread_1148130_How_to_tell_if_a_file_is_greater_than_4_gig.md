---
title: "How to tell if a file is greater than 4 gig"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by Mick8882003 on 2009-05-04
I need to copy some files (music) to an external hard drive, now I have tried this before and it will crash half way through (32gig pen drive)

I need to search my music files to see if there are any larger than 4 gig, I assume this is the problem.

Thanks Mick

---

### Post by Malta paul on 2009-05-04
Right click on your file, then check properties. 
:)

---

### Post by freak42 on 2009-05-04
in the root folder of the files to be copied try the command:

find -size +4G

this finds files bigger than 4 Gigabytes.. you can also specify the size in Megabytes (M) and probably other units. I am not sure if on certain filesystems even files bigger than 2 Gigs cause problems.

hth

---

### Post by freeman2000 on 2009-05-04
Go to Places --> Music and right-click on the folder, then left-click on Properties.  This will tell you the size of your Music folder.  If you open the Music folder, you can right-click on any of the individual folders inside to find out how large each individual folder is.  You may have to copy individual folders from within the Music folder instead of trying to copy the whole Music folder at once.  For example, my Music folder is over 30 gb, but each individual artist folder within it is less than 500 mb.  Hope this helps.

---

### Post by Kevbert on 2009-05-04
An easy way to do this is to display all file sizes in Nautilus File Manager. Open Nautilus and then go to Edit-Preferences. Under the Views Tab select Arrange items by size from the pull-down menu. Now go to the Display Tab select Icon captions and set the first box to size. Then select Close. All files will now be listed in their directories in file size order with the file size displayed. You can even modify the Preview Tab if required.

---

### Post by Mark Phelps on 2009-05-04
I guess it must still be "standard practice" for suppliers to format USB sticks using FAT32 -- even if the sticks hold or more!

My solution was easier -- stick the USB stick in the machine, open Partition Editor, remove the existing partitions, reformat the stick as NTFS.

Now, I can save any size file I want to the drive.

---

### Post by gordintoronto on 2009-05-04
What program did you use?  I think KDE's Partition Manager can create NTFS partitions, but Parted can not?


> **Mark Phelps said:**
> I guess it must still be "standard practice" for suppliers to format USB sticks using FAT32 -- even if the sticks hold or more!

My solution was easier -- stick the USB stick in the machine, open Partition Editor, remove the existing partitions, reformat the stick as NTFS.

Now, I can save any size file I want to the drive.

---

### Post by Mark Phelps on 2009-05-05
I used the Partition Editor in GNome -- a version of GParted.  If that's not available in KDE, you can always download and burn a GParted LiveCD from distrowatch.com and use that.

---

### Post by gordintoronto on 2009-05-05
I'm using Gnome.  Gparted won't create an NTFS partition.

> **Mark Phelps said:**
> I used the Partition Editor in GNome -- a version of GParted.  If that's not available in KDE, you can always download and burn a GParted LiveCD from distrowatch.com and use that.

---

### Post by Mark Phelps on 2009-05-05
I've used GParted versions as far back as 3.5 (current is 4.4) and ALL have been able to create NTFS partitions. Have you tried the GParted LiveCD?

How about doing an "fdisk -lu" (that's a lowercase L, not a one) on the device you're trying to format.

Also, you sure you're mounting it in read/write mode?

If it's a permission problem, then run from the GParted LiveCD, that way, you can be sure that (1) you're running as root, and (2) the device is not mounted.

---

### Post by gordintoronto on 2009-05-05
I'm running from a fresh install of Jaunty.  I needed to download Ntfsprogs, then Gparted could do everything with NTFS partitions.


> **Mark Phelps said:**
> I've used GParted versions as far back as 3.5 (current is 4.4) and ALL have been able to create NTFS partitions. Have you tried the GParted LiveCD?


---


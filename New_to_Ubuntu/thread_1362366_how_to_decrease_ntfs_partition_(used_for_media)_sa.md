---
title: "how to decrease ntfs partition (used for media) safetly"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by theromanone on 2009-12-23
Hi there, I have two partitions:
1)Ubuntu on a 13gb ext4. This is just the install and programs. 2GB are free
2)Every file any program uses, media, etc, on a 210GB NTFS. 70GB are free

I'm going to try opensuse, mint, and play around with gnome, kde to see what I like best. Been Ubuntu for a while, want to start fresh.

*  The problem is, I would like to free up HD space, around 60GB, from the NTFS partition to play around with the other distros. In windows, I would of had to defrag the partition before resizing it so as to not lose any files.. Can I simply resize the partition (dragging the right arrow in Gparted to the left until I get 60GB free) without having to worry about losing any data?

Is there something I should do to the NTFS partition before resizing it to ensure no data loss? Thanks!

---

### Post by theromanone on 2009-12-23
Hi there, I have two partitions:
1)Ubuntu on a 13gb ext4. This is just the install and programs. 2GB are free
2)Every file any program uses, media, etc, on a 210GB NTFS. 70GB are free

I'm going to try opensuse, mint, and play around with gnome, kde to see what I like best. Been Ubuntu for a while, want to start fresh.

* The problem is, I would like to free up HD space, around 60GB, from the NTFS partition to play around with the other distros. In windows, I would of had to defrag the partition before resizing it so as to not lose any files.. Can I simply resize the partition (dragging the right arrow in Gparted to the left until I get 60GB free) without having to worry about losing any data?

Is there something I should do to the NTFS partition before resizing it to ensure no data loss? Thanks!

---

### Post by adam814 on 2009-12-23
I've never had a problem resizing NTFS partitions using Gparted.  As long as you don't try to shrink the partition to less than the amount of space used it shouldn't be a problem.

The only problem you might run into is that by leaving only 10GB free on the NTFS partition you'll be unable to effectively defragment it afterwards.  Last I checked Windows complains about less than 15% free space for that reason.

---

### Post by prshah on 2009-12-23
> **theromanone said:**
> Can I simply resize the partition (dragging the right arrow in Gparted to the left until I get 60GB free) without having to worry about losing any data?

Is there something I should do to the NTFS partition before resizing it to ensure no data loss? Thanks!

In theory (and mostly even in reality) you can do just what you are suggesting and it will work fine. But the risk of data loss is inherent, especially if the resize operation is interrupted. 

I always suggest a backup to third parties, but I personally never bother with it; and have had to suffer once (out of over 200 operations) for it.

One thing you can do to ensure that your resizing operation is trouble free; please keep swap enabled, unless it also has to be resized/moved, etc. With swap enabled, large resizing operations move much faster; I don't know why.

Good luck!

---

### Post by audiomick on 2009-12-23
Hallo.
Have you got windows on the machine at all? You didn't say.

If you have, I would strongly recommend a degfrag first; maybe twice if the partition has been in use for a while, maybe twice. Also, if the windows is on this partition, start it a couple of times after the defrag, and let it do any disc checking it wants to do.

If you have no windows, think about changing the file system to a Linux format. This would involve copying your data across to somewhere else, doing your partition changes, then copying back.

---

### Post by Mark Phelps on 2009-12-23
If the NTFS partition is strictly data (i.e., no OS on it), you should have no trouble resizing it with GParted.  Even if it's a WinXP partition, GParted should still work OK.  The problems have surfaced when GParted was used to resize Vista OS partitions.

---

### Post by audiomick on 2009-12-23
You have two identical threads going.
[http://ubuntuforums.org/showthread.php?t=1362408](http://ubuntuforums.org/showthread.php?t=1362408)

This is not good etiquette.

---

### Post by audiomick on 2009-12-23
You have two identical threads going.
[http://ubuntuforums.org/showthread.php?p=8547594#post8547594](http://ubuntuforums.org/showthread.php?p=8547594#post8547594)

This is not good etiquette.

---

### Post by ST3ALTHPSYCH0 on 2009-12-23
If you do have windows on the drive just make sure to uncheck the "round to cylinders" box in Gparted. I resized my buddy's HDD w/ Vista on it and it fired right up.... If you don't uncheck that box you will have to do a repair install or let the machine sit for around 4hours while vista remakes it's own partition.

---

### Post by wkulecz on 2009-12-23
Fry's regularly has 1GB drive on sale for $70.  Unless your data (or time to attempt recovery) are worth less than this you'd be very foolish indeed to not backup your data before resizing any partition.

--wally.

---

### Post by theromanone on 2009-12-23
Thanks to all! No I have no windows, but kept the files partition in NTFS in case I ever wanted windows so it would be able to be read by both windows and linux. I'll try it!

---

### Post by Shpongle on 2009-12-23
> **audiomick said:**
> hallo.
Have you got windows on the machine at all? You didn't say.

If you have, **i would strongly recommend a degfrag first**; maybe twice if the partition has been in use for a while, maybe twice. Also, if the windows is on this partition, start it a couple of times after the defrag, and let it do any disc checking it wants to do.

If you have no windows, think about changing the file system to a linux format. This would involve copying your data across to somewhere else, doing your partition changes, then copying back.
+1

as far as i know windows can read ext3 if you plan on having windows but ext4 has better performance. but windows cant read it

---

### Post by theromanone on 2009-12-23
Yeah, tried to shrink the NTFS by values of 5, 15, 40, 70GB, and each gave this error when in Gparted (both in liveCD and in gnome):

GParted 0.4.5

Libparted 1.8.8.1.159-1e0e
Shrink /dev/sda1 from 219.65 GiB to 148.04 GiB  00:01:04    ( ERROR )
     	
calibrate /dev/sda1  00:00:00    ( SUCCESS )
     	
path: /dev/sda1
start: 27744255
end: 488392064
size: 460647810 (219.65 GiB)
check file system on /dev/sda1 for errors and (if possible) fix them  00:00:16    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 235851678208 bytes (235852 MB)
Current device size: 235851678720 bytes (235852 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 155819 MB (66.1%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 113565 MB 0
Multi-Record : 235852 MB 23212
$MFTMirr : 117926 MB 1
Sparse : 113108 MB 11158
Ordinary : 235852 MB 21597
You might resize at 155818422272 bytes or 155819 MB (freeing 80033 MB).
Please make a test run using both the -n and -s options before real resizing!
shrink file system  00:00:33    ( ERROR )
     	
run simulation  00:00:33    ( ERROR )
     	
ntfsresize -P --force /dev/sda1 -s 158961761279 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 235851678208 bytes (235852 MB)
Current device size: 235851678720 bytes (235852 MB)
New volume size : 158961754624 bytes (158962 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 155819 MB (66.1%)
Collecting resizing constraints ...
Needed relocations : 11025913 (45163 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1136 > 1024), not yet supported!
Please try to free less space.
check file system on /dev/sda1 for errors and (if possible) fix them  00:00:15    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 235851678208 bytes (235852 MB)
Current device size: 235851678720 bytes (235852 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 155819 MB (66.1%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 113565 MB 0
Multi-Record : 235852 MB 23212
$MFTMirr : 117926 MB 1
Sparse : 113108 MB 11158
Ordinary : 235852 MB 21597
You might resize at 155818422272 bytes or 155819 MB (freeing 80033 MB).
Please make a test run using both the -n and -s options before real resizing!
grow file system to fill the partition  00:00:00    ( SUCCESS )
     	
run simulation  00:00:00    ( SUCCESS )
     	
ntfsresize -P --force /dev/sda1 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 235851678208 bytes (235852 MB)
Current device size: 235851678720 bytes (235852 MB)
New volume size : 235851674112 bytes (235852 MB)
Nothing to do: NTFS volume size is already OK.
real resize  00:00:00    ( SUCCESS )
     	
ntfsresize -P --force /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 235851678208 bytes (235852 MB)
Current device size: 235851678720 bytes (235852 MB)
New volume size : 235851674112 bytes (235852 MB)
Nothing to do: NTFS volume size is already OK.

========================================




Any help here? Thanks again!

---

### Post by bapoumba on 2009-12-24
Threads merged.

---


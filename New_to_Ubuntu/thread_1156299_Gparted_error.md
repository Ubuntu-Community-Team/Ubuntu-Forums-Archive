---
title: "Gparted error"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by timbim on 2009-05-11
I'm trying to resize the NTFS partiton on a friends laptop to install Ubuntu into the unpartitioned space, but Gparted always errors from the Ubuntu live CD, so I've used Gparted on the System Rescue CD, but that doesn't work either, producing the following error log.```
GParted 0.4.4

Libparted 1.8.8
Shrink /dev/sda3 from 54.44 GiB to 30.38 GiB  00:00:11    ( ERROR )
     	
calibrate /dev/sda3  00:00:00    ( SUCCESS )
     	
path: /dev/sda3
start: 120262590
end: 234436544
size: 114173955 (54.44 GiB)
check file system on /dev/sda3 for errors and (if possible) fix them  00:00:05    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda3
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda3
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 58457063936 bytes (58458 MB)
Current device size: 58457064960 bytes (58458 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 30838 MB (52.8%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 7401 MB 0
$MFTMirr : 1 MB 1
Compressed : 99 MB 33
Ordinary : 44792 MB 6725
You might resize at 30837399552 bytes or 30838 MB (freeing 27620 MB).
Please make a test run using both the -n and -s options before real resizing!
shrink file system  00:00:05    ( ERROR )
     	
run simulation  00:00:05    ( SUCCESS )
     	
ntfsresize -P --force /dev/sda3 -s 32621460479 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda3
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 58457063936 bytes (58458 MB)
Current device size: 58457064960 bytes (58458 MB)
New volume size : 32621453824 bytes (32622 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 30838 MB (52.8%)
Collecting resizing constraints ...
Needed relocations : 1972262 (8079 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
The read-only test run ended successfully.
real resize  00:00:00    ( ERROR )
     	
ntfsresize -P --force /dev/sda3 -s 32621460479
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
ERROR(95): Opening '/dev/sda3' as NTFS failed: Operation not supported
The NTFS journal file is unclean. Please shutdown Windows properly before
using this software! Note, if you have run chkdsk previously then boot
Windows again which will automatically initialize the journal correctly.
check file system on /dev/sda3 for errors and (if possible) fix them  00:00:01    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda3
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda3
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 58457063936 bytes (58458 MB)
Current device size: 58457064960 bytes (58458 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 30838 MB (52.8%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 7401 MB 0
$MFTMirr : 1 MB 1
Compressed : 99 MB 33
Ordinary : 44792 MB 6725
You might resize at 30837399552 bytes or 30838 MB (freeing 27620 MB).
Please make a test run using both the -n and -s options before real resizing!
grow file system to fill the partition  00:00:00    ( ERROR )
     	
run simulation  00:00:00    ( SUCCESS )
     	
ntfsresize -P --force /dev/sda3 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda3
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 58457063936 bytes (58458 MB)
Current device size: 58457064960 bytes (58458 MB)
New volume size : 58457059840 bytes (58458 MB)
Nothing to do: NTFS volume size is already OK.
real resize  00:00:00    ( ERROR )
     	
ntfsresize -P --force /dev/sda3
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
ERROR(95): Opening '/dev/sda3' as NTFS failed: Operation not supported
The NTFS journal file is unclean. Please shutdown Windows properly before
using this software! Note, if you have run chkdsk previously then boot
Windows again which will automatically initialize the journal correctly.

========================================
```Anyone advise on what's wrong?

---

### Post by AndThenWhat on 2009-05-11
I would do what the error message at the bottom says:

- run chkdsk
- and most importantly: shutdown windows properly before you try resizing that NTFS partition.

---

### Post by finer recliner on 2009-05-11
> Please shutdown Windows properly before
using this software!

restart the computer into windows and then shut it down. it may have shut down incorrectly last time. (also run a defrag if you haven't already)

---

### Post by Niniel on 2009-05-11
Looks like this is wrong:
> Please shutdown Windows properly before
using this software! Note, if you have run chkdsk previously then boot Windows again which will automatically initialize the journal correctly.

Even offers a solution.
Also, if your friend has Vista/W7, it's better to use the Windows partitioner to resize the NTFS partition.

---

### Post by Didius Falco on 2009-05-11
All good stuff above - one other thing I'd add. If the swap file for Windows is on the same partition, you should set it to "no swap file" until after you resize it. Windows will often stick the swap file towards the outer edge of the partition, and it may block the resize.

You can reset it after you are done with your partitioning work.

---

### Post by timbim on 2009-05-11
Thanks.  All installed and working now.  It's late and I'm more than a little tired, I just thought it was an error log that only the hardcore experts would understand.  You guys rock!

---


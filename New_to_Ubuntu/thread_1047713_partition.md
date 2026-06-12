---
title: "partition"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by windows hater on 2009-01-22
hello im trying to partition my HD so that i can run both windows and ubuntu but the partition editor wont let me do it so far everything is running on one partition and thats windows but when i seperate it i get an error and im only using a boot cd right now 

thanks ahead

---

### Post by DezSP on 2009-01-22
What is the error?

---

### Post by DariusS on 2009-01-22
> **windows hater said:**
> hello im trying to partition my HD so that i can run both windows and ubuntu but the partition editor wont let me do it so far everything is running on one partition and thats windows but when i seperate it i get an error and im only using a boot cd right now 

thanks ahead

If you could elaborate a bit more, it would help. Are you trying to split the HD into NTFS and EXT3? I know the installation formatting app is capable of simply resizing partitions to make room for the linux install, which has always been the way I do it with 8.10.

---

### Post by windows hater on 2009-01-22
Move /dev/sda1 to the left and shrink it from 292.29 GiB to 146.14 GiB  00:00:19    ( ERROR )
     	
calibrate /dev/sda1  00:00:00    ( SUCCESS )
     	
path: /dev/sda1
start: 2048
end: 612974591
size: 612972544 (292.29 GiB)
calculate new size and position of /dev/sda1  00:00:00    ( SUCCESS )
     	
requested start: 0
requested end: 306488069
requested size: 306488070 (146.14 GiB)
new start: 63
new end: 306488069
new size: 306488007 (146.14 GiB)
check filesystem on /dev/sda1 for errors and (if possible) fix them  00:00:04    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 313841938944 bytes (313842 MB)
Current device size: 313841942528 bytes (313842 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 82932 MB (26.4%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 3287 MB 0
Multi-Record : 184992 MB 17075
$MFTMirr : 156921 MB 1
Compressed : 185180 MB 43774
Sparse : 176523 MB 27534
Ordinary : 185191 MB 22012
You might resize at 82931306496 bytes or 82932 MB (freeing 230910 MB).
Please make a test run using both the -n and -s options before real resizing!
shrink filesystem  00:00:10    ( ERROR )
     	
run simulation  00:00:09    ( SUCCESS )
     	
ntfsresize -P --force --force /dev/sda1 -s 156921859583 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 313841938944 bytes (313842 MB)
Current device size: 313841942528 bytes (313842 MB)
New volume size : 156921852416 bytes (156922 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 82932 MB (26.4%)
Collecting resizing constraints ...
Needed relocations : 3108444 (12733 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
The read-only test run ended successfully.
real resize  00:00:01    ( ERROR )
     	
ntfsresize -P --force --force /dev/sda1 -s 156921859583
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
ERROR(95): Opening '/dev/sda1' as NTFS failed: Operation not supported
The NTFS journal file is unclean. Please shutdown Windows properly before
using this software! Note, if you have run chkdsk previously then boot
Windows again which will automatically initialize the journal correctly.
check filesystem on /dev/sda1 for errors and (if possible) fix them  00:00:03    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 313841938944 bytes (313842 MB)
Current device size: 313841942528 bytes (313842 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 82932 MB (26.4%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 3287 MB 0
Multi-Record : 184992 MB 17075
$MFTMirr : 156921 MB 1
Compressed : 185180 MB 43774
Sparse : 176523 MB 27534
Ordinary : 185191 MB 22012
You might resize at 82931306496 bytes or 82932 MB (freeing 230910 MB).
Please make a test run using both the -n and -s options before real resizing!
grow filesystem to fill the partition  00:00:02    ( ERROR )
     	
run simulation  00:00:01    ( SUCCESS )
     	
ntfsresize -P --force --force /dev/sda1 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 313841938944 bytes (313842 MB)
Current device size: 313841942528 bytes (313842 MB)
New volume size : 313841938944 bytes (313842 MB)
Nothing to do: NTFS volume size is already OK.
real resize  00:00:01    ( ERROR )
     	
ntfsresize -P --force --force /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
ERROR(95): Opening '/dev/sda1' as NTFS failed: Operation not supported
The NTFS journal file is unclean. Please shutdown Windows properly before
using this software! Note, if you have run chkdsk previously then boot
Windows again which will automatically initialize the journal correctly.

---

### Post by handydan918 on 2009-01-22
> Opening '/dev/sda1' as NTFS failed: Operation not supported
The NTFS journal file is unclean. Please shutdown Windows properly before
using this software! Note, if you have run chkdsk previously then boot
Windows again which will automatically initialize the journal correctly.

This is enough to cause a lot of problems. I suggest doing as it says, and try again.

---

### Post by DezSP on 2009-01-22
It looks like you're trying to shrink your Windows partition by more than it's capable of. I suggest you run a CHKDSK (this should happen automatically when you next boot Windows) and a defragment, then try again. If it still fails then try shrinking it by a smaller amount.

---

### Post by DariusS on 2009-01-22
I am certainly no expert, but I've had issues mounting ntfs partitions in the past and received similar errors. This only happened to me when I had not performed a clean shutdown of windows. That is, let the OS shutdown completely by itself. Windows is finicky like that ;)

---

### Post by DariusS on 2009-01-22
> **DezSP said:**
> It looks like you're trying to shrink your Windows partition by more than it's capable of. I suggest you run a CHKDSK (this should happen automatically when you next boot Windows) and a defragment, then try again. If it still fails then try shrinking it by a smaller amount.

Also important^
ALWAYS defrag NTFS drives before partitioning them, as windows doesn't do a good job of housekeeping.

---


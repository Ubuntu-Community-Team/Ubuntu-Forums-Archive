---
title: "GParted Not Working"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by darklinkq on 2009-12-24
I get this error

```
GParted 0.4.5

Libparted 1.8.8
Move /dev/sda3 to the left and grow it from 198.46 GiB to 416.34 GiB  00:01:48    ( ERROR )
     	
calibrate /dev/sda3  00:00:00    ( SUCCESS )
     	
path: /dev/sda3
start: 560556045
end: 976751999
size: 416195955 (198.46 GiB)
calculate new size and position of /dev/sda3  00:00:00    ( SUCCESS )
     	
requested start: 103635315
requested end: 976768064
requested size: 873132750 (416.34 GiB)
new start: 103635315
new end: 976768064
new size: 873132750 (416.34 GiB)
check file system on /dev/sda3 for errors and (if possible) fix them  00:00:07    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda3
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda3
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 213092327936 bytes (213093 MB)
Current device size: 213092328960 bytes (213093 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 95371 MB (44.8%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 205016 MB 0
Multi-Record : 213072 MB 66761
$MFTMirr : 106547 MB 1
Compressed : 212103 MB 180918
Sparse : 122312 MB 152179
Ordinary : 213087 MB 130390
You might resize at 95370342400 bytes or 95371 MB (freeing 117722 MB).
Please make a test run using both the -n and -s options before real resizing!
move partition to the left  00:00:01    ( SUCCESS )
     	
old start: 560556045
old end: 976751999
old size: 416195955 (198.46 GiB)
new start: 103635315
new end: 519831269
new size: 416195955 (198.46 GiB)
move file system to the left  00:01:39    ( ERROR )
     	
using internal algorithm
copy 416195955 sectors
finding optimal blocksize
     	
copy 65536 sectors using a blocksize of 64 sectors  00:00:02    ( SUCCESS )
     	
65536 of 65536 copied
1.81323 seconds
copy 65536 sectors using a blocksize of 128 sectors  00:00:01    ( SUCCESS )
     	
65536 of 65536 copied
1.42243 seconds
copy 65536 sectors using a blocksize of 256 sectors  00:00:01    ( SUCCESS )
     	
65536 of 65536 copied
1.28112 seconds
copy 65536 sectors using a blocksize of 512 sectors  00:00:02    ( SUCCESS )
     	
65536 of 65536 copied
1.24843 seconds
copy 65536 sectors using a blocksize of 1024 sectors  00:00:01    ( SUCCESS )
     	
65536 of 65536 copied
0.892112 seconds
copy 65536 sectors using a blocksize of 2048 sectors  00:00:01    ( SUCCESS )
     	
65536 of 65536 copied
1.16833 seconds
copy 65536 sectors using a blocksize of 4096 sectors  00:00:01    ( SUCCESS )
     	
65536 of 65536 copied
1.12854 seconds
copy 65536 sectors using a blocksize of 8192 sectors  00:00:01    ( SUCCESS )
     	
65536 of 65536 copied
1.04683 seconds
copy 65536 sectors using a blocksize of 16384 sectors  00:00:01    ( SUCCESS )
     	
65536 of 65536 copied
1.01528 seconds
copy 65536 sectors using a blocksize of 32768 sectors  00:00:01    ( SUCCESS )
     	
65536 of 65536 copied
0.875618 seconds
copy 65536 sectors using a blocksize of 65536 sectors  00:00:01    ( SUCCESS )
     	
65536 of 65536 copied
0.798631 seconds
optimal blocksize is 65536 sectors (32.00 MiB)
copy 415475059 sectors using a blocksize of 65536 sectors  00:01:26    ( ERROR )
     	
5416307 of 415475059 copied
Error while reading block at sector 566693248
6137203 sectors copied
rollback last change to the partition table  00:00:01    ( SUCCESS )
     	
move partition to the right  00:00:01    ( SUCCESS )
     	
old start: 103635315
old end: 519831269
old size: 416195955 (198.46 GiB)
new start: 560556045
new end: 976751999
new size: 416195955 (198.46 GiB)
libparted messages    ( INFO )
     	
Error informing the kernel about modifications to partition /dev/sda5 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sda5 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
Input/output error during read on /dev/sda
Error informing the kernel about modifications to partition /dev/sda5 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sda5 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.

========================================
```

---

### Post by dwasifar on 2009-12-24
Looks like you are trying to work on a drive with mounted partitions.

Try booting from a live CD instead.

---

### Post by darklinkq on 2009-12-24
This...IS a live cd actually <.<

---

### Post by Eldera on 2009-12-24
[quote=dwasifar]Try booting from a live CD instead[/quote]

+1 also, right click your swap files and choose "swapoff" if swaps show lock.

Edit: sorry, you added a post while I was typing. If using a live CD and swapoff doesn't do it you'll have to bump. I don't know what else to do.

---

### Post by darklinkq on 2009-12-24
Swapoff?

---

### Post by Eldera on 2009-12-24
When you boot from a live Ubuntu CD and open Gparted, does the screen show any lock or key symbols like my /dev/sda4 and /dev/sda5 partitions in the first screen shot. If it does, it means that that partition is mounted and locking Gparted out. If you right click on the line where the lock is, a drop down menu should appear giving you the option to "swapoff" if it is a swap partition or "unmount" if it is a regular partiton. Click swapoff. (Do the swap partition before the extended partition. The extended partition may unmount automatically.) The locks should disappear as in my second screen shot and Gparted should then work.

If you do not having any locks showing on your screen, you have a different problem and someone else is going to have to help. I am a bit of a newbie myself. I just know that getting the partitions unlocked helped me in a simular problem.

I hope you get this worked out.

---

### Post by darklinkq on 2009-12-24
That's..not the issue...I've now got it to the point where it says I have 4 bad sectors ; ;

---

### Post by dwasifar on 2009-12-24
> **darklinkq said:**
> That's..not the issue...I've now got it to the point where it says I have 4 bad sectors ; ;

If it...says you have bad sectors...then you should probably run...e2fsck before...you try resizing.

---


---
title: "expanding partition on RAID array"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by AndyInNYC on 2010-12-31
I have a 3ware 9500S-8 RAID card running with Ubuntu 10.04 64 bit server.

The array is not the boot drive.


I added a drive to my array (using the 3ware migrate utility).  This expanded my array to 5.4 TB.  Ubuntu is not 'seeing' the new space.  I understand this is because the partition space hasn't been allocated.

Using gparted, I attempted to expand the partition to take up the full space on the drive.

Gparted fails; I saved the log file, but I can't locate it on my system - not sure where it was put.

Gparted correctly identified the correct size of the drive prior to attempt to extend the partition.

Questions:

Is there a limit on drive size that gparted can address?
Is there another tool I can use to correctly extend the partition and get full use of the array?  I don't want to create a separate partition - I'd like to keep it as a single partition.

Any help is appreciated.

Andrew

---

### Post by AndyInNYC on 2011-01-03
This is the error message created by gparted.  I'm not sure how to fix the gpt as suggested.

Help?



GParted 0.6.2

Libparted 2.3
Grow /dev/sdc1 from 2.73 TiB to 4.55 TiB  01:52:16    ( ERROR )
     	
calibrate /dev/sdc1  00:00:03    ( SUCCESS )
     	
path: /dev/sdc1
start: 34
end: 5859311582
size: 5859311549 (2.73 TiB)
check file system on /dev/sdc1 for errors and (if possible) fix them  00:55:49    ( SUCCESS )
     	
e2fsck -f -y -v /dev/sdc1
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

28367 inodes used (0.01%)
3453 non-contiguous files (12.2%)
47 non-contiguous directories (0.2%)
# of inodes with ind/dind/tind blocks: 21237/4359/90
310327601 blocks used (42.37%)
0 bad blocks
105 large files

27269 regular files
1089 directories
0 character device files
0 block device files
0 fifos
0 links
0 symbolic links (0 fast symbolic links)
0 sockets
--------
28358 files
e2fsck 1.41.12 (17-May-2010)
grow partition from 2.73 TiB to 4.55 TiB  00:00:00    ( ERROR )
     	
old start: 34
old end: 5859311582
old size: 5859311549 (2.73 TiB)
check file system on /dev/sdc1 for errors and (if possible) fix them  00:56:23    ( SUCCESS )
     	
e2fsck -f -y -v /dev/sdc1
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

28367 inodes used (0.01%)
3453 non-contiguous files (12.2%)
47 non-contiguous directories (0.2%)
# of inodes with ind/dind/tind blocks: 21237/4359/90
310327601 blocks used (42.37%)
0 bad blocks
105 large files

27269 regular files
1089 directories
0 character device files
0 block device files
0 fifos
0 links
0 symbolic links (0 fast symbolic links)
0 sockets
--------
28358 files
e2fsck 1.41.12 (17-May-2010)
grow file system to fill the partition  00:00:01    ( SUCCESS )
     	
resize2fs /dev/sdc1
     	
resize2fs 1.41.12 (17-May-2010)
The filesystem is already 732413943 blocks long. Nothing to do!

libparted messages    ( INFO )
     	
The backup GPT table is not at the end of the disk, as it should be. This might mean that another operating system believes the disk is smaller. Fix, by moving the backup to the end (and removing the old backup)?
Not all of the space available to /dev/sdc appears to be used, you can fix the GPT to use all of the space (an extra 3906207744 blocks) or continue with the current setting?
The backup GPT table is not at the end of the disk, as it should be. This might mean that another operating system believes the disk is smaller. Fix, by moving the backup to the end (and removing the old backup)?
Not all of the space available to /dev/sdc appears to be used, you can fix the GPT to use all of the space (an extra 3906207744 blocks) or continue with the current setting?
Unable to satisfy all constraints on the partition.

========================================

---

### Post by srs5694 on 2011-01-03
I was pretty sure that libparted (upon which GParted is based) corrected this problem automatically. I could be misremembering, though, or it could be a version-specific difference.

In any event, you can use my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) to fix the problem. Download and install the latest version from its [Sourceforge downloads page](http://sourceforge.net/projects/gptfdisk/files/) (the version in the Ubuntu repositories is hopelessly out of date), and do this:


[list=1]
[*]Type "sudo gdisk /dev/sdc" (or whatever the appropriate device filename is)
[*]Type "x" to enter experts' mode
[*]Type "e" to relocate the backup data
[*]Type "w" to save your changes.
[/list]


You can also create new partitions with gdisk, if you like, but if you want to resize partitions, GParted is much easier to use.

---

### Post by AndyInNYC on 2011-01-04
srs5694,

Thanks for the response - I believe you replied directly to an email from me with the same info.

A bit of clarification:

Are you saying that if I follow your four steps my problem is (hopefully solved)?  Or do I need additional steps somewhere between steps 1 and 4?

Additionally, do I need to run these steps AFTER I run gparted and it fails or just 'all by themselves'.

I'm tarring up the array now, but I'd rather not have to f*%#% it up (the array) and do a restore.

All your help and hand-holding is appreciated.

Andrew

---

### Post by srs5694 on 2011-01-04
Once the software is installed, those four steps fix it. It doesn't matter whether or not GParted looks at the disk first (unless of course doing so would fix the problem, in which case my procedure would do neither harm nor good).

Backups are always good. You may also want to check out the 'b' option on the gdisk main menu; that backs up the partition table itself so that you can restore it later. This could be handy if a partitioning tool clobbers the partition table without damaging the filesystems within the partitions.

---

### Post by AndyInNYC on 2011-01-06
Ran the program and no change to array size.

Downloaded the newest version (64 bit) and ran it.  Completed successfully.
Upon reboot, the array is still 3.0 TB in the OS and 5.4 on the 3ware side (it sees everything).

I ran the commands exactly as stated and then ran
sudo sync
3 times (read in one other post somewhere to do that)

Stubborn array!

I'm happy to provide more info, but I don't know what to do next.

Andrew

---

### Post by AndyInNYC on 2011-01-06
One additional/final thought.

Right now, /dev/sdc has a single partition - /dev/sdc1 which is only part of the array.

Do I need to partition the rest (as /dev/sdc2 for example) and THEN run your program?  I'm running the program with the extra space unrecognized by the OS (although as discussed, gparted sees the space correctly).

I'm thinking if there is the option to merge partitions (although one would be empty).

Andrew

---

### Post by srs5694 on 2011-01-06
You use gdisk as I described to get the rest of the space usable *for partitioning*. You must still resize your existing partition and/or create new partition(s) in the new space. If might be helpful if you'd post the output of:

```

sudo gdisk -l /dev/sdc

```

This will show us the disk size and the size of your partition, which can help with providing further advice.

I suspect, though, that the answer at this point is to start up GParted and use it to resize the partition. Using gdisk as I described should allow GParted to get past its stumbling block that you reported in your first post.

---

### Post by AndyInNYC on 2011-01-06
Here's the output:

GPT fdisk (gdisk) version 0.6.13

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdc: 9765519360 sectors, 4.5 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): A08759EE-AC07-406F-8B1B-74C1B8D69F31
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 9765519326
Partitions will be aligned on 8-sector boundaries
Total free space is 3906207744 sectors (1.8 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34      5859311582   2.7 TiB     0700  primary




All of which seems to make sense (although not what I want).  The 4.5 TB is right and the 2.8TB is what is currently recognized.


Andrew

---

### Post by srs5694 on 2011-01-06
You've left out a critical piece of information from your statement (easy to do when using passive voice):

> ...and the 2.8TB is what is currently recognized.

The question is, *what* is recognizing 2.8 TB?

My suspicion is that you're looking at disk free space on the mounted filesystem. If so, the solution is, as I suggested, to use GParted to resize that partition and the filesystem it contains.

To elaborate, there are several different size issues that must be addressed in sequence when you add space to a RAID array, but gdisk only addressed one of them:


[list=1]
[*]The size of the disk (or hardware RAID array, in your case). This was changed by your RAID controller when you added the disk.
[*]The amount of space that's usable by the partition table, which in GPT is limited by the placement of the secondary data structures (normally at the end of the disk, but when you resized the array, they were no longer located there). This was the source of the error message you reported, and was fixed by gdisk when you followed my instructions.
[*]The size of the partition that holds the filesystem on the disk. This hasn't yet been changed. It can be changed in at least two different ways (see below).
[*]The size of the filesystem contained by the partition on the disk. This also hasn't yet been changed. Again, see below.
[/list]


Resizing partitions and resizing filesystems usually go hand-in-hand. This task is most easily performed by GParted, which does both simultaneously and presents a friendly point-and-click interface. GParted was flaking out because of problem #2, but since gdisk has fixed that issue, you can proceed to #3 and #4; GParted *should* now be OK with your disk. (If you try it and it still flakes out, post back with details.) You *could* use gdisk to correct #3 by deleting and then re-creating that partition; however, if you did this wrong you could be in worse shape, and even if you were successful you'd then need to use the text-mode resize2fs to perform step #4. It's much easier to use GParted to do steps #3 and #4 together.

---

### Post by AndyInNYC on 2011-01-06
After running gdisk I reran gparted - which took 2 hours +.

I now have a partition equal to the array size and all is well.

Hurray.

Thanks for your help.

Andrew

---


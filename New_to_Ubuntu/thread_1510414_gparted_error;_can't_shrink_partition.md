---
title: "gparted error; can't shrink partition"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by stevepoppers on 2010-06-15
I'm trying to shrink my partition to fit crunchbang onto a tiny bit of free space and have it and my normal Ubuntu Desktop share a /home folder. I'm using the gparted on the crunchbang live cd, which should be the same as was in Jaunty. It fails and I get an error. The attached screenshots should explain it pretty well. Here are the Details:
> GParted 0.4.3
 Libparted 1.8.8
    **Move /dev/sda5 to the right and shrink it from 367.87 GiB to 362.86 GiB**  00:00:57    ( ERROR )             calibrate /dev/sda5  00:00:01    ( SUCCESS )             [I]path: /dev/sda5
start: 199122944
end: 970604543
size: 771481600 (367.87 GiB)[/I]          calculate new size and position of /dev/sda5  00:00:00    ( SUCCESS )             [I]requested start: 199125738
requested end: 960108659
requested size: 760982922 (362.86 GiB)[/I]       [I]new start: 199125675
new end: 960108659
new size: 760982985 (362.86 GiB)[/I]          check file system on /dev/sda5 for errors and (if possible) fix them  00:00:28    ( SUCCESS )             ***e2fsck -f -y -v /dev/sda5***             [I]Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

   14641 inodes used (0.06%)
     413 non-contiguous files (2.8%)
       8 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 14517/89/4
 9351172 blocks used (9.70%)
       0 bad blocks
       2 large files

   13141 regular files
    1470 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
      18 symbolic links (18 fast symbolic links)
       3 sockets
--------
   14632 files
[/I]       [I]e2fsck 1.41.4 (27-Jan-2009)
[/I]             shrink file system  00:00:00    ( ERROR )             ***resize2fs /dev/sda5 380491492K***             [I]resize2fs 1.41.4 (27-Jan-2009)
Please run 'e2fsck -f /dev/sda5' first.

[/I]             check file system on /dev/sda5 for errors and (if possible) fix them  00:00:28    ( SUCCESS )             ***e2fsck -f -y -v /dev/sda5***             [I]Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

   14641 inodes used (0.06%)
     413 non-contiguous files (2.8%)
       8 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 14517/89/4
 9351172 blocks used (9.70%)
       0 bad blocks
       2 large files

   13141 regular files
    1470 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
      18 symbolic links (18 fast symbolic links)
       3 sockets
--------
   14632 files
[/I]       [I]e2fsck 1.41.4 (27-Jan-2009)
[/I]             grow file system to fill the partition  00:00:00    ( SUCCESS )             ***resize2fs /dev/sda5***             [I]resize2fs 1.41.4 (27-Jan-2009)
The filesystem is already 96435200 blocks long.  Nothing to do!

[/I]             ========================================
 It runs e2fsck, tries to shrink the partition, but says to run e2fsck first, which it just did!

---

### Post by stevepoppers on 2010-06-15
Well, it would appear I fixed my own problem. A post on the gparted forums said to try the gparted livedisc and it appears to be working. It's going to take almost **_3 HOURS,_** however. Lame. but worth it in the end, I suppose. At least I've got this other machine to play on and most of my stuff on an external. I will update and mark as SOLVED when everything's done. Maybe this will make someone else's day a little easier.

Edit: 3 hours later, it's going to take **_6 HOURS_** to move the partition to the right. Can it really not go faster?

---

### Post by john newbuntu on 2010-06-16
Well, you could have just shrunk /dev/sda5 from the right boundary by 5 GB.  This would have gotten you the space that you wanted a lot lot faster especially with the data so sparse.  Remember moving a partition on its left boundary takes forever especially with dense data(not so much in your case but still 6 hours!!).  I hope you have a backup of /dev/sda5 just in case.

---

### Post by wilee-nilee on 2010-06-16
Just for reference if you turn off the swap you should be able to do it on any live disc. The reason the gparted disc works is it doesn't activate using swap I think.

---

### Post by stevepoppers on 2010-06-16
> **john newbuntu said:**
> Well, you could have just shrunk /dev/sda5 from the right boundary by 5 GB.  This would have gotten you the space that you wanted a lot lot faster especially with the data so sparse.  Remember moving a partition on its left boundary takes forever especially with dense data(not so much in your case but still 6 hours!!).  I hope you have a backup of /dev/sda5 just in case.
It seemed to want to move it no matter what I did. I didnt want my OS's surrounding my /home. I seemed sloppy, but I'll probably have to just deal with  if I want to install any more logical partitions. The time makes sense if it has to move all the data on there. Yes, I have a recent enough backup.

> **wilee-nilee said:**
> Just for reference if you turn off the swap you should be able to do it on any live disc. The reason the gparted disc works is it doesn't activate using swap I think.
I thought the swap was off. In the screenshot, there's no key next to it. I'm pretty sure I unmounted it myself.

---


---
title: "Missing Disk space"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by brallan on 2011-03-18
Note: 5% of the space on an ext3 partition is reserved for root use, that is why I was missing some 23GB on a 500GB HD..... thanks [mikechant]("http://ubuntuforums.org/member.php?u=721760") for your solution below!!!

************************************************************

i have a 500GB external USB drive, which although there should be 24GB of space on it, there is less than 1GB. why could this be?

df -h shows:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1             459G  435G  807M 100% /media/MassCool

```Even taking into account the 1000 vs 1024 bytes thing, the math just doesn't add up.

---

### Post by blind2314 on 2011-03-18
Assuming you're using this as backup or other storage within Ubuntu.
 
You can try this:
 
```

cd /media/MassCool
du -sh *

```
 
That should give you the total size that each folder/file is taking up.
 
Also,
 
```
ls -lah
```
 
will show any hidden folders/files and how much size they're using as well (in a "human" format).

---

### Post by seawolf167 on 2011-03-18
A pretty basic suggestion - have you check your & root's trash to ensure they are emptied? Some files could be held up in there.

Else follow blind2314's suggestion and see what is using up your disk space

---

### Post by brallan on 2011-03-18
Thanks for your answer, blind2314!

> **blind2314 said:**
> Assuming you're using this as backup or other storage within Ubuntu. 

Yes.

> **blind2314 said:**
> 
```

cd /media/MassCool
du -sh *

```That should give you the total size that each folder/file is taking up.
 

here's what it says:

eeepc@eeepc-901:/media/MassCool$ du -sh *
du: cannot read directory `lost+found': Permission denied
16K    lost+found
435G    VIDEO

even if I mount is as root, it says the same:
root@eeepc-901:/media/MassCool# du -sh *
16K    lost+found
435G    VIDEO

> **blind2314 said:**
> 
```
ls -lah
```will show any hidden folders/files and how much size they're using as well (in a "human" format)

but it only shows me the size of the folder file, not the folder size:

```
eeepc@eeepc-901:/media/MassCool$ ls -lah
total 28K
drwx------ 4 eeepc eeepc 4.0K 2011-03-18 15:01 .
drwxr-xr-x 4 root  root  4.0K 2011-03-18 15:15 ..
drwx------ 2 root  root   16K 2011-02-11 12:45 lost+found
drwx------ 6 eeepc eeepc 4.0K 2011-03-17 23:20 VIDEO

```

---

### Post by brallan on 2011-03-18
> **seawolf167 said:**
> A pretty basic suggestion - have you check your & root's trash to ensure they are emptied? Some files could be held up in there.

Else follow blind2314's suggestion and see what is using up your disk space

tried all that, to no avail.

But now I am starting to wonder if the partition is bad:

sudo fdisk -l shows it as an NTFS disk!

```
Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e7314

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS
```but sudo blkid shows it as ext4!

```
/dev/sdc1: LABEL="MassCool_465GB" UUID="0bd4e71d-ad2e-4d9c-80f7-bbf399a811ae" TYPE="ext4" 

```Maybe something is very wrong with the partition. Or perhaps the Masscool external USB enclosure doesn't like ext4? Is it possible?

I'd hate to redo this data, as it is a lot of copying. I'm going to install gparted and see what it says.

---

### Post by brallan on 2011-03-18
well, resized the partition using gparted and fdisk still shows it as ntfs though gparted thinks it is a ext4 disk. what could this mean?

gparted is not finding any errors

---

### Post by mikechant on 2011-03-18
Firstly, I don't understand the NTFS/ext4 discrepancy, but assuming it *is* a valid ext4 filesystem, the explanation for the mssing 24GB is probably quite simple - by default 5% of the disc is reserved and can only be used by root.
This may be appropriate for a root filesystem but for most other filesystems it's unnecessary.

You can easily reduce or eliminate this reserved area (I've done it myself several times). Use this command:

```
sudo tune2fs -m 0 /dev/sdc1
```

The -m option specifies the reserved % - in this case 0%, no space reserved.
This should take effect immediately, try a df -h to check.

(If it really is an NTFS filesystem tune2fs should recognize this and not do anything).

---

### Post by brallan on 2011-03-18
now gparted gave me an error. Going to repartition.

---

### Post by mikechant on 2011-03-18
Removed in light of the above comment.

---

### Post by blind2314 on 2011-03-18
> **brallan said:**
> Thanks for your answer, blind2314!
 
 
 
Yes.
 
 
 
here's what it says:
 
eeepc@eeepc-901:/media/MassCool$ du -sh *
du: cannot read directory `lost+found': Permission denied
16K lost+found
435G VIDEO
 
even if I mount is as root, it says the same:
root@eeepc-901:/media/MassCool# du -sh *
16K lost+found
435G VIDEO
 
 
 
but it only shows me the size of the folder file, not the folder size:
 
```
eeepc@eeepc-901:/media/MassCool$ ls -lah
total 28K
drwx------ 4 eeepc eeepc 4.0K 2011-03-18 15:01 .
drwxr-xr-x 4 root  root  4.0K 2011-03-18 15:15 ..
drwx------ 2 root  root   16K 2011-02-11 12:45 lost+found
drwx------ 6 eeepc eeepc 4.0K 2011-03-17 23:20 VIDEO

```
 
Yes, it only shows you the folder size, but it also proves that there's nothing hidden in the root directory (not /, the root directory of this drive) taking up space. Here's another idea. DISCLAIMER: In the old Solaris world, fsck can cause some..issues. Since this isn't your root partition, it's not going to FUBAR your machine, but data loss is always a possibility (though highly unlikely).
 
```
fsck -n -t ext4 /media/MassCool
```

---

### Post by psusi on 2011-03-18
You may not want to remove the 5% reservation.  Any time you fill the disk above 90% it is going to start getting heavily fragmented, so it's a good idea to NOT fill it up all the way.

---

### Post by mikechant on 2011-03-19
> You may not want to remove the 5% reservation. Any time you fill the disk above 90% it is going to start getting heavily fragmented, so it's a good idea to NOT fill it up all the way. 

If you are filling up a large partition with lots of media files over time, but not editing these files subsequently, they will not be very fragmented and keeping the reserved area reserved will just be a waste.
And fragmentation only really matters when it gets bad enough to cause some sort of stuttering or dropouts when playing media files, which is unlikely on modern hardware.

---

### Post by brallan on 2011-03-19
So, if I format it ext4, then it by default 5 percent of the partition space is reserved for root use? Sounds like it might have been what was going on. I had never before used ext4 for a usb drive, and was unaware of that. 

how can one see if there is space reserved for root on a partition? And how does one keep that space from getting assigned to root?

Thanks for all of your help. In the end I simply decided to repartition the drive in light of the error gparted gave  me, and chose NTFS since it has always worked for me in the past.... I  am using two 500GB disks to back up a single terabyte disk, so having that extra 5%  is  important. 12 hours later, the backup is done.

---

### Post by mikechant on 2011-03-21
If you add together the 'used' and 'avail' amounts from "df -h" then subtract the total from the 'size' amount this will show how much space is reserved, i.e. using the "df -h" output from your original post in this thread:

reserved = free - (used + avail)
         = 459G - (435G + 807M)
         = 459G - 436G approx
         = 23G

Note that 23G/459G = 0.05 = 5% reserved

My earlier post in this thread:
[http://ubuntuforums.org/showpost.php?p=10573753&postcount=7](http://ubuntuforums.org/showpost.php?p=10573753&postcount=7)
shows the tune2fs command to reduce or remove the reserved space.


One further thought is that maybe on a backup drive it could be worth leaving 1-2% reserved as a warning - i.e., you hit 'disc full', remove the reserved space and successfully complete the backup, but you've been warned that you're nearly out of space and have a bit of time to take some action before your disc is really completely full.

---

### Post by psusi on 2011-03-22
> **mikechant said:**
> If you are filling up a large partition with lots of media files over time, but not editing these files subsequently, they will not be very fragmented and keeping the reserved area reserved will just be a waste.
And fragmentation only really matters when it gets bad enough to cause some sort of stuttering or dropouts when playing media files, which is unlikely on modern hardware.

Yes, they will be.  The less free space is left on the disk, the less large free extents there are, so putting one more large file on to use up the last of the space will leave it VERY fragmented.

---

### Post by mikechant on 2011-04-28
> Yes, they will be. The less free space is left on the disk, the less large free extents there are, so putting one more large file on to use up the last of the space will leave it VERY fragmented. 

In the extreme case where all files are written sequentially one at a time (like a tape backup) you will get exactly zero fragmentation on any sensible filesystem - every file, including the last one that fills the disc, will get a contiguous space allocation.
What I am asserting is that for drives full of large media files where deletions and updates are very rare, the real life case will be very close to this situation. This is based on at least one assumption - that bittorrent clients generally reflect the behavior of the ones I have used, where they allocate entire files in one chunk, in one operation, at their full size (and fill in the actual data in place later). Also it assumes that a typical disc copy operation using cp, rsync etc. when copying multiple files essentially copies one file at a time rather than interleaving them.
Essentially, I'm saying that certain common patterns of media file accumulation where files are typically allocated in one operation, or one file at a time, and never updated or deleted subsequently, does in fact lead to the filesystems being written to in an entirely sequential pattern with zero fragmentation.
The odd deletion or update will give some fragmentation but it will not be significant because the deleted areas will still be large and will typically only end up in making the odd file use 2 extents rather than one.
Using different tools/applications etc. to obtain media files may in some cases introduce fragmentation but this will typically be localized (e.g in some cases downloading three single music tracks simultaneously will lead to these files being interleaved but the three files as a whole will form one contiguous blocks and subsequent space will still be contiguous).

to remove any doubt, I'm *not* talking about any filesystems which include such things as the browser cache which will typically be being updated frequently in small chunks. This alone will cause serious fragmentation in that filesystem. I'm talking specifically only about filesystems dedicated to large media files.

Apologies if this is a bit rambling/repetitive, I'm "celebrating" the royal wedding in the traditional British way by consuming large amounts of alcohol!

---


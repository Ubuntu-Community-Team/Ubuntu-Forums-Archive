---
title: "Hard Drive formatting question"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by Marko723 on 2009-09-27
Question;

If I issue the following command to format a new physical HDD 

*mkfs.ext3 -b 4096 /dev/**sdb***

opposed to 

*mkfs.ext3 -b 4096 /dev/**sdb1***

Are there any problems?  I know mkfs came back to confirm I wanted to do the whole drive opposed to a partition, and I gave it the go ahead.  After the format I ran *fdisk -l* and it said there was a error with the partition type, but going in to fdisk, not changing anything and issuing a write corrected this complaint by fdisk.

My question is, will there be any problems down the road, or have I introduced any limitation in formatting the whole drive opposed to a partition?  The drive and data appear to behave with out issue.

(side note: I did use fdisk before the format to partition the whole HDD to a single type 83 partition, I assume this is why fdisk was complaining when I did the *fdisk -l*)

Thanks

Mark

---

### Post by mikeyphi on 2009-09-27
If the disk is still seen as a single partition - there shouldn't be any problem. You could easily check using Partition Editor.
I think the point, probably, is that Ubuntu mounts partitions - rather than whole drives.

---

### Post by mapes12 on 2009-09-27
> **Marko723 said:**
> Question;

If I issue the following command to format a new physical HDD 

*mkfs.ext3 -b 4096 /dev/**sdb***

opposed to 

*mkfs.ext3 -b 4096 /dev/**sdb1***

Are there any problems?  I know mkfs came back to confirm I wanted to do the whole drive opposed to a partition, and I gave it the go ahead.  After the format I ran *fdisk -l* and it said there was a error with the partition type, but going in to fdisk, not changing anything and issuing a write corrected this complaint by fdisk.

My question is, will there be any problems down the road, or have I introduced any limitation in formatting the whole drive opposed to a partition?  The drive and data appear to behave with out issue.

(side note: I did use fdisk before the format to partition the whole HDD to a single type 83 partition, I assume this is why fdisk was complaining when I did the *fdisk -l*)

Thanks

MarkIs there a reason why you want to do this the hard way rather than using a Live CD or a GParted CD to do this for you?

---

### Post by Marko723 on 2009-09-27
> **mapes12 said:**
> Is there a reason why you want to do this the hard way rather than using a Live CD or a GParted CD to do this for you?

I enjoy technology.  My original career many years ago was in IT support (enterprise firewalls, networking...etc)  Over the years this evolved to more supervision, management, and now IT auditing.   I miss the hands on, and would rather understand the true power behind Ubuntu opposed to a point and click.

The other reason is that I've built a home file server out of a old P4 with 5 - 1.5GB data HDDs to act as a place to store all my multimedia.  The plan is to move the server in a corner in the basement with out a monitor.  When I expand the storage in the future I plan to bring everything on-line through command line.  

I've been cutting my teeth (or clearing the cobwebs from years of using windows) over the last couple of weeks by simulating this scenario.  After the base install, I configured SSH and haven't logged in to the local console since.  All the data drives, Samba shares (including the Samba install) have all been through a putty terminal.  I've even been updating the core patches via terminal.

Although this may change down the road, depending on mood, right now I'm totaly enjoying this and wouldn't do it any other way.

Mark

---

### Post by mcduck on 2009-09-27
> **Marko723 said:**
> Question;

If I issue the following command to format a new physical HDD 

*mkfs.ext3 -b 4096 /dev/**sdb***

opposed to 

*mkfs.ext3 -b 4096 /dev/**sdb1***

Are there any problems?  I know mkfs came back to confirm I wanted to do the whole drive opposed to a partition, and I gave it the go ahead.  After the format I ran *fdisk -l* and it said there was a error with the partition type, but going in to fdisk, not changing anything and issuing a write corrected this complaint by fdisk.

My question is, will there be any problems down the road, or have I introduced any limitation in formatting the whole drive opposed to a partition?  The drive and data appear to behave with out issue. The use of partitions is pretty much a standard on IBM PC-compatible computers.

(side note: I did use fdisk before the format to partition the whole HDD to a single type 83 partition, I assume this is why fdisk was complaining when I did the *fdisk -l*)

Thanks

Mark

It's not possible to use a hard disk without having at least one partition on the disk. Of course you can make the partition to use the whole disk, but you still need to make one and format that, not the disk.

Edit: I researched a bit, and it seems that you might be able to use the disks without partitioning them. But You'd probably have quite hard time booting anything from such a disk (since BIOS looks for MBR for information where to start running code to boot te OS, and MBR is not present on a non-partitioned disk), and most of the tools around will assume partitions so you might run into other unexpected troubles.

I'd rather play it safe and set up single partitions on each disk, since the partition table doesn't really use any noticeable amount of disk space compared to size hard drives are these days. But of course you are free to see if things work without any too serious problems. :)

---

### Post by Marko723 on 2009-09-27
> **mcduck said:**
> It's not possible to use a hard disk without having at last one partition on the disk. Of course you can make the partition to use the whole disk, but you still need to make one and format that, not the disk.

Hmmm... ok, I may have to re-do things then.  This is what fdisk says;

```
Command (m for help): p

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52f85806

   Device Boot      Start         End      Blocks   Id  System

Command (m for help): v
2930277167 unallocated sectors
```

and df
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             453G  121G  310G  29% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  1.2M 1006M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  160K 1007M   1% /dev
tmpfs                1007M     0 1007M   0% /dev/shm
lrm                  1007M  2.2M 1005M   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sdb              1.4T  417G  889G  32% /mnt/WD_1
/dev/sdc              1.4T  198M  1.3T   1% /mnt/WD_2
/dev/sdd              1.4T  198M  1.3T   1% /mnt/WD_3
/dev/sde              1.4T  198M  1.3T   1% /mnt/WD_4
/dev/sdf              1.4T  308G  999G  24% /mnt/WD_5
```

The data is intact and valid, so I must have a partition (sdb - sdf), no?

---

### Post by Marko723 on 2009-09-27
Well, to be safe, I'll redo the partitions.  sdc is done, and I've re-done the symbolic links..etc.  most time consuming will be moving the data off sdb and sdf to sdc1 then moving things back to the original drives.

From what I can tell, there are no partitions, I'm using a formatted drive and the data is fine.  To play it safe for long term, I'll create partitions and this time make sure I'm formatting the partitions and not the drive. 

I guess in the future I need to pay closer attention or not do things like this sitting on the couch with kids jumping all over me. 

Thanks for the feedback.

---

### Post by Marko723 on 2009-09-27
> **mcduck said:**
> It's not possible to use a hard disk without having at least one partition on the disk. Of course you can make the partition to use the whole disk, but you still need to make one and format that, not the disk.

Edit: I researched a bit, and it seems that you might be able to use the disks without partitioning them. But You'd probably have quite hard time booting anything from such a disk (since BIOS looks for MBR for information where to start running code to boot te OS, and MBR is not present on a non-partitioned disk), and most of the tools around will assume partitions so you might run into other unexpected troubles.

I'd rather play it safe and set up single partitions on each disk, since the partition table doesn't really use any noticeable amount of disk space compared to size hard drives are these days. But of course you are free to see if things work without any too serious problems. :)

It's only the data disks that were done this way, and I think I found a clue on how this was possible.  When I ran fdisk and it corrected the problem it placed something called "relatime" is the fstab.

/dev/sde /mnt/WD_4 ext3 defaults,relatime 1 1

I'm in the process of setting up partitions on the data drives now, so I should be back by the end of the day.  The data move is the pain, even under SATA-II.

Thanks for the feedback!

Cheers!

Mark

---

### Post by mcduck on 2009-09-27
> **Marko723 said:**
> It's only the data disks that were done this way, and I think I found a clue on how this was possible.  When I ran fdisk and it corrected the problem it placed something called "relatime" is the fstab.

/dev/sde /mnt/WD_4 ext3 defaults,relatime 1 1

I'm in the process of setting up partitions on the data drives now, so I should be back by the end of the day.  The data move is the pain, even under SATA-II.

Thanks for the feedback!

Cheers!

Mark

"relatime" is only related to the way last access times for files is stored in the filesystem, so it shouldn't have anything to do with this.

"atime"-option stores last access time for files, "relatime" only stores the access time if the last access time is older than the file's modify time (to reduce disk writes and increase performance when compared to "atime". "noatime" disables saving the access time completely.

---

### Post by Marko723 on 2009-09-27
> **mcduck said:**
> "relatime" is only related to the way last access times for files is stored in the filesystem, so it shouldn't have anything to do with this.

"atime"-option stores last access time for files, "relatime" only stores the access time if the last access time is older than the file's modify time (to reduce disk writes and increase performance when compared to "atime". "noatime" disables saving the access time completely.

Yes, mt 1st assumption appears wrong.  After some google searches I turned up the same information as you posted here.  Just not sure how it got into the fstab, as I didn't add it.

Just going to write this up as a learning experience and move on.  I'm still rusty at this with only fragments of my memories intact.   It's been about 14 years since I've administered a UNIX box.  Back then I think it was HP-UX ver 9.x...

Thanks for your help!

Mark

---


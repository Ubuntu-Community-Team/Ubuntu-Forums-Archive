---
title: "Hard drive partitions"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by Rayve on 2009-10-20
Okay, so I finally got Ubuntu 9.04 on a real side-by-side dual-boot setup with my Windows XP, instead of from Wubi.  I did this via a LiveCD of gparted which worked great - I shrunk the main HD to give Windows about 200GB, then created a small 3G swap area, and made about another 200G of extended partition.  Within there, I put 30G for my / root drive and about 150G for /home, and left 20G unallocated just in case...

Now, here's my output of sudo blkid, as you can tell, Ubuntu created another swap partition of it's own when it did the install from it's LiveCD, and when I slid the partitioner over during install, it only let me go until the 150G area, not the addiitonal 30G, though I made both ext3.

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04282ece

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1957    15719571    c  W95 FAT32 (LBA)
/dev/sda2   *        1958       27260   203246347+   7  HPFS/NTFS
/dev/sda3           27261       27662     3229065   82  Linux swap / Solaris
/dev/sda4           27663       60801   266189017+   5  Extended
/dev/sda5           27663       31486    30716248+  83  Linux
/dev/sda6           31487       31931     3574431   83  Linux
/dev/sda7           31932       60050   225865836   83  Linux
/dev/sda8           60051       60801     6032376   82  Linux swap / Solaris
candice@candice-desktop:~$ sudo blkid
/dev/sda1: LABEL="HP_RECOVERY" UUID="2B72-1CC3" TYPE="vfat" 
/dev/sda2: UUID="D0EC7E96EC7E7696" LABEL="HP_PAVILION" TYPE="ntfs" 
/dev/sda3: TYPE="swap" LABEL="linuxswap" UUID="41a0c790-ed7b-4588-b5db-0c35c23fb7f9" 
/dev/sda5: LABEL="root" UUID="7540f4a4-7107-4e14-84f7-3335d630d7e8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: LABEL="home" UUID="5b141c5d-db65-4de9-93da-2fa5dc14ca57" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="a941fe4c-c29d-412e-a717-4edff3361398" TYPE="ext3" 
/dev/sda8: TYPE="swap" UUID="91d3eed7-beac-4f88-8b59-eb6ceb557692" 

```Can I remove one of the swaps?  How do I make my /home partition on the one I wanted it to be?  It looks like, according to the blkid (that is, the space allocated to them, not the names), I meant /dev/sda6 to be root and /dev/sda7 to be home, but everything got shifted?  Or am I reading it incorrectly?  This is literally a brand-spanking new install, so I can re-install and change settings if I did it incorrectly the first time.

Thanks!

EDIT: Here's my cat /etc/fstab:

```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=a941fe4c-c29d-412e-a717-4edff3361398 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=91d3eed7-beac-4f88-8b59-eb6ceb557692 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

I'm not confident editing this on my own yet - can I just tell it that /sda7 is home, then add in a line for /sda6 being root?

---

### Post by tarps87 on 2009-10-20
The easiest way on the basis this is a new install it to reinsall selecting manual partitioning, this will allow you to use gparted to remove your partitions and re-allocate them. You can modify you current install to use the existing partitions and only one swap partition, it you want to do it this way post back and I will explain how

---

### Post by Rayve on 2009-10-20
> **tarps87 said:**
> The easiest way on the basis this is a new install it to reinsall selecting manual partitioning, this will allow you to use gparted to remove your partitions and re-allocate them. You can modify you current install to use the existing partitions and only one swap partition, it you want to do it this way post back and I will explain how

That sounds good to me!  I shied away from the manual install the first time since I wasn't comfortable doing it on my own.  :)  Thank you!

---

### Post by tarps87 on 2009-10-20
> **Rayve said:**
> That sounds good to me!  I shied away from the manual install the first time since I wasn't comfortable doing it on my own.  :)  Thank you!

:) Basically the manual install does the same as the gparted cd, if you need any pointers just post back.

Note: You have probably already worked this out don't delete this partitions.
/dev/sda1               1        1957    15719571    c  W95 FAT32 (LBA)
/dev/sda2   *        1958       27260   203246347+   7  HPFS/NTFS

---

### Post by Bartender on 2009-10-20
I'd say start over.  Go in with your GParted LiveCD and delete the entire extended partition, then delete sda3.  Apply the changes.

Then create one extended partition out of the entire unallocated space.  If you want to (this is how I like to do it anymore) create your logical partitions for /, swap, /home, etc. with the GParted LiveCD.  I need to explain a distinction.  You won't actually create the / partition, or the /home partition.  You'll create a logical partition that looks to be about the right size for /, and make another one for /home that looks to be the size you want.  You'll format these partitions as ext3 or 4.

Then, when you go back in with your Ubuntu install CD, you'll use the manual method and mount / to the partition that you'd previously created, and mount /home to the partition that you created, etc.

Do you see what I mean?  With the GParted LiveCD, you're just carving out the pieces that you want and making them ready for data, you're not actually reserving them as / or /home or whatever.

The swap partition is different.  When you create it in GParted LiveCD and format it as swap, that's what it's going to be.  Still has to be mounted during installation, but the difference is you've already made it the swap partition before leaving GParted.

The very simplest thing to do in your case would be delete everything starting with sda3, then create one extended partition, then just point Ubuntu installer at the free space.  But it looks like you want to create manual partitions.  :)

---

### Post by Rayve on 2009-10-20
Thank you both! :)

Bartender, quick question - if Ubuntu already made a swap, will it make it again using manual partitions, or will it let me keep the swap I make with GParted?

And yes, the partitioning you mentioned makes sense.  Create the extended and logical partitions with GParted, but wait until the Ubuntu install to actually label them and mount root and /home myself, instead of expecting Ubuntu to read my mind.  :P

---

### Post by Bartender on 2009-10-20
I'm dating myself by quoting from Cheech & Chong's first movie, but sometimes my head is like a sieve.  I've manually partitioned at least a dozen times in the last year or so, and I don't remember exactly how the swap thing goes.  I'm sure that I had to mount it as swap when I was in the Ubuntu manual installation process, it's just that it was a little bit different that mounting / and /home.
The button clicks weren't quite the same, something like that.  It wasn't difficult to figure out, it just wasn't exactly like the other two mounts.
So that's how I do it - create three partitions in GParted LiveCD.  Two of them are just ext partitions, destined to be mounted as / and /home by the installer, but the swap partition is formatted as swap so that's all it can be.  When you get out of GParted and fire up the Ubuntu installer, you still have to tell the Ubuntu installer, "here's the swap partition that I want you to use".

This might help - there are some screenshots in this thread.

[http://ubuntuforums.org/showthread.php?t=1249374](http://ubuntuforums.org/showthread.php?t=1249374)  

A couple of these are dual-boot.  If you compare them, you'll see some differences and some similarities.  For instance, the / partition is primary in one scheme.  But it's logical in another.  Fortunately for us, Linux can boot from within an extended partition!

One hard-and-fast rule I try to stick to is this - no more than two primary partitions if I can.  Three's OK, but then you're up against the stops.

---

### Post by Rayve on 2009-10-20
Worked perfectly!  :)  Thanks, everyone.

---


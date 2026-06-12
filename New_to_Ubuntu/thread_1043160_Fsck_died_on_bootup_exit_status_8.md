---
title: "Fsck died on bootup exit status 8"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by marker5a on 2009-01-18
Hello everyone
I am a newbie to ubuntu as well as linux period.  I am receiving an error upon booting up ubuntu and I get the "fsck died with exit status 8" message.  I looked through everything I could find on the internet and havewnt found a solution to my problem.  

/var/log/fsck/checkfs:
> 
Log of fsck -C3 -R -A -a
Sat Jan 17 20:54:09 2009

fsck 1.41.3 (12-Oct-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  71:4f/46, 72:53/41, 73:20/54, 74:53/33, 75:48/32, 76:41/00, 77:52/00
  , 78:45/00, 79:20/00, 80:20/00, 81:20/00
  Not automatically fixing this.
/dev/sda7: 11 files, 11/1278673 clusters
/dev/sda5 is mounted.  e2fsck: Cannot continue, aborting.


fsck died with exit status 8

Sat Jan 17 20:54:10 2009
----------------


/etc/fstab:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=771d35fc-1145-4cea-80d8-35529c14d230 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=927F-5972  /osshare        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=af70d5dc-3ad5-4fe1-bc35-08028e93986d none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1  /media/disk    ntfs    iocharset=utf8,umask=000  0    0

UUID=771d35fc-1145-4cea-80d8-35529c14d230 /dev/sdc5 ext3 defaults 0 2


fdisk -l:
> 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94ff94ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       46922   376900933+   7  HPFS/NTFS
/dev/sda2           46923       60801   111483067+   f  W95 Ext'd (LBA)
/dev/sda5           46923       59159    98293671   83  Linux
/dev/sda6           59160       60163     8064598+  82  Linux swap / Solaris
/dev/sda7           60164       60801     5124703+   b  W95 FAT32

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8e7bcbfc


I posted these because everytime someone had a question, this is what was asked of them.

Thanks for any help

---

### Post by Bachstelze on 2009-01-18
Try this:

```
sudo fsck /dev/sda7
```

---

### Post by marker5a on 2009-01-18
Thanks Hymn for the quick response... This is what i get... I wasn't sure which option to select

> 
fsck 1.41.3 (12-Oct-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  71:4f/46, 72:53/41, 73:20/54, 74:53/33, 75:48/32, 76:41/00, 77:52/00
  , 78:45/00, 79:20/00, 80:20/00, 81:20/00
1) Copy original to backup
2) Copy backup to original
3) No action
?


---

### Post by Bachstelze on 2009-01-18
Choose 1. It shouldn't matter anyway since the differences are in the boot sector and I don't think you use that partition for booting.

---

### Post by marker5a on 2009-01-18
This is what I got when I selected '1'

Leaving file system unchanged.
/dev/sda7: 11 files, 11/1278673 clusters

I ran sudo fsck /dev/sda7 again after using this option, and it still says there are differences.

---

### Post by Bachstelze on 2009-01-18
Choose 2 then. ;p As I said, it won't matter what you have in the boot sector.

---

### Post by marker5a on 2009-01-18
same response... :(

---

### Post by Bachstelze on 2009-01-18
Hmm, very weird... What if you try to boot Windows?

---

### Post by marker5a on 2009-01-18
Booting into windows works fine without any flaws.  When I booted into windows, I ran chkdsk and this hadnt fixed anything.

---

### Post by mcduck on 2009-01-18
To solve the problem when booting you should change this line:
```
# /dev/sda7
UUID=927F-5972 /osshare vfat utf8,umask=007,gid=46 0 1
```
..into this:
```
# /dev/sda7
UUID=927F-5972 /osshare vfat utf8,umask=007,gid=46 0 2
```
or this:
```
# /dev/sda7
UUID=927F-5972 /osshare vfat utf8,umask=007,gid=46 0 0
```

The last number tells fsck the order in which the partitions are checked. Only root partition should have "1" there, for all other it should be either "2" (to check that partition after root) or "0" (to disable fsck on that partition).

If changing the number to "2" doesn't help, use "0" instead. Since you are dual-booting with Windows you can safely let Windows handle checking of that partition, after all it _is_ a Windows file system..

---

### Post by marker5a on 2009-01-18
editing the fstab didnt have any effect... I tried both 0 and 2... any other suggestions?

Thanks

---

### Post by mcduck on 2009-01-18
> **marker5a said:**
> editing the fstab didnt have any effect... I tried both 0 and 2... any other suggestions?

Thanks

Did you actually restart the machine after editing fstab?

It will not change what happens if you run fsck manually, only what partitions are checked during boot (and in which order"). If you change it to "0" fsck definitely should not even try to check that partition at boot.

Anyway, could you also post the output of "blkid" here, just to check that the UUID's in your fstab are correct.

edit: I spotted one definitely wrong thing in your fstab:
```
UUID=771d35fc-1145-4cea-80d8-35529c14d230 /dev/sdc5 ext3 defaults 0 2
```
That sure isn't correct. You can't mount a device into a device. replace the "/dev/sdc5" here with the directory where you want to mount this partition. (most likely something like "/media/sdc5", you'll have to create the destination directory first)

---

### Post by Bachstelze on 2009-01-18
> **mcduck said:**
> 
edit: I spotted one definitely wrong thing in your fstab:
```
UUID=771d35fc-1145-4cea-80d8-35529c14d230 /dev/sdc5 ext3 defaults 0 2
```
That sure isn't correct. You can't mount a device into a device. replace the "/dev/sdc5" here with the directory where you want to mount this partition. (most likely something like "/media/sdc5", you'll have to create the destination directory first)

I beg your pardon? This line does not appear anywhere in his fstab...

---

### Post by mcduck on 2009-01-18
> **HymnToLife said:**
> I beg your pardon? This line does not appear anywhere in his fstab...

Then the forums are playing strange tricks on me, but that is a direct copypaste from the fstab he posted on the first post of this thread. (the last line in it..)

---

### Post by marker5a on 2009-01-18
I have been restarting the system after each change to the fstab.

Anyways, I changed that line in the fstab, however this still didnt fix anything.
Here is my blkid:
> 
/dev/sda1: UUID="06F008B5F008ACCD" TYPE="ntfs"
/dev/sda5: UUID="771d35fc-1145-4cea-80d8-35529c14d230" TYPE="ext3"
/dev/sda6: TYPE="swap" UUID="af70d5dc-3ad5-4fe1-bc35-08028e93986d"
/dev/sda7: LABEL="OS SHARE" UUID="927F-5972" TYPE="vfat"
/dev/sdb1: UUID="06F008B5F008ACCD" TYPE="ntfs"
/dev/sdc5: UUID="771d35fc-1145-4cea-80d8-35529c14d230" TYPE="ext3"


---

### Post by mcduck on 2009-01-18
Ok, based on that the last entry in fstab isn't actually any use, it's the same as your root partition (which of course is already mounted). Remove that and you'll get rid of one error during boot ("/dev/sda5 is mounted. e2fsck: Cannot continue, aborting.").

It's still interesting that two different partitions have the same UUID, or one partition shows up twice (claiming to be on different disks):
```
/dev/sda5: UUID="771d35fc-1145-4cea-80d8-35529c14d230" TYPE="ext3"
/dev/sdc5: UUID="771d35fc-1145-4cea-80d8-35529c14d230" TYPE="ext3" 
```
Could be result of mounting the partition into /dev directory, so I suppose it's safe to ignore that and just remove the second entry for same partition in fstab.

However that doesn't still explain why fsck would try to check /dev/sda7 even when it's told to _not_ check it. Or why the check fails.

---

### Post by marker5a on 2009-01-18
I removed that last line in fstab... it boots great now.  
When I run sudo fsck /dev/sda7, I still get this.  I really dont care though because the machine boots fine now.

> 
fsck 1.41.3 (12-Oct-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  71:4f/46, 72:53/41, 73:20/54, 74:53/33, 75:48/32, 76:41/00, 77:52/00
  , 78:45/00, 79:20/00, 80:20/00, 81:20/00
1) Copy original to backup
2) Copy backup to original
3) No action
?


I appreciate your help... both of you.  
Thanks again

---

### Post by efalk on 2009-01-18
> **marker5a said:**
> Hello everyone
I am a newbie to ubuntu as well as linux period.  I am receiving an error upon booting up ubuntu and I get the "fsck died with exit status 8" message.  I looked through everything I could find on the internet and havewnt found a solution to my problem.

**CAUTION!**

I upgraded to Hardy last night and had the same problem.  When I looked around, I found out that whatever automated process had converted the /dev/sda* entries in my fstab to UUID entries had fscked up and entered UUID entries that correspond to /dev/sdb

In other words, I am now running off of my backup mirror disk, which is very much NOT what I had in mind.  I have no idea how to untangle this mess, and am very glad I noticed it before my nightly backup script ran.

Do you have more than one drive on your system by any chance?  This could be your problem.

The problems you're experiencing may have come from the fact that you've booted from one drive but mounted another.  Or something like that.

I still haven't figured out how to untangle this mess.

---

### Post by marker5a on 2009-01-18
Actually, I am running two HD's... however, this problem still occured when I unplugged the second drive and just ran off of the first...

---

### Post by efalk on 2009-01-18
> **marker5a said:**
> Actually, I am running two HD's... however, this problem still occured when I unplugged the second drive and just ran off of the first...

Interesting.  But I still suspect a corrupted UUID entry in fstab.

(Aside, Ubuntu was my favorite distro, but this UUID= nonsense, and the glib 1.2 screwup have really tarnished things.)

---

### Post by unutbu on 2009-01-18
Maybe this will help:

[http://www.linuxquestions.org/questions/linux-software-2/utterly-fascinating-boot-sector-problem-differences-offsetoriginalbackup-40214/](http://www.linuxquestions.org/questions/linux-software-2/utterly-fascinating-boot-sector-problem-differences-offsetoriginalbackup-40214/)
[http://www.linuxquestions.org/questions/linux-hardware-18/dosfsck-of-fat32-differences-between-boot-sector-and-its-backup-246949/](http://www.linuxquestions.org/questions/linux-hardware-18/dosfsck-of-fat32-differences-between-boot-sector-and-its-backup-246949/)

Boot from the LiveCD.
```
sudo umount /dev/sda7   # Maybe isn't necessary after booting from LiveCD, but it won't hurt
sudo fsck.vfat -ar /dev/sda7

```

---

### Post by mcduck on 2009-01-18
> **efalk said:**
> **CAUTION!**

I upgraded to Hardy last night and had the same problem.  When I looked around, I found out that whatever automated process had converted the /dev/sda* entries in my fstab to UUID entries had fscked up and entered UUID entries that correspond to /dev/sdb

In other words, I am now running off of my backup mirror disk, which is very much NOT what I had in mind.  I have no idea how to untangle this mess, and am very glad I noticed it before my nightly backup script ran.

Do you have more than one drive on your system by any chance?  This could be your problem.

The problems you're experiencing may have come from the fact that you've booted from one drive but mounted another.  Or something like that.

I still haven't figured out how to untangle this mess.
THe main reason for using UUID's is that they allow pointing to the partition itself, no matter which device name the disk gets.

Your problem should be easily solved simply by running the "blkid" and "sudo fdisk -l"-commands and editing fstab to use the correct UUID's for each partition.

If you can't boot the system, you should still be able to do the required changes sing a live-CD.

(On some hardware the devices are detected in different order on each boot, which means that they get different device names as well. Drive that's known as /dev/sda might become /dev/sdb on next boot. Having removable drives connected during boot make things even more complex. Using UUID instead of device name solves all these problems.)

---

### Post by efalk on 2009-01-18
A little more progress:

My system has three disks.  They used to be hda, sda, and sdb.

Hardy changed them to sda, sdb, sdc.

So in other words, the UUID= entries are correct after all, it's all the other entries that are wrong.  (Including /boot/grub/device.map, which still has the old entries; this may be a problem later)

So my fstab had both

> # Really sdb2, even though the original comment said sda2
UUID=32db6025-9e17-4bc0-b288-7c280368cc59 / ext2 defaults,errors=remount-ro 0 1

and

> /dev/sdb2       /backups        ext2    noauto,errors=remount-ro        0 1

Which could explain why fsck was acting up.  We'll see what happens on the next reboot.

---

### Post by mcduck on 2009-01-18
> **efalk said:**
> A little more progress:

My system has three disks.  They used to be hda, sda, and sdb.

Hardy changed them to sda, sdb, sdc.

So in other words, the UUID= entries are correct after all, it's all the other entries that are wrong.  (Including /boot/grub/device.map, which still has the old entries; this may be a problem later)

So my fstab had both



and



Which could explain why fsck was acting up.  We'll see what happens on the next reboot.

Just remove the extra entries.

The device name change was caused by Ubuntu (and actually most of Linux distributions) changing to use the SATA/SCSI driver for all disks, as it performed better with PATA drives than the actual PATA driver did. Since the driver is same, the devices get same style of names regardless of them being SATA or PATA.

---

### Post by efalk on 2009-01-18
> **mcduck said:**
> Just remove the extra entries.

Actually, I wound up renaming them from sdb to sdc and that fixed everything nicely.  No more fsck problems on boot.

> ... changing to use the SATA/SCSI driver for all disks, as it performed better with PATA drives than the actual PATA driver did....

Having been up to my elbows in the original IDE layer, I can believe it.

---


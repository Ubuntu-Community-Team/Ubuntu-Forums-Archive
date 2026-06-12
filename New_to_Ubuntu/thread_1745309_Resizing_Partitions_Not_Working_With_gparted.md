---
title: "Resizing Partitions Not Working With gparted"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by Kartari on 2011-04-30
New guy to Linux here again.  I found some helpful advice here for resizing partitions, but it's just not working for me.

I have Ubuntu 10.10 and just upgraded my RAM to 8 GB (from 4 GB).  Did this because I'm running Win7 in VirtualBox and want to feed it 4 GB for better performance (4 GB is ideal for Win7 performance).  Anyway, I set up my swap partition to 5.7 GB and would like to up it to 10 GB (1.25x my memory size, more than enough for hibernation).

I tried rebooting from the live CD and running gparted.  It was easy enough for me to see how to shrink the home partition (sda4) by 4.4 GB, then grow the swap partition (sda3) by the same amount.  However, when I click the green checkmark to Apply changes, I get an error and the changes are not applied.  What the exact error is I cannot say; I tried saving details, but they were saved, apparently, to a temporary file system (RAM disk, I'm guessing?) instead of my permanent file system (I could not access my permanent file system from the CD for some reason?!  Just did not appear while I browsed for it).  I read that it's advisable to unmount partitions before resizing them, but there was no "unmount" option to be found.  The one idea I have as to why this might be causing an error is that I am using a RAID 1 (mirroring) array of two hard disks.  I tried setting the flags to "raid" for each partition on each drive (sda and sdb), but I got the same error message.

Not sure what else to try.  Your help is much appreciated, thanks!

---

### Post by mr_luksom on 2011-05-01
Is it possible for you to try the resize in two steps:
1. Reduce the size of the main partition, then Apply.
See if this works.
2. Increase the size of the swap partition, then Apply.

That will narrow down which step is failing. Also, can you write the error down, or post a screenshot? You can use firefox in a liveusb session to do this.

---

### Post by Kartari on 2011-05-02
Hi mr_luksom,

Okay, unstable and strange behavior going on now.  I got a red circle icon with an exclamation point next to sda1, sda2, and sda4, and ditto for sdb1, sdb2, and sdb4.  Right-clicked and clicked Information, and it said something about being unable to read the file system, and needing a certain package that began with "e2" (I forgot the rest).  I simply rebooted, figuring maybe it was a fluke.  Not so... Ubuntu failed to fully boot up this time?!  It asked if I wanted to try or install Ubuntu, I clicked Try, and then watched the cursor animate for ten minutes, then shutdown and started up again.

Third bootup... Ubuntu came on quickly, and I got gparted working with the same red exclamation point warnings/errors once more.  Used & unused space were coming up blank, too.  Setting sda1's "raid" flag on cleared the red exclamation points on all sda partitions, and ditto for sdb, and the used/unused columns were corrected.  For the heck of it, I flagged all four partitions on each disk as "raid."

I tried an identical resize of the /home partition on each disk, figuring maybe gparted wants identical actions on RAID arrays.  No such luck, the error popped up once more.  Here's the error results I got (gparted.html):

> GParted 0.6.2

Libparted 2.3
Move /dev/sda4 to the right and shrink it from 273.21 GiB to 268.91 GiB  00:00:00    ( ERROR )
     	
calibrate /dev/sda4  00:00:00    ( SUCCESS )
     	
path: /dev/sda4
start: 52037632
end: 624998399
size: 572960768 (273.21 GiB)
check file system on /dev/sda4 for errors and (if possible) fix them  00:00:00    ( ERROR )
     	
e2fsck -f -y -v /dev/sda4
     	
Filesystem mounted or opened exclusively by another program?
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda4

========================================
Move /dev/sdb4 to the right and shrink it from 273.21 GiB to 268.91 GiB

========================================

I posted a screenshot for another attempt, this time tried shrinking sda4 by 4.3 GiB and growing sda3 by 4.3 GiB.  gparted.html reported what looks like an identical error.

---

### Post by Hedgehog1 on 2011-05-03
Kartari,

One very possible reason the partition resize attempts are failing is that gparted is finding bad sectors on the disk.  If there are bad sectors in the area you are working, gparted puts things back the way it found it and behaves - well - the way you are seeing.

To verify this, please run the Disk Utility and look at the SMART status of the drive.  You will likely see a message that says "This drive has a few bad sectors".

If this message (or one like it) is what you are seeing, please expect to be replacing the drive before too long.  You will not be able to resize the partitions on a drive with bad sectors.

Once you aquire a new drive that is the same size or larger then your current drive, you can use ddrescue to copy the old drive to the new drive (it copies everything, even Windows and grub).

***The Hedge***

:KS

---

### Post by Kartari on 2011-05-03
Hi Hedgehog1,

The SMART status of all partitions (under Peripheral Devices) and the disks themselves (under SATA Host Adapter) is "Not Supported," when Disk Utility is run either from the installed partitions or from the live CD.  I had to reboot to the live CD to get Disk Utility to perform the Check Filesystem function, because it wouldn't work due to the partitions being mounted.  It reports, "File system is clean" for all ext4 partitions.

I did this on the second reboot actually.  The first one stalled, just like it did last time: never got past the Try Ubuntu/Install Ubuntu screen.

The two mirrored hard disks are both five months old and previously unused... but I know hard disks are a fragile technology.  But it's not giving me the error report you expected, it seems.  Still think it's one or both of the disks, or something else?

Thanks.

---

### Post by Kartari on 2011-05-03
Here's a screenshot of gparted, just ran it again.  It retained the raid flags I set, but the red exclamation points are back, and clicking Information on each partition produces the error message in the screenshot I'm attaching.

---

### Post by srs5694 on 2011-05-03
Do *not* attempt to resize the partitions on /dev/sda using GParted! At least, not if those "raid" flags are accurate. If you somehow coerce the software into making such changes, you'll only have succeeded in damaging your RAID array. I'm not an expert on this topic, but a quick Google turned up [this article](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid) on the topic. You can try Googling yourself if you want more references.

---

### Post by Kartari on 2011-05-04
srs5694,

That was my original suspicion.  I had set the raid flags myself (thinking gparted might need to be told this to work properly), but it is, in fact, a RAID 1 (mirroring) array of two hard disks I am using.

Thank you for the article.  It looks complicated to me, as I am not very familiar with Linux terminal commands yet.  So maybe if gparted really doesn't work with RAID, I'll simply live with a 5.7 GiB swap partition for the time being and, when I have some time in the distant future, will wipe and reinstall everything from scratch.  My system seems to be running smoothly as is, so long as I do not hibertnate...

---


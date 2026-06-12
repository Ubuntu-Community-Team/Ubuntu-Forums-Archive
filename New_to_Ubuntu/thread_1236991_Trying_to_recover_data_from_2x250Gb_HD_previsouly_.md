---
title: "Trying to recover data from 2x250Gb HD previsouly installed in Iomega NAS"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by luiscardoso on 2009-08-10
Hello


I'm trying, for quite some time, to retrieve data from two 250 Gb units that were part of an Iomega NAS (RAID 1).
Professional data retrieval is out of the question.

I checked the drives using western digital software and they appear to be OK.
I suspect that only the NAS motherboard went dead.

I disassemble the NAS and plug one of drives to my pc (using EIDE).
I started my PC using a ubuntu boot cd.
The drive is recognized and, of the 4 partitions inside, I can read the first 2 directly (without mounting them)

The data is inside the XFS partition with 232 Gb.
I also have a partition with 125 Mb with and unknown file system.

Attached you will see a print screen.

After booting, how do I mount this partition to allow me to retrieve the data?
Will I loose data by doing so?

I also have an external hard drive with 1 Tb (NTFS) with data already inside. 
I read something somewhere saying that I also have to mount the external drive to have access to allow me to transfer the files to that drive.

What should I do to gain acess to the partitions and external drives, if possible without loosing much of the data?

Thank you.

LC

---

### Post by unutbu on 2009-08-10
Since you mentioned a priority is to lose as little data as possible, 
I think the first thing you should do is make a clone of your sda4 partition:```


sudo apt-get install gddrescue
sudo ddrescue -r 3 /dev/sda4 /media/usbdrive/image /media/usbdrive/logfile
```

Change /media/usbdrive/ to the correct path to your 1TB drive.

Once you have a clone of sda4, then you could try xfs_check and/or xfs_repair ([http://linux.die.net/man/8/fsck.xfs](http://linux.die.net/man/8/fsck.xfs)). I don't have any experience with xfs filesystems however, so I'm hoping you know how to check and repair xfs filesystems. If not, post a question (or google!) and someone should be able to help you.

Hopefully that is all you'll need to do. However, if that does not work, then there are many "data carving" tools, such as PhotoRec, which can search your drive for files. (Despite its name, PhotoRec can recover many types of files, not just images.)

For details on these data carving tools, see this very informative page:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Good luck, and please let us know if you run into any difficulties and/or how it goes.

---

### Post by luiscardoso on 2009-08-10
Hello

Thank you for your quick reply.

However you did not mention if I need to mount the external hard drive to have access to it.
Attached you can see a print screen.
Do I need to do anything or I'm good to start?

Regards

LC

---

### Post by unutbu on 2009-08-10
First you'll need to use GParted to create a blank partition on the 1TB drive.

It should be at least 233GB in size, since that is the size of sda4.

If the new partition is called /dev/sdbX, then without it being mounted, you can run
```

ddrescue -r3 /dev/sda4 /dev/sdbX logfile
```

(You can provide a path to whereever you wish to save the logfile, so long as it is not on sda4 or sdbX. The logfile is used by ddrescue if the command has to be run more than once.)

---


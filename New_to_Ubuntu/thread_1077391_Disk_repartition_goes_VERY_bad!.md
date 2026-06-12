---
title: "Disk repartition goes VERY bad!"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by taminrob on 2009-02-22
Ok, really need some help and hope this can work.  Let me say now that I posted and received great advice on doing this the right way, that I chose to play the odds on and lost very badly.  I did not have an external drive to use to back up my drive, so rather than go buy one, I just took a chance. :(

Using gparted, I deleted my windows partition, I wanted to have all my drive space for Ubuntu.  That part went great...then against advice, thinking that I would be among the masses who have done this without issue, I resized my partition to take the whole disk with the exception of the 2gig linux swap at the end of the disk.  Things seemed to be going great, at about 87% of the process of copying 48gig of files to the front of the disk (I didnt know it was going to do that or perhaps I would have hesitated) gparted took a dump, said it had an error and died.  I rebooted and found that I cant boot without the live CD, so I did that and opened gparted again, without doing anything, to see my drive partitions.  They show the 48gig at the front of the drive and 68gig unallocated towards the back...it looks like it should have worked, but no luck.
Searched the net and forums and came up with using testdisk, ran it and it freezes at 28% for over an hour, started over and had the same problem but let it run all night, only made it to 35% when I woke up this morning.

Please tell me there is something I can do to recover at least a portion of my files...do I need to use something else, am I using testdisk wrong???

---

### Post by Old *ix Geek on 2009-02-22
Please post the output from this:
```
sudo fdisk -l
```

---

### Post by taminrob on 2009-02-22
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda4               1       14593   117218241    5  Extended
/dev/sda5               1        6197    49769338+  83  Linux
/dev/sda6           14324       14593     2168743+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

this is all the information I have at this time.

I am going to attempt to image my drive to a new external drive and see if that helps...will let you know, but I will certainly appreciate all the help I can get so I know the proper way to go about this

---


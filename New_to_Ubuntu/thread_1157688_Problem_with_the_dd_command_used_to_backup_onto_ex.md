---
title: "Problem with the dd command used to backup onto external HD"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by raj9786 on 2009-05-13
So I tried to dd command to backup my system (i wanted an exact copy of my system). The problem is that i backed it up to an external HD with other data on it that i wanted. i made sure that my partition would fit on the free space on the external drive. Now it seems like all those files are gone. Is there any way to get them back? Im noticing that the free space on the external is listed at 6.2 GB which would have been right if both my old data and my new backup were on it. However I cannot find those old files. Can anyone give me some help? Thanks.

---

### Post by cariboo on 2009-05-13
DD stands for disk duplicate, using it will create an exact image of the hard drive you are cloning. You may want to install the [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") package, and use photorec to recover your files. Testdisk is in the repositories and you can use Add/Remove Programs or Synaptic Package Manager to install it.

---

### Post by lavinog on 2009-05-13
can you post the command you used to backup?

---

### Post by raj9786 on 2009-05-13
Does the testdisk help me recover the files? or is that a different command?

The command i used:

sudo dd if=/dev/sda5 of=/dev/sdc1

where sda5 is my ubuntu partition and sdc1 is my external HD. Thanks for your help.

---

### Post by lavinog on 2009-05-13
installing testdisk will also install photorec. photorec can recover your files. (you will need to run it as super user)

The problem with your dd command is that it would only work for you if there were two partitions on the drive, and the existing data was on the 2nd partition (/dev/sdc2) or higher. If you only had one partition made, you most likely overwrote partition 1 with the ubuntu backup. overwriting a partition like this causes an inconsistancy in the partition tables, and can cause weird reports of free space.

using gparted on the live cd is a good way to backup partitions. Its visual representation of the partition tables helps make sure you do what you want to do.
With gparted you just copy and paste the partition from one drive to the next. It also lets you review what will be done, and simulates the process first to make sure it can be done. DD can hose your system in the first microsecond of operation.

---

### Post by logos34 on 2009-05-13
> **lavinog said:**
> 
The problem with your dd command is that it would only work for you if there were two partitions on the drive, and the existing data was on the 2nd partition (/dev/sdc2) or higher. If you only had one partition made, you most likely overwrote partition 1 with the ubuntu backup. overwriting a partition like this causes an inconsistancy in the partition tables, and can cause weird reports of free space.

 +1 

Yes, sounds like you overwrote the existing parition.

Testdisk should be able to get it back (hopefully)

---

### Post by sir_nasty on 2009-05-13
in the future you may want to download and use partimage, I recently used it to backup to a usb drive and it worked amazingly well, the other upside to it is that it doesn't record free space in the file size and it will compress it and make an image.

---

### Post by raj9786 on 2009-05-13
thanks for your help everyone. so gparted can make a 1:1 backup of my ubuntu partition that can be restored easily?

also is partimage available for jaunty? i tried to find it but i remember not being able to install it. does it support ext4?

---

### Post by logos34 on 2009-05-13
> **raj9786 said:**
> thanks for your help everyone. so gparted can make a 1:1 backup of my ubuntu partition that can be restored easily?

Yes.  The only drawback with gparted copy is it takes up more space (vs. .gz image)

> also is partimage available for jaunty? i tried to find it but i remember not being able to install it. does it support ext4?
> 
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

Warning: Partimage does not support ext4 and btrfs filesystems. If you need an ext4 / btrfs support or if you need modern features (checksumming, multi-thread compression, encryption, flexibility in the size) you should try FSArchiver.

Hmm.  No indication they plan to support ext4 either.

But Clonezilla Live CD supports ext4 --> [Testing (Beta) and Experimental (Ubuntu-based)]("http://clonezilla.org/") versions only

---


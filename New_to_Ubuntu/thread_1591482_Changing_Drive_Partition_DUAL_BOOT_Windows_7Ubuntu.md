---
title: "Changing Drive Partition DUAL BOOT Windows 7/Ubuntu 10.04 already set-up"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by teddymeerkat on 2010-10-09
Hey all, I have already installed Ubuntu 10.04 64-bit alongside Windows 7 Professional 64-bit, but in the install just chose the basic settings. What I would like to do is create a partition for files (especially photos and music) which will be common to both Ubuntu and Windows 7.

As a complete Linux/UNIX noob, but not altogether terrible computer user in general I was wondering how I go about this, what the best way to manage my partitions on my drive is.

I have a single 500 GB drive on a new ACER laptop. I would like to make the common partition at least 200GB big, as realistically most of my files would fall into the categories of photos and music.

Thanks,
Teddy

---

### Post by oldfred on 2010-10-09
You will need to shrink a partition. If you are shrinking your windows partition use the windows tools to do that, otherwise you can use gparted. You will want to add the new partition to fstab to mount it and make it easy to use in Ubuntu. If sharing with windows you need to use NTFS as the format.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I prefer the control manual editing gives, but
Some think it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

---

### Post by irv on 2010-10-09
I did this by shrinking the windows partition and setting up a new NTFS partition and put all my data files I share between the two OS's.
Here is a screen shot from gparted. The sda2 is my windows, and sda4 is my partition for data. I am thinking about making it bigger because I have less that 3Gib free. My arrow is pointing to this data partition.
[ATTACH]171753[/ATTACH]

---

### Post by teddymeerkat on 2010-10-10
OK... so I used GParted to check the status of my drive, and it looks as follows. I don't really mind taking either 100 GB from the Ubuntu (logical) partition or from the "ACER" primary partition. The problem is that I already have all four primary partitions accounted for as Windows 7 requires 3.

So, I am wondering now:

(1) if I resize the Ubuntu partition and use it to create another logical partition in the extended partition do i give it a mount point or not (say "/music")? and will windows recognise it... and equivalently

(2) if I resize the ACER partition can I then move the free space into the extended partition to create another logical partition and if not can I change the ACER partition to an extended partition (if i am allowed more than one) and leave it there.

I know that inside Ubuntu I cannot modify the extended partition I just thought I would take a look without loading the live CD.

Thanks again,
Teddy

---

### Post by Mark Phelps on 2010-10-10
You should probably shrink your Acer partition since there's so much available space there.  But, but sure to do that using the Win7 Disk Management utility.  Do NOT use GParted to do that shrinkage.

You could the boot into the Ubuntu LiveCd and use it to extend the Extended partition to the left to "move" the free space inside that partition.

---


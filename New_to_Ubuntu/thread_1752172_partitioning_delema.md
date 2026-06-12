---
title: "partitioning delema"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by hdmet2011 on 2011-05-07
I pre partitioned my hard drive.  I have a 320gig hd and partitioned it to 270gig for windows vista and a 50gig ubuntu or really close, I couldnt get exact.  I installed ubuntu from a live cd 2 times grub did not work.  Both times I choose which hd for ubuntu.  The second time I created a 4.4 for swap and a 3.? for /boot out of the approx 50gig partition.  The third time I installed Ubuntu I chose to let the installer write over the Ubuntu 11.04 with the new 11.04 and this is what I got out of partitioning:

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1411    11333826    7  HPFS/NTFS
/dev/sda2   *        1412       32994   253687420    7  HPFS/NTFS
/dev/sda4           32994       38914    47549441    5  Extended
/dev/sda5           38100       38380     2245632   83  Linux
/dev/sda6           38380       38914     4286464   82  Linux swap / Solaris
/dev/sda7           32994       37970    39967744   83  Linux
/dev/sda8           37970       38100     1040384   82  Linux swap / Solaris


Now how can I consolidate the /dev/sda5 &7 and the /dev/sda6 & 8?  Also the sda4 I would like to add to sda 5 & 7.  

Anything will help.

---

### Post by madjr on 2011-05-07
sd4 is the extended partition that holds all the other sub/logical partitions.

this guide should help you:
[http://dedoimedo.com/computers/ubuntu-install.html](http://dedoimedo.com/computers/ubuntu-install.html)

---

### Post by sidzen on 2011-05-07
This is what i ended up doing with my first dual-boot of a new laptop --

TOOLS:

Windows Recovery Disk
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
([http://www.techrepublic.com/blog/window-on-windows/creating-a-windows-vista-recovery-cd/622](http://www.techrepublic.com/blog/window-on-windows/creating-a-windows-vista-recovery-cd/622))

EasyBCD
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

GParted
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
---------------------------------------------------------------------------------------------
 
GOAL = to end up with no more than four total partions on the hard drive

METHOD:

Make your Recovery Disk.

Shrink your Windows partition to leave a  least 20% free space, Defragment it.
Copy any Windows Recovery partition to DVD. 

Use GParted Live to --
 
eliminate (delete) any Linux partitions already present, 
plus delete the Windows Recovery Partiton (if applicable) backed up to DVD

    NOTE: one may either leave the Recovery Partition and move it with
    GParted to be adjacent to the C:\ drive, or eliminate it; in either
    case, back it up!

Create one / (root) partition, making it a Primary partition of about 15GB
Create one Extended partition, of 90-95% of Unallocated (leaving a small amount)

Of the Extended partition, make your /home and swap, at least.  Use ext4 for all.

Correct the Boot Manager

Reboot and install Linux of your choice, choosing Manual at Partition section, using
(modify or edit) what partitions created with GParted above.

Use Recovery Disk to boot to Windows and install EasyBCD
If a small (about 200MB) partition is used by Windows as a Boot partition, reformat it
to ntfs using GParted, then Use Recovery Disk to boot to Windows and install EasyBCD.

One should now be able to choose which OS to boot to in "normal" Windows Boot Manager.

---


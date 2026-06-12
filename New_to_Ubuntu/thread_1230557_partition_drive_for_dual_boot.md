---
title: "partition drive for dual boot"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by rcbinwi on 2009-08-03
When I partitioned my drive for dual boot (XP and Ubuntu 9.04) I wanted to partition my 60G drive for 40G XP (C) and 20G Ubuntu (D).  So I made two partitions through XP.  XP installed on the C: partition.  Then I installed Ubuntu using the "next to XP" option.  (I surely don't have the wording right, but I hope it's clear.)

Now when Ubuntu went to update, it said it didn't have enough disk space.  I went to look at my disk manager via XP and noticed that Ubuntu has a tiny slice of hard drive, and is disconnected from the D: partition that I intended it to go into.

Ideally I would like Ubuntu to install in a nice, big partition so that it can expand as it needs to.  At the same time, I would like to be able use the partition in other ways.  In other words, I would like Ubuntu and the rest of the partition to be included together.

How can I fix the problem?  Of course, I would prefer not to reformat the whole drive.  Can I fix what I've already done?  I've included a screen shot of my partitions as of now, if that helps.

---

### Post by jacklinux on 2009-08-03
try instaling via wubi: [http://wubi-installer.org/](http://wubi-installer.org/)
Very simple to use - Also you can set the amout of GB space for ubuntu.

---

### Post by egalvan on 2009-08-03
Can you do a screen shot in Ubuntu, using gparted?

---

### Post by Moop on 2009-08-03
Delete the last 3 partitions and reinstall Ubuntu to the free space. Ubuntu uses a different file system than windows does so creating that 2nd partition using XP wasn't needed. 

The live cd has a disk partitioner you can use to delete and create partitions.

---

### Post by Mark Phelps on 2009-08-03
Looks like what you did initially is accidentally install through Wubi and let it automatically select the amount of space needed.  It did that because you can't install Ubuntu in native mode to MS Windows formatted partitions.

If you want Ubuntu to have its own partition, you must reformat the "D" drive as Ext3.

You will then need to remove the existing Ubuntu installation and reinstall it, selecting the existing Ext3 partition.

---

### Post by rcbinwi on 2009-08-03
> **egalvan said:**
> Can you do a screen shot in Ubuntu, using gparted?

New problem: when I go to use gparted I get the error, "Root privileges are required for running GParted."  When I try to find the partitions via GUI (System>Administration>Partition Editor), I get, "Failed to run /usr/sbin/gparted as user root.  Unable to copy the user's Xauthorization file."

I can't figure out what the problem is here, unfortunately.

---

### Post by jacklinux on 2009-08-03
> **Mark Phelps said:**
> Looks like what you did initially is accidentally install through Wubi and let it automatically select the amount of space needed.  It did that because you can't install Ubuntu in native mode to MS Windows formatted partitions.

If you want Ubuntu to have its own partition, you must reformat the "D" drive as Ext3.

You will then need to remove the existing Ubuntu installation and reinstall it, selecting the existing Ext3 partition.
He can change the alicated GB space in the wubi istaller. i found its much easier

---

### Post by ajgreeny on 2009-08-03
If you really did install with wubi, I would uninstall it using the windows control panel, then install ubuntu again, but this time choose manual when you get to the partitioning part, and choose the empty 20 GB unallocated space.  Click on that and make a new partition of 18GB ext3 for root (/) and a second of 2 GB for swap.  This may sound difficult but have a look at this site for more info.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

[ ]("http://ubuntuforums.org/showthread.php?t=282018")

---

### Post by rcbinwi on 2009-08-03
I didn't use WUBI.  I'll try out what you suggest.  Should I erase the partition via XP first, or just reformat the partition from Ubuntu?

Oops!  I see that XP has not formatted that partition.  How should I format it via Ubuntu?

---

### Post by LewRockwell on 2009-08-03
> **rcbinwi said:**
> I didn't use WUBI.  I'll try out what you suggest.  Should I erase the partition via XP first, or just reformat the partition from Ubuntu?

Oops!  I see that XP has not formatted that partition.  How should I format it via Ubuntu?

You'll use any of a number of LiveCD linux distros that have Gparted to work with your hard drive

There are many dozens of partitioning tutorials at various websites, hundreds of blog and forum threads, and thousands of individual posts relating to anyone and everyone's differing methods and opinions regarding partitioning.

This includes, but is not limited to, considerations like how many primary partitions to create, how many logical partitions to create in an extended partition area, swap partition(s), and the sizes and placement of these and the operating systems and data that will be placed in them.

If you read up and plan ahead before committing to your layout you'll enjoy your system(s) much more in the long-run.

.

---

### Post by ajgreeny on 2009-08-03
> **rcbinwi said:**
> I didn't use WUBI.  I'll try out what you suggest.  Should I erase the partition via XP first, or just reformat the partition from Ubuntu?

Oops!  I see that XP has not formatted that partition.  How should I format it via Ubuntu?
Erase which partition?  Be careful when erasing anything with gparted as you could be in trouble if it's the wrong one. Your screenshot shows a 2.33GB (root?)  and 173MB (swap?) partitions, which if you know nothing about, and they are the ones made in your attempted ubuntu install, you can delete with gparted, when you boot to the live CD.  Gparted will probably show these partitions as ext3 and swap, as I say above, which will prove they are the ubuntu partitions, and the 17.3GB unallocated, judging by what shows in the disk management screenshot.

Once the two small partitions are deleted you will have your 20GB of unallocated space into which you can install ubuntu according to my previous post.  You must choose Manual when you get to the partitioning part if you want to choose partition sizes in this area, or I think you can choose to use the largest unallocated space if you choose to use the guided way.  I always do it manually and have now got a bit rusty on any other method, but see the posts I linked to earlier for more info.

---

### Post by Daniel1994 on 2009-08-03
I had the same problem, but solved it without reinstalling:

 			 			 			 		   		 		1. Boot from the liveCD, and use GParted to remove the unused partion(D)
 
2. Boot onto XP and install a 3 GB wubi

3. Reboot onto the wubi and install GParted

4. Use GParted on wubi to resize the ubuntu(ext3), so that it is twenty GB

5. Boot onto XP and remove wubi

and there you go.:D

---

### Post by rcbinwi on 2009-08-04
From Gparted on the live CD I deleted the D partition on the hard drive.

Now I'm getting:
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 22

I looked up this error elsewhere and am trying to solve that problem before I come back to the instructions recommended in this thread.

Any suggestions for a quick solution?

---

### Post by ajgreeny on 2009-08-04
Why did you delete the D partition and not the two small ones with ubuntu on them?  D appeared to be unallocated space already as it was not shown as formatted space in the disk management screenshot.

You could try Daniel1994's suggestion, but I can't quite see why you need to install ubuntu with wubi to do it, rather than use the live CD.  I still believe that your best way forward is to ignore the wubi way, and to ignore the grub error 22; just follow my post #11, which will give you a space of 20GB for ubuntu and when you install it, a new grub will be put on the MBR of the main windows disk instead of the windows MBR, which is the normal and easiest way to proceed, allowing you to choose which OS to boot from each time you start the machine.  There is no need to use wubi when you can simply run from the live CD to do the partition cleanup, and then install to the space you make.

Incidentally, I would personally only ever use the windows disk management tool to shrink a vista partition, and not bother about it for XP, which does not object to partition management with gparted, a much better partition tool than the windows one.  You will note that the screenshot you gave us does not recognise the partitions of ubuntu at all, and it simply calls them "unknown".

---

### Post by rcbinwi on 2009-08-04
I did it the ajgreeny way with a guided partitioning and it worked this time.  I can now download the updates without Ubuntu telling me the drive is out of space.

I think the problem may have arisen because I originally used a new option for partitioning the drive, something like "install next to XP."  This time I went with the "largest unused space" and it worked.  Since the latter guided option is older and the former is newer, I'm guessing the latter is still buggy.

I haven't had a chance to read all about partitioning, though I've read some.  Next time I will try to learn more about /home partitions and such.

Thanks all!

---

### Post by rcbinwi on 2009-08-04
So now I've reinstalled Ubuntu, and Ubuntu is able to update without running out of space.  When I go to disk manager in XP, though, it looks identical to how it looked in the beginning.

Could it be that my problem was not the partitions after all but just the way Ubuntu installed?

---

### Post by ajgreeny on 2009-08-04
Sorry, no idea about that, but just to check how things are now set up, run ```
sudo fdisk -l
``` in terminal and report the output back here again

---

### Post by egalvan on 2009-08-04
> **rcbinwi said:**
> ...I've reinstalled Ubuntu,... able to update without running out of space.
 When I go to **disk manager in XP,**...,
 it looks identical to how it looked in the beginning.

Could it be that my problem was not the partitions after all but just the way Ubuntu installed?

Windows Disk Manager knows nothing about *nix partitions.

gparted knows VFAT (FAT16/FAT32), NTFS and all manner of *nix partitions.

You are MUCH better off using gparted under Ubuntu.
You will get better info.
Try posting a screenshot with gparted.

---

### Post by rcbinwi on 2009-08-05
Here's what I'm getting.

> Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        4524    36290835    7  HPFS/NTFS
/dev/sda3            4525        7113    20796142+   5  Extended
/dev/sda5            4525        7000    19888438+  83  Linux
/dev/sda6            7001        7113      907641   82  Linux swap / Solaris


It seems to work fine now since Ubuntu seems to access the whole of the Linux drive partition (D).

Any more suggestions?  I'm reading up on how to set up a /home partition in Linux.

---

### Post by ajgreeny on 2009-08-05
OK, now run ```
df -h
``` to see the size and free space on your drives.  All the virtual filesystems will also be listed as well as the actual drives, but the first one should be the hard drive itself, like this
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             128G   43G   80G  35% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  108K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M 1007M     0 100% /dev
tmpfs                1007M   76K 1007M   1% /dev/shm
lrm                  1007M  2.2M 1005M   1% /lib/modules/2.6.28-14-generic/volatile
```

---

### Post by rcbinwi on 2009-08-06
Here's what I get when I run that:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              19G  2.6G   16G  15% /
tmpfs                 497M     0  497M   0% /lib/init/rw
varrun                497M  108K  497M   1% /var/run
varlock               497M     0  497M   0% /var/lock
udev                  497M  144K  497M   1% /dev
tmpfs                 497M  488K  497M   1% /dev/shm
lrm                   497M  2.2M  495M   1% /lib/modules/2.6.28-14-generic/volatile
```
It looks like just the specs on the Ubuntu partition, as I intended to divide the drive ~40G XP, ~20 Ubuntu.

Am I reading this correctly.

Thanks for the help.

---

### Post by ajgreeny on 2009-08-06
Yes, it looks as if you've now got what you wanted.

I'll be interested to see if, like me you start with a small ubuntu partition and gradually increase it to be the main OS of your machine as time goes by.  I started with a partition of 30GB for ubuntu and windows was 120GB.  Now after about 4 years I have 128GB ubuntu and 22Gb windows, and have not booted windows now for about 2 months now.  I did need it for an old paralell port scanner, but a new MFP means a scanner is now available in ubuntu so I might just get rid of windows completely.

---


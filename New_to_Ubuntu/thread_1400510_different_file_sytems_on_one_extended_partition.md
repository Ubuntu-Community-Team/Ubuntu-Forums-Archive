---
title: "different file sytems on one extended partition?"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by Joe Question on 2010-02-07
Hi expert friends, I am trying to switch to Ubuntu and badly need help. My acer timeline 1810t came with windows 7 preinstalled. Alone, it took 3 primary partitions. I installed ubuntu 9.10 64 bit on the 4th extended via pen drive.
I attach the gparted screenshot as it is now, after resizing ext4, and the swap file which were too big. 

And this is what fdisk says:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x75a2b104

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1567    12582912   27  Unknown
/dev/sda2   *        1567        1580      102400    7  HPFS/NTFS
/dev/sda3            1580        7519    47710031+   7  HPFS/NTFS
/dev/sda4            7520       38913   252172305    5  Extended
/dev/sda5            7520       10783    26218048+  83  Linux
/dev/sda6           38381       38903     4200966   82  Linux swap / Solaris

I need to format the unallocated 211 Gib to nfts or fat 32 to creat an archive that both OS can access. 

But I as I tried to format it to fat 32, ubuntu would not boot.

Using the live pen drive took a look with gparted and the swap file mark was black with an exclamation mark by it. 
I had to cancel the fat 32 partition to have ubuntu booting again.  
Maybe I can only choose file systems belonging to linux inside this extended partition?
Thanks in advance for any help

---

### Post by Paqman on 2010-02-07
You can't modify partitions which are in use ("mounted"). When a partition within an extended partition is mounted, the whole extended partition will be locked.

When you use your USB stick, the system automatically mounts any swap partitions it finds (to improve performance). All you need to do is boot up into the USB stick, open Gparted, right click on the swap partition and "swapoff". You should be able to make any changes you want after that.

---

### Post by Howard Roark on 2010-02-07
There are people out there who know a hell of a lot more about this then I do, so take this for what it's worth. Ask around and see if you can get a copy of *Partition Magic*; computer repair shops almost always have this at their disposal. As the name implies it is a quick and easy fix to partitioning problems. Set aside what ever chunk of disk space you want to dedicate to Ubuntu and the issue should be fixed. If you want to do it the hackers way and work from the terminal than disregard what I have to say and listen those people out there who know!
Good Luck
Howard Roark

---

### Post by The Cog on 2010-02-07
You can put any filesystem type you like in an extended partition. One thing that comes to mind is that if you allocate the format the 211G area, it will probably become sda6, and the swap become sda7.

I really can't imagine why Ubuntu wouldn't boot after doing this, I'm afraid. It uses the UUID fingerprint rather than the sda* number to identify partitions these days, so it shouldn't get upset by any renumbering.

So sadly, I can't help with your problem except to say that you should be able to convert that space to fat without problems. 

One way to get it sorted would be to delete the Ubuntu partitions, create the fat partition the size you want, then run the Ubuntu installer and tell it to use the remaining unused disk space. But I dislike that solution because it's defeatist, and doesn't help explain what's wrong now.

---

### Post by oldfred on 2010-02-07
It really should make a new partition sda7. If you edit or make large changes then you may have to reinstall grub and edit fstab to boot because of those changes to partitions.

I would not even consider FAT anymore for storage except for USB keys that may require it. NTFS is the best of the windows compatible file systems.

NTFS and Fat info:
[]("http://technet.microsoft.com/en-us/l.../cc938932.aspx")[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)
max - 4GB minus 2 Bytes

---

### Post by Joe Question on 2010-02-08
One way to get it sorted would be to delete the Ubuntu partitions, create the fat partition the size you want, then run the Ubuntu installer and tell it to use the remaining unused disk space. But I dislike that solution because it's defeatist, and doesn't help explain what's wrong now.[/QUOTE]

Thanks for help. I LOVE defeatist solutions :) I mean, any white flag here, as long as it works... 
On one of my previous attempts to install ubuntu I run g parted from a pen drive and erased any linux related partition, so that all was left were the 3 windows primary partitions. I wanted to create a 4th logical partition in FAT for storing data. However GP didn't let me choose to make a logical partition (options were grayed out). I could only choose to create an extended one. This forces me to have my archive within the extended...

---

### Post by Joe Question on 2010-02-08
Thanks to all, I am nearly there. Here's what happened: I tried to format the unallocated 211 Gib space once again from GP using the USB pen drive, to make sure I did everything right the first time around. Only, this time I choosed NTFS... and ubuntu booted! 
Once booted I could see the new 211 Gib NTFS partition in GParted. Yes, it was sda7. 
However It is unmounted and I don't know how to access it or if I should (and how) assign a mount point to it somehow.

The other thing is that ubuntu now boots just every now and then, let's say once out of 3 times. 

guess it my fstab got messy. 

Here I post it:

[FONT=verdana, helvetica,  sans-serif][SIZE=2][COLOR=#000000][COLOR=#000000][FONT=verdana][SIZE=1]/etc/fstab: static file system information.
#
#   -- This file has been automaticly generated by ntfs-config -- 
#
#  <file system> <mount point>   <type>   <options>       <dump>  <pass>

proc /proc proc  defaults 0 0
# Entry for /dev/sda5 :
UUID=ca64c7ad-6980-4a8a-a06a-b5ed4ab7cc25  / ext4 errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=81489926-fce8-4c91-b969-3d528e2d8aec  none swap sw 0 0
/dev/scd0 /media/cdrom1 udf,iso9660  user,noauto,exec,utf8 0 0[/SIZE]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT]

[QUOTE=oldfred;8789767] If you edit or make large changes then you may have to ... edit fstab to boot because of those changes to partitions.


- How do I do that?

Thanks again.

---

### Post by oldfred on 2010-02-09
If it boots at all the fstab must be ok. One out of three is very strange.
Can you check your logs in system, administration, log file viewer to see if anything gives errors.

Your UUIDs should be correct. to see them:
sudo blkid

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

You have to make a mount point first.

# modify fstab to mount directory
gksudo gedit /etc/fstab
# remount from updated fstab, also will give error message if something is wrong (that might even prevent booting).
sudo mount -a
# mounted list
df -h

this is my entry as I mount it directly into home.
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  

You also can use SDM storage device manager which creates a mount point and edits fstab, but it is better if you understand some of the choices first. See links above.

But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager

---

### Post by Joe Question on 2010-02-09
Thank you sooo much oldfred! 
I looked into the tutorials and there I found also about ntfs configuration tool, which made mounting a piece of cake. It also edited the fstab and the sda7 now mounts on boot.

Fstab:

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=ca64c7ad-6980-4a8a-a06a-b5ed4ab7cc25 / ext4 errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=81489926-fce8-4c91-b969-3d528e2d8aec none swap sw 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda7 /media/Basement ntfs-3g defaults,locale=en_US.UTF-8 0 0
 
 The UUIDs do match to those I see by typing "sudo blkid" but the /dev/sda7 UUID does not appear in fstab. 

As for the logs file viewer, that looks massive. Is there any section in particular I should look at? 

cheers

---

### Post by oldfred on 2010-02-10
In the log files I look for errors or large skips in time which either it takes a long time to process possibly normal or has errors and takes a long time. But anything with a long time is what should be reviewed.

this is from mine but my total time to boot is about 1 minute so I have not researched it and I am not sure if the time issue is with cups-pdf or udev?

eb 10 08:53:08 fred-laptop kernel: [    4.307891] type=1505 audit(1265791963.591:9): operation="profile_load" pid=447 name=/usr/lib/cups/backend/cups-pdf
Feb 10 08:53:08 fred-laptop kernel: [   27.088896] udev: starting version 147

---

### Post by Joe Question on 2010-02-11
Ten booting attempts later...
Ubuntu is becoming more and more fancy... As it finally booted (after trying also in recovery mode) I accessed the log file viewer (I attach it) and it seems I always get messages like "invalid CHS sector 0".
I started thinking there was some bad sector on my hard drive, but run the disk check from my live pen drive, and it seems ok. By googling "invalid CHS sector 0" I found that it might also be a bug in ubuntu 9.10 or an incompatibility issue with some hard drives (but the discussion was too technical for my knowledge). If so, hope everything gets ironed out with the next release. 

I also get many messages like "unable to read EDID block". 

When trying to boot in recovery mode (see picture), I also got an alert warning that the dev referring to the UUID of my sda5 (root) didn't exist.

The more I get into the booting problem, the more I think it has nothing to do with having different filesystems in the same extended partition, as I initially thought. I was probably mislead by the fact that on one of my previous installs, ubuntu was booting almost fine (80% of times) altought I didn't test it longtime. Then I made the new fat 32 partition and it never booted again (but tried only 4-5 times), so I erased and reinstalled everything. Now I think the "decent" boot record was just a matter of luck. Still, booting time was too slow anyway, which suggests the problems were already there. 

1 minute for booting seems a wonder to me. On my pc, even WHEN ubuntu boots (it's like hitting the jackpot) it takes some 3-4 mins at its best.   
Basically, there's no difference in time between booting from usb or from hard drive.

---

### Post by Joe Question on 2010-02-12
ok, solved. Apparently. Some more testing and i'll be back to explain what happened.

---

### Post by Joe Question on 2010-02-12
Ok, let's say partly solved.

Googling around I realized many people experienced the same "invalid CHS sector" message and it may be a bug in ubuntu 9.10 (support issue with some hdd) whereas 8.04 woldn't give the same problem.

One guy wrote that he installed xubuntu instead of ubuntu and it got better. So, once in ubuntu  I installed xubuntu from the terminal
 "sudo aptitude install xubuntu-desktop" (make sure you're connected). 
Rebooted but nothing booted (same alert message posted before, saying my root drive didn't exist) and the BusyBox v1.13.3. message 
So turned off and fixed grub manually following this very nice instructions:

[http://computergyan.wordpress.com/2009/12/31/solving-the-busybox-black-screen-problem-in-grub2ubuntu9-10/](http://computergyan.wordpress.com/2009/12/31/solving-the-busybox-black-screen-problem-in-grub2ubuntu9-10/)

Xubuntu booted and kept booting 90% of times. Hooray!
No Idea why xubuntu should be booting better than ubuntu as they share the same core. 
If I get into the log viewer I still see the same error messages, but at least the whole thing works now.

Maybe it is just because I fixed the grub problem, but then I can't explain this: I tried to install ubuntu 4 times beforehand and it never booted properly. And each time it reinstalled grub. Was it corrupted all the time? Mhhh...

So, now I can survive till the next release, hoping for the better.   
Also, also all the partitions are perfectly mounted and visible. 

Changing this thread into solved (somehow).

Personal note: I much prefer xubuntu as it is way more snappy than ubuntu...

---

### Post by Joe Question on 2010-02-17
One last update for Acer Timeline 1810T/TZ owners, all my problems were solved by changing the bios sata settings to ide (it's in the main tab).

Ubuntu would load in less than a minute. 
To load both ubuntu and windows without changing these settings everytime, it might help to update to the latest bios.

---


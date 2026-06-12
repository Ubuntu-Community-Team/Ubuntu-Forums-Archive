---
title: "Ext4 in ubuntu"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Duskao on 2009-04-28
Hello everybody! 
I installed ubuntu 9.04 64 bit, and really like it. I have heard about Ext4 and that it can be a fair amount faster then Ext3, how can I upgrade to Ext4? If I had known about it when I first installed U 9.04 I would have done it, but it's a bit too late for that. I do have the Live Disc for 9.04 if it is needed. Please a bit of a walkthough. Thanks!!!

(does anybody else think of Dr. Nick when they hear or read "Hello Everybody"?)

---

### Post by skymera on 2009-04-28
You need to reinstall if you want to use EXT4.

When partition manager comes up on install, choose manual.
There you can select your filesystem :)

---

### Post by wizard10000 on 2009-04-28
> **Duskao said:**
> Hello everybody! 
I installed ubuntu 9.04 64 bit, and really like it. I have heard about Ext4 and that it can be a fair amount faster then Ext3, how can I upgrade to Ext4? If I had known about it when I first installed U 9.04 I would have done it, but it's a bit too late for that. I do have the Live Disc for 9.04 if it is needed. Please a bit of a walkthough. Thanks!!!

(does anybody else think of Dr. Nick when they hear or read "Hello Everybody"?)

Here's how to convert from ext3 to ext4.  Be sure to back up your data first -

[http://www.cyberciti.biz/tips/linux-convert-ext3-to-ext4-file-system.html](http://www.cyberciti.biz/tips/linux-convert-ext3-to-ext4-file-system.html)

---

### Post by skymera on 2009-04-28
> **wizard10000 said:**
> Here's how to convert from ext3 to ext4.  Be sure to back up your data first -

[http://www.cyberciti.biz/tips/linux-convert-ext3-to-ext4-file-system.html](http://www.cyberciti.biz/tips/linux-convert-ext3-to-ext4-file-system.html)

That broke my Debian EXT3 hard.

So i suggest a fresh install to keep problems to a minimum

---

### Post by Peter09 on 2009-04-28
Hi,
this is more of a query to skymera than an answer, but I have read that changing the mount description in /etc/fstab from ext3 to ext4 for the system disk will mean that new files are written as ext4. I have done this on all of my systems with no problems.

My guess is that speed up will be less, but improving, as old files are removed/overwritten.

Has anyone any comment on this?

---

### Post by wizard10000 on 2009-04-28
> **skymera said:**
> That broke my Debian EXT3 hard.

I'll bet it did  :)

---

### Post by wizard10000 on 2009-04-28
> **Peter09 said:**
> Hi,
this is more of a query to skymera than an answer, but I have read that changing the mount description in /etc/fstab from ext3 to ext4 for the system disk will mean that new files are written as ext4. I have done this on all of my systems with no problems.

My guess is that speed up will be less, but improving, as old files are removed/overwritten.

Has anyone any comment on this?

I'm afraid that's not correct - tune2fs and fsck need to be run to convert a filesystem from ext3 to ext4.  Since ext4 is backwards-compatible with ext3 I'm guessing you're running an ext3 filesystem with an ext4 entry in fstab, which should mount just fine.

Normally you can tell what filesystem is mounted by just using 'mount' with no parameters but I think that might get some of its information from fstab and I'm not sure the information you get will be accurate.

The way to tell for sure would be to run gparted from a live CD on an unmounted partition.

---

### Post by Peter09 on 2009-04-28
Yeah, in a way I suspected as much. Next time I have a LiveCD handy I'll do that. I do wonder though what happens when a new file is written, does the driver actually say .... mmmm I'll not write this as ext4 ..... I'll use ext3 because ....  (what criteria)

Sorry, that was not expressed very well :)

---

### Post by wizard10000 on 2009-04-28
> **Peter09 said:**
> I do wonder though what happens when a new file is written, does the driver actually say .... mmmm I'll not write this as ext4 ..... I'll use ext3 because ....  (what criteria)

Sorry, that was not expressed very well :)

I think it was expressed fine :)

What happens is the driver says "I'll not write this as ext4 because the filesystem doesn't support ext4 attributes - I'll try ext3 instead."

---

### Post by binbash on 2009-04-28
Since you newly installed 9.04 i suggest a new install with ext4 instead of converting it.

---

### Post by mhh91 on 2009-04-28
okay,and what if i want to convert an ext3 partition-not the one with ubuntu on it-is it really worth it?

---

### Post by wizard10000 on 2009-04-28
> **mhh91 said:**
> okay,and what if i want to convert an ext3 partition-not the one with ubuntu on it-is it really worth it?

I'd vote no.

I'm running ext4 partitions - I had a good backup of /home before I started so I just wiped the drive, formatted everything ext4 and restored /home from backup.

Running simple hdparm benchmarks I really can't see much of a difference but I will say that deleting large files or lots of files seems to be a fair bit quicker.

If you've got a good backup of home (and I usually back up /etc as well) then I'd clean install rather than messing with converting the filesystem.

---

### Post by hesjnet on 2009-04-28
has anything been done with the data-loss reports on ext4 partitions?

---

### Post by Sef on 2009-04-28
> I'm running ext4 partitions - I had a good backup of /home before I started so I just wiped the drive, formatted everything ext4 and restored /home from backup.

Boot up is much quicker with ext4.

---

### Post by theozzlives on 2009-04-28
That'd be like (if you could) changing FAT32 to NTFS in Disk Management, it won't work. You can just re-install the / partition and leave /home Ext3... You'll keep your files but your OS is Ext4. I did that on one computer. You'll still notice a speed increase.

If you don't have a seperate /home, check out [here.]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")

---

### Post by wizard10000 on 2009-04-28
> **theozzlives said:**
> That'd be like (if you could) changing FAT32 to NTFS in Disk Management, it won't work. 

Huh?

You can't convert it from within disk management but you certainly can convert a FAT32 filesystem to NTFS from within Windows.

convert c: fs:ntfs

will do the deed.

:D

---

### Post by Duskao on 2009-04-28
Thanks a bunch guys. Great amounts of info.

---

### Post by whoop on 2009-04-29
I converted ext3 to ext4 after I made a jump from intrepid to jaunty... No problems for me, here's the howto: [http://ubuntuforums.org/showthread.php?t=1118295](http://ubuntuforums.org/showthread.php?t=1118295)

---

### Post by Saghaulor on 2009-04-29
> **Duskao said:**
> Hello everybody! 
I installed ubuntu 9.04 64 bit, and really like it. I have heard about Ext4 and that it can be a fair amount faster then Ext3, how can I upgrade to Ext4? If I had known about it when I first installed U 9.04 I would have done it, but it's a bit too late for that. I do have the Live Disc for 9.04 if it is needed. Please a bit of a walkthough. Thanks!!!

(does anybody else think of Dr. Nick when they hear or read "Hello Everybody"?)

I'm using ext4 with Jaunty. It's a helluva lot faster than my ext3 with Intrepid, or at least I mean the boot is faster.

I'm not sure if that's the ext4 or Jaunty. I've read that there was performance gains at boot with Jaunty.

I personally like to start clean, no conversions. You risk breaking stuff. I would recommend copying your data and then scrapping everything and starting fresh.

---

### Post by Jack Shankle on 2009-04-29
All this sounds fine and good but nobody talks about upgrading because
they have data that they can't loose from a new install. I have data from Firefox and Thunderbird that I can't loose and don't know how to save it and put it back in the correct place in the new install. So I will be out 
of luck on the next upgrade.

---

### Post by whoop on 2009-04-29
> **Jack Shankle said:**
> All this sounds fine and good but nobody talks about upgrading because
they have data that they can't loose from a new install. I have data from Firefox and Thunderbird that I can't loose and don't know how to save it and put it back in the correct place in the new install. So I will be out 
of luck on the next upgrade.

I did an upgrade from intrepid ext3, to jaunty and then converted the file system to ext4. I did backup my important data (as I do with every upgrade), the upgrade as well as the conversion kept all of my data safe and functional.

HOTWO convert ext3 to ext4: [http://ubuntuforums.org/showthread.php?t=1118295](http://ubuntuforums.org/showthread.php?t=1118295)

---

### Post by The Cog on 2009-04-29
I just had to reinstall today, after the second hard lockup in 5 days. Both lockups happened during heavy disk activity. As a result, I have decided to revert from ext4 back to my previous filesystem, JFS.

First lockup, I was had just reatored a large tar file to /opt. Immediately after the restore finished, I looked and saw that I had restored (amongst other things) two different versions of the Sun JDK. So I immediately did **rm -rf** on one. The PC locked up before the rm finished. No apparent damage after a reboot.

Second lockup was towards the end of a package install in synaptic. After a reboot, snaptic was unable to install or remove anything because of failures in post-install and pre-remove scripts. So I had to reinstall the whole thing.

I have no direct proof but I have a "feeling" that the problem is probably in the ext4 driver. I would be interested to hear if anyone else has started having unexpected freezes.

---

### Post by NightwishFan on 2009-04-29
I have not had any problems. I copied about 50 gb of data from my data partition to my home partition, converted the data partition to ext4, and moved all the files back. Took about 30 minutes (each way, about 20mb/s) and no crashes.

---


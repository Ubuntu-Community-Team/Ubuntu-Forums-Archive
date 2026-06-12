---
title: "Installing 10.10 alongside XP - Partitioning/Resizing Help!"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by AnjanaSofia on 2010-11-16
(As a disclaimer I'm totally new to Linux and Ubuntu.)

I'm trying to install Ubuntu 10.10 alongside the already-installed XP on my Asus eee pc 1005HA. I don't want XP taking up very much space, so I want to shrink the C: drive partition with XP on it, which is now about 72GB with almost 23GB used, to 30 or maybe 35GB to be on the safe side.  

So here's my issue: after defragging again and again, the partition with XP on it still looks like the attached picture; after a bunch of free space there's some file(s) left way out on the right side.

I've seen people say stuff like this in other threads:

Quote:
Originally Posted by Jerry N  
I don't think it has been mentioned but if you want to resize an NTFS partition containing Win XP and you want to continue using XP, it is imperative that you run your Windows defragmenter, preferably more than once. You should then start defragment again and note where the last used sectors are located on your hard drive, ie at 50%, 75%. You can then boot up one of the partition editor programs and resize the NTFS partition but **don't make it so small that you delete the last used sectors noted above**. 
Jerry

It looks like the last used sectors are past the 50% mark, so if I try to resize it to, say 35GB (<50%), will it delete those out-there files and screw things up?

Is there a way to move those stupid files closer to the beginning so I can shrink this partition? If I manually adjust partitions in the installer and tell it to shrink that partition to, say 35GB, will it move the files left before shrinking, or will it just delete them?

Incidentally the XP disk management utility won't allow me to shrink the C: drive. I've heard that gparted can do this, but I've also heard the opposite, and I'd rather not screw things up and have to restore XP from CD. 

Any suggestions??? Thanks in advance.

---

### Post by mcduck on 2010-11-16
Try booting windows into recovery mode and running defrag there. It can't move files that are in use, and running in recovery mode stops most of the background stuff from running allowing defrag to do a better job.

And yes, GParted and Ubuntu's installer both do a great job at resizing Windows partitions. But same as with any partition editing, you should always have a backup. Well, you should really *always* have a backup, no matter what you do. :D

---

### Post by oldfred on 2010-11-16
Gparted works fine with XP. It is just with Vista or 7 that it is better to use the windows tools to resize the windows partition.

Some have said with gparted it will move everything securely, so even running defrag is not required, although I have always run it twice. I think it then makes the resize quicker also.

Always have good backups. And after resizing windows, boot windows. It often wants to run chkdsk or other repairs to reset to its new size.

The new installer in Maverick is a little more confusing. Some have picked side by side but somehow still overwritten entire drive. I always partition with gparted from Ubuntu liveCD or gparted liveCD in advance and use manual install. 

Some examples of installs:
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by AnjanaSofia on 2010-11-16
Thanks mcduck - 

I rebooted in safe mode (is that different from "recovery mode"?) and tried defragging a few times, but nothing changed...

any other ideas?  :)


P.S. I have backed up all my files, I just really don't want to have to restore XP because the eee PC doesn't have an optical drive, so to use the recovery DVD I have to get an external DVD drive. (Thanks Asus, totally brilliant to send a DVD with a machine that can't play one.)

---

### Post by AnjanaSofia on 2010-11-16
Thanks oldfred.

So if I run gparted from the live USB (before installing), resize the partition with XP on it, reboot XP, and then install, it should work?

---

### Post by oldfred on 2010-11-16
Yes that should work. Just be careful if you use the side by side. I have not used it but some seem to have issues. 

Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

I did use Ubuntu with just root & swap for a couple of years but I also added a shared NTFS partition. I do not recommend directly writing into foreign systems. I only write into my XP if I have to make repairs. If you want a shared partition you can either do it before or after but the installer does not let you create a NTFS partition. If you are going to put most of your data into a shared partition then /home does not have to be as large.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Everyone has different opinions on partitioning, several more, but I do not agree with separate /boot or /grub partition now with grub2:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

---

### Post by AnjanaSofia on 2011-04-10
Oldfred, I know I'm many months late, but thank you so much for all the advice!

I got distracted from my linux installation project for a while, but I'm back in the swing of it, and I've learned a lot about partitioning and filesystems in the process!

Gparted on the ubuntu live USB worked like a dream at shrinking my NTFS partition with Windows XP on it. Now I've got a bunch of leftover disk space and I'm trying to follow oldfred's advice on what to do with it...

I've read more posts/discussions about this than I probably should need to, but I'm still hung up on what to do about shared data partition.

The general consensus seems to be that NTFS is the best option for a shared partition, but [_psychocats' partitioning guide_]("http://www.psychocats.net/ubuntu/partitioning") got me thinking that maybe ext3, not NTFS, is the way to go, with an installation of the [_Ext2(3) Installable File System For Windows_]("http://www.fs-driver.org").

I'm thinking ext3 because once I fully install ubuntu,  that's what I'll be working in most of the time, and will only occasionally need to boot into Windows to do something that I can't figure out in linux. I gather that Windows doesn't handle ext2/3 perfectly, but adequately, and if I'm mostly accessing the partition from ubuntu it seems to make more sense to use the system that linux handles best, no?

Opinions?

---


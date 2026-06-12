---
title: "Not Enough Disc Space Available"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by Sandwiches on 2009-05-26
Hi all.  First time Ubuntu user here (first full day :p).

Now, as I'm getting used to the new environment (dual booting Ubuntu 9.04 with Vista), I've come across an issue.

I have a 640 GB hard drive, and I only used about 300 GB or so while on Windows.  Update manager on Ubuntu has come up and alerted me that I have updates that total 46.1 MB to install.  However, I apparently don't have the free disc space to do this.

Does Linux partition itself with very little space?  How can I get more/where did the space go?

Please come down to a very low level.  My understanding of computers is pretty good (I built the one I'm on right now), but my Linux knowledge is much more limited.  I fit the "absolute" part of the forum's name pretty darn well.

---

### Post by halitech on 2009-05-26
open a terminal and post the results of
```
sudo df -h
```
also
```
sudo fdisk -l
```

did you create partitions manually or let Ubuntu set them up for you?

---

### Post by Sandwiches on 2009-05-26
For the first one:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G     0 100% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  104K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  148K  2.0G   1% /dev
tmpfs                 2.0G   84K  2.0G   1% /dev/shm
lrm                   2.0G  2.7M  2.0G   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
/dev/sr0              697M  697M     0 100% /media/cdrom0

For the second:

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ded8c0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       77500   622517726    7  HPFS/NTFS
/dev/sda2           77501       77825     2610562+   5  Extended
/dev/sda5           77501       77803     2433816   83  Linux
/dev/sda6           77804       77825      176683+  82  Linux swap / Solaris

I let it set the partitions on its own, as it was labeled "advanced."

---

### Post by zobcat on 2009-05-26
It seems like you may have allocated too little space to your ubuntu partition when you set it up. You had Windows installed first?

If so, and Windows isn't taking up all of its own partition, then you can:

1. Open Applications > Accessories > Terminal

Copy and paste this code into terminal:
```
sudo apt-get install gparted
```

2. After it finishes installing go to System > Administration > Partition Editor

3. Now, you may be able to Resize your partitions here. If not, then you'll need to download the Gparted LiveCD, [here]("http://sourceforge.net/project/downloading.php?group_id=115843&filename=gparted-live-0.4.5-2.iso&a=43520096"). With this LiveCD, you'll need to burn the image to a cd and boot from it (the same way you installed ubuntu, most likely). 

Good luck!

---

### Post by halitech on 2009-05-26
[color="red"]/dev/sda5 2.3G 2.2G 0 100% /[/color]

looks like you installed on a 2.3gig partition and yeah, its full

---

### Post by Sandwiches on 2009-05-26
Makes sense that it'd be full.  How do I go about changing the partition's size?

If I'd need to reinstall Ubuntu, it wouldn't be the end of the world, as I wouldn't lose much.

---

### Post by halitech on 2009-05-26
> **zobcat said:**
> It seems like you may have allocated too little space to your ubuntu partition when you set it up. You had Windows installed first?

If so, and Windows isn't taking up all of its own partition, then you can:

1. Open Applications > Accessories > Terminal

Copy and paste this code into terminal:
```
sudo apt-get install gparted
```

2. After it finishes installing go to System > Administration > Partition Editor

3. Now, you may be able to Resize your partitions here. If not, then you'll need to download the Gparted LiveCD, [here]("http://sourceforge.net/project/downloading.php?group_id=115843&filename=gparted-live-0.4.5-2.iso&a=43520096"). With this LiveCD, you'll need to burn the image to a cd and boot from it (the same way you installed ubuntu, most likely). 

Good luck!

they can repartition the windows partition using gparted but they can't resize or do anything to the Ubuntu partition if its mounted so I would suggest booting into windows, defrag the drive at least twice then use the windows tools to resize the space (give it at least 5gig) then reinstall.

---

### Post by zobcat on 2009-05-26
Ah, that's right. Forgot about the "being mounted" part, and that Vista has a pretty good partition editor. :KS

---

### Post by lisati on 2009-05-26
> **zobcat said:**
> Ah, that's right. Forgot about the "being mounted" part, and that Vista has a pretty good partition editor. :KS

Doesn't always work: when I wanted to reorganize the partitions on my laptop which came with Vista, its partition editor didn't want to resize the main Vista partition. I ended up useing gparted on an Ubuntu LiveCD. I think I've seen other threads touching on similar in the forums.

---

### Post by Sandwiches on 2009-05-26
OK, I did the first step, but I can't access the partitions.  I tried to enter Windows, but after I select it from the boot menu and a fancy screen comes up, nothing happens.

Help!  How can I boot into Windows?

---

### Post by lisati on 2009-05-26
> **Sandwiches said:**
> OK, I did the first step, but I can't access the partitions.  I tried to enter Windows, but after I select it from the boot menu and a fancy screen comes up, nothing happens.

Help!  How can I boot into Windows?

If you've already resized your partitions, Windows will probably want to do a "CHKDSK" (where it scans your disks) and then restart. Is this what you're getting?

---

### Post by Sandwiches on 2009-05-26
No, I haven't been able to resize partitions.  I did the line in the terminal, but I was unable to resize partitions due to it being mounted and unable to be unmounted.  So, I restarted and tried to log into Windows, but I can't.

---

### Post by zobcat on 2009-05-26
Have you ever booted into Windows since installing Ubuntu?

---

### Post by Sandwiches on 2009-05-26
No, I've been getting acquainted to it since install.  Have not booted into Windows since before the install.

---

### Post by zobcat on 2009-05-26
Welcome to the second layer of your troubleshooting experience. You've got a completely new, totally unrelated problem.

Let me see if I can find a solution for you.

---

### Post by Sandwiches on 2009-05-26
New development: I left it trying to enter Windows for 15 minutes or so; it rebooted itself and then worked.  I think I'm just going to uninstall Ubuntu for a few months and try this again when I have more time (please don't try to talk me out of this.  I really liked what I tried, but now's not the time).  Am I correct in understanding that I need to put in my Vista disc and use the fixmbr function?

---

### Post by mrbiggbrain on 2009-05-26
Iv seen alot of people come unprepared when they tackle complex issues like dual booting, i find the following are a requirment!

Gparted (latest version) live CD/DVD
Vista Recovery Console DVD (not the install, ms offers a free version online w/ just the recovery tools)
if u have XP, the XP install cd (oem, or retail)
A linux Live cd/dvd (i find puppy or slax are two lightweight and good ones.)


Gparted can resize the partitons, note that this does take forever, and i have had the process fail on me quite a bit. also note that resizeing is dangerous, i have used gparted quite a bit, find it reliable, and have used every last operation it offers.... but it can fail... not saying it will.

Vista cd/dvd is good becuse it allows full vista chkdsk /r well the disk is unmounted. it can also reload the bootloader, repair brocken files, or even fix the MBR (master boot record) it is imho something every vista user needs!

The xp cd has the same functions for xp, over vista. 

the live cd/dvd allows you to access the internet, check files, and do other general linux commands/checking.

having those things will make creating and maintaining a multi-boot verry easy.


note, when i say fail, i mean that gparted says it cant do it, not disk damage or data loss...

---

### Post by Didius Falco on 2009-05-26
> **Sandwiches said:**
> New development: I left it trying to enter Windows for 15 minutes or so; it rebooted itself and then worked.  I think I'm just going to uninstall Ubuntu for a few months and try this again when I have more time (please don't try to talk me out of this.  I really liked what I tried, but now's not the time).  Am I correct in understanding that I need to put in my Vista disc and use the fixmbr function?

Yes that will work to get you booting directly back into Windows.

You can then use the Vista partitioning utility to delete or reformat your Ubuntu partition, if you want to reclaim that space.

Regards,

Didius

---

### Post by raymondh on 2009-05-26
> **Sandwiches said:**
> New development: I left it trying to enter Windows for 15 minutes or so; it rebooted itself and then worked.  I think I'm just going to uninstall Ubuntu for a few months and try this again when I have more time (please don't try to talk me out of this.  I really liked what I tried, but now's not the time).  Am I correct in understanding that I need to put in my Vista disc and use the fixmbr function?

Hello sandwiches,

If that is your decision, so be it.

1.  In Vista, you have the disk management tool which you can use to delete ubuntu, keep the deleted partition unallocated and then resize the Vista partition (in that order as you can only resize expanding to the right).
2.  Then, shut down (or restart) and boot into the Vista Install Disc.  You will have to select language > repair computer > command prompt > type

bootrec.exe/FixMbr

If that gives a success message, type exit > take out Vista disc and try a restart.

If no go, repeat the Vista disc boot and at command prompt type

bootrec.exe/FixBoot
bootrec.exe/FixMbr

and then exit.

Oh, defrag after as well.

Some links as guides

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Good luck and Ubuntu (and the Forum) will be here welcoming you when you decide to come back.

Regards,

---

### Post by Sandwiches on 2009-05-26
I want to thank you all for being very helpful :D.  I think I'll be back on one of my other computers ;).  I'm pretty darn impressed at how well it scales for lower-end machines, and how helpful (and fast!) the community is.

One final question: FixMbr was a success.  Now when I boot up, there are only two options: Vista and plain Ubuntu (before, there were two Ubuntus with numbers, one was a recovery).  Can I delete the partitions with Ubuntu to make the choice go away?

---

### Post by bennachie on 2009-05-26
I can appreciate your caution, but you can continue to explore Ubuntu to your heart's content while remaining "safely" within a Vista environment (the quotation marks have been inserted because I entirely endorse the comments made by a previous contributor about the value of the Vista Recovery CD). 

Once you are satisfied that Vista is running just as you wish, insert the Ubuntu LiveCD, and choose the option to "install within Windows" using a very clever piece of software called Wubi. Select a decent-sized block of space for the installation to give you plenty headroom. Around 25GB will allow for lots of music, videos, documents etc. 

Don't be alarmed by the various subsequent messages implying that real partitioning may be going on. In effect, Ubuntu is being installed as a normal application within Windows, except that the application reserves a fixed block of space within the normal NTFS Windows partition. You can later uninstall Ubuntu at any time using the standard Vista mechanism.

This all works very well indeed, with only a small (much less than 10%) performance hit on Ubuntu (Vista applications are unaffected) as compared with a true dual-boot situation.

Give it a go once the dust has settled. You will be impressed. The same trick works with Linux Mint, which is based on Ubuntu, and you might like to try that as well at some stage.

---

### Post by Sandwiches on 2009-05-26
I will do that next time (I know you guys are right, but I'm currently in knee-jerk state and just want to be comfortable until this summer when I can really get my hands dirty.  I am looking forward to ditching my anti-virus).  But right now I need to clean up the partitions.

Here are the three partitions:
[[IMG]http://img37.imageshack.us/img37/3455/partitionsm.jpg[/IMG]](http://img37.imageshack.us/img37/3455/partitionsm.jpg)
Click for full size if it's too big.

I had no partitions when I installed Ubuntu.  The two little ones are the one's to remove?  And out of curiosity, why did it make two?

---

### Post by Didius Falco on 2009-05-26
Yes, those are the two to delete.

The littler of the two would be your Linux Swap partition. You can use a swap file, but a separate swap partition is the better option, so the installer defaults to that whenever possible.

Regards,

Didius

---

### Post by brimorse on 2009-07-07
Great thread!  Thank you Sandwiches and all who contributed.  I have the exact same thing going on with my new Ubuntu install, but haven't tried the fixes yet.
 
I too allowed Ubuntu to size its own partition- not an option I would recommend to those who are looking to do their first install.
 
Will post feedback once I try the fixes detailed here.

---

### Post by brimorse on 2009-07-07
Ok- so I got Gparted installed and running.  How do I actually change the partition sizes?  How big should the Ubuntu partition be?

---

### Post by raymondh on 2009-07-07
> **brimorse said:**
> Ok- so I got Gparted installed and running.  How do I actually change the partition sizes?  How big should the Ubuntu partition be?

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Using gparted, click on the partition you wish to resize to highlight it > Partition > Resize.

If you wish to resize Vista, kindly defrag Vista first.  Also,  use the built-in Vista Disc Management Tool to resize Vista/windows partitions.  Sure, you can use gparted ... but Vista's tool seems to work better on a Vista partition.

Reference the first post on this link .... posted by CMDR.

[http://gparted-forum.surf4.info/viewtopic.php?id=2892](http://gparted-forum.surf4.info/viewtopic.php?id=2892)

As for Ubuntu size ... it really depends on what you plan to do and how much you can afford to give.  Most give Ubuntu (root) a minimum between 8-15GB.  Then, there's SWAP which is OK at about 1.5GB.  Then, if you wish, you can make a separate /home partition (which stores your files, settings, tweaks, etc) and that can be "as much as you want it to be".  I have given my ubuntu (full-time use system with a bunch of apps already) 300GB and have stored a bunch of data and media (about 80hrs worth of HD Home videos at 2GB per video) and still have about 120GB remaining.   

Good luck.

---

### Post by brimorse on 2009-07-08
Ok- used the Vista disk management tool, and it came up with another 70 GB of free space.
 
So I go to Ubuntu and open the partition manager- I can see the free space but can't figure out how to merge it with the existing Ubuntu partition.  I don't have the option to mount it to /home.
 
Thinking I will download and try the Gparted Live trick...

---

### Post by carml on 2009-07-08
If that space is unallocated you can move the border of your Ubuntu partition to include all the free space,use Gparted Live or a Live cd of Ubuntu in order to do that.

---

### Post by raymondh on 2009-07-08
> **brimorse said:**
> Ok- used the Vista disk management tool, and it came up with another 70 GB of free space.
 
So I go to Ubuntu and open the partition manager- I can see the free space but can't figure out how to merge it with the existing Ubuntu partition.  I don't have the option to mount it to /home.
 
Thinking I will download and try the Gparted Live trick...

Hello Brimorse,


Gparted will not work on a partition that is mounted.  If you accessed gparted thru your ubuntu install, then that partition is in use (aka mounted).  You can use the liveCD and in live session ("try without any chnages") which will auto unmount.  Just to be sure, in liveCD and in live session mode, if you see in the desktop a partition that is mounted, rt. click on the icon to unmount.  If none, you're good to go.

In liveSession, and using gparted, if you cannot resize because you are given greyed-out option, RT. click on the SWAP partition and SWAPOFF.

Good luck.  A personal copy of a gparted disc is valuable :)

Back up your files before working on a hard drive.

Also, kindly take a screenshot of the *current* gparted output and post back.  It'll help the contributors in this thread to visualize.

---


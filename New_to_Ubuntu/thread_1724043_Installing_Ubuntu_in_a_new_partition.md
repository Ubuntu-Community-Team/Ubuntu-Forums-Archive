---
title: "Installing Ubuntu in a new partition"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by tishtosh on 2011-04-07
Hey guys, 

I know this is an absolute newb question and you've probably answered it a million times, but here goes.

I have 2 HDDs, 250Gb (OS) and 2Tb (media). I recently installed Ubuntu 10.10 on my laptop with no issues, just did a complete format of the disk because I just got sick of Vista...

I know Linux uses EXT3/4 as a file system, so I split the OS HDD into approx 120Gb for Windows 7 and 110Gb for Ubuntu 10.10, leaving the Windows partition as NTFS and defining the new partition as EXT3 (I used EASEUS Partition Tool, and EXT4 was unavailable). But when I run the Live CD from boot to install, it says there isn't enough space available (i.e. less than 2.4Gb). What do?

I have backed up my OS to the media drive so I'm less worried about removing the new partition and letting Ubuntu make the partition itself, but can someone tell me how risky it is?

That's about it, thanks in advance for the help!

---

### Post by ssulaco on 2011-04-07
tishtosh,welcome to Ubuntu......Im dual booting XP and 10.04,I installed Windows first,I defragged windows and ran chkdsk,I then used gparted live to partition windows to make room for Ubuntu
Not sure whats going on with the low HDD space..
someone correct me if Im wrong but I think youre suppose to use the partitioning tools in Vista/7 rather than using a 3rd party partitioning tool
The default install on my system was ext4
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by tishtosh on 2011-04-07
Hi, thanks!
Well I deleted the new partition to see if that would make any difference. I rebooted from the Ubuntu CD and yet again it said there wasn't enough room (on the 250Gb OS drive), although the most definitely is...

Maybe I should unplug the media drive to only leave the main boot drive available, you reckon that would work?

I took a look at that GParted Live link, and it's for x86 computers. Since I'm running 64-bit W7, not 32-bit, would that have an effect? I never really looked into the details of 32/64-bit software...

Thanks again.

---

### Post by ssulaco on 2011-04-07
Boot up the Ubuntu cd...can you run it "live" (try ubuntu without any changes to your computer),gparted is on the live session,if you can get to the live session desktop,go to System -> Admin -> GParted to take a look at your partition

---

### Post by Quackers on 2011-04-07
Does Windows still boot up ok? Windows 7 does not like other partitioning tools playing with it! If Win 7 boots, you may need to run a chkdsk on it.
Also take a look at the Windows Disk Management Console to see how much space Windows thinks it has. Also note how many primary partitions are already in use - 4 is the max on any single hard drive (unless you use GUID Partitioning).

---

### Post by tishtosh on 2011-04-08
I tried running GParted from the Ubuntu boot; it started but no options were available and all the buttons were greyed out...

Win7 still boots fine. I'll run a chkdsk and see if it's fine. If it is I'll try the disk management and report back!

There are only 3 partitions currently on my OS drive:
 - The main C: drive
 - System reserved space (~70Mb)
 - Other space that also seems to be system reserved but isn't labeled (~60Mb)
All of them are labeled as primary.

---

### Post by ssulaco on 2011-04-08
> **tishtosh said:**
> I tried running GParted from the Ubuntu boot; it started but no options were available and all the buttons were greyed out...

Win7 still boots fine. I'll run a chkdsk and see if it's fine. 
Gparted wont let you do anything to the unmounted Windows partition if it senses file system corruption(i.e. heavily fragged or needs chkdsk)like I stated in my original post.
1)Defrag Windows 
2)run chkdsk
3)try using Disk management in 7 first.

---

### Post by oldfred on 2011-04-09
Post a screenshot of windows partition management if you cannot get gparted to show you your partitions. 
Does this show anything from the liveCD/liveUSB?

```
sudo fdisk -lu
```

---

### Post by tishtosh on 2011-04-09
C: shouldn't be at all fragmented as it was a clean install on a formatted drive only a few months ago, but I ran a defrag and disk check and everything's dandy now.

Using Win7 disk management I've shrunk the partition, but when I try to format the unallocated space I can only set it to NTFS or exFAT, which Ubuntu can't use, right?


I'll try that command oldfred, thanks.

---

### Post by tishtosh on 2011-04-09
Sorry for the double post.


I'm currently running Ubuntu from the CD and have tried what you suggested:
[IMG]http://i166.photobucket.com/albums/u107/toshtish/Screenshot.png?t=1302349343[/IMG]

As you can see, GParted won't detect anything, the command has no effect (I also tried "sudo fdisk -l"). I checked Disk Utility and although I'm not quite sure how to interpret it, I'm pretty certain it's not recognising my HDDs correctly...

[IMG]http://i166.photobucket.com/albums/u107/toshtish/Screenshot-1.png?t=1302349831[/IMG]

The install package is still not recognising any space on my drive. What do?


Sorry about this hassle guys, I'm new to Ubuntu so don't really understand the commands etc.
Willing to learn though!

---

### Post by ssulaco on 2011-04-09
> **tishtosh said:**
> 
Using Win7 disk management I've shrunk the partition, but when I try to format the unallocated space I can only set it to NTFS or exFAT, which Ubuntu can't use, right?

If you have shrunk the partition where you want, using disk management,could you post a screenshot of your partitioned drive using the "snipping tool",under "Accessories" in 7,here is a picture of mine,Vista is using the entire drive.
Also could you download and burn Gparted Live to see what its showing?once its burned,use it like a live cd,lets see if it sees the unallocated space
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by oldfred on 2011-04-09
THe 693MB /dev0/loop looks like the CD (or USB flash) not the hard drive. And the CD is not partitioned.

But it does not look like it sees a hard drive.

---

### Post by tishtosh on 2011-04-09
> **ssulaco said:**
> If you have shrunk the partition where you want,  using disk management,could you post a screenshot of your partitioned  drive using the "snipping tool",under "Accessories" in 7,here is a  picture of mine,Vista is using the entire drive.
Also could you download and burn Gparted Live to see what its  showing?once its burned,use it like a live cd,lets see if it sees the  unallocated space
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
I removed it to see if the Live CD would do the partitioning itself but no dice.
I'll reshrink it and report back. Do you want me to set it to EXT3 or just leave it as Unallocated? I'll assume unallocated unless you state otherwise. [Attached image]


> **oldfred said:**
> THe 693MB /dev0/loop looks like the CD (or USB flash) not the hard drive. And the CD is not partitioned.

But it does not look like it sees a hard drive.
That would make sense.
I can see that that it's finding 2 SATA drives, but it won't register any proper information on them, so it's as if they're present but not spinning or something?

---

### Post by ssulaco on 2011-04-09
> **tishtosh said:**
> I removed it to see if the Live CD would do the partitioning itself but no dice.

Assuming your talking about the unallocated partition you made with 7's disk management,and are you talking about the Ubuntu live CD,or the Gparted live CD?
The reason I'm curious about Gparted is that if it see's your partitions and the Ubuntu CD doesn't,You may have a bad Ubuntu Image.Looking at your screenshot everything looks good,
In an earlier post you suggested unplugging the media drive,go ahead and unplug it,see what happens.
I need to know if you have tried Gparted live.
I dont see any HD's in the screenshot in post#10,its sensing the controllers,but no drives,Correct me if Im wrong,but I dont believe the live session will see your HD using the Disk Utility.

---

### Post by tishtosh on 2011-04-09
> **ssulaco said:**
> Assuming your talking about the unallocated partition you made with 7's disk management,and are you talking about the Ubuntu live CD,or the Gparted live CD?
The reason I'm curious about Gparted is that if it see's your partitions and the Ubuntu CD doesn't,You may have a bad Ubuntu Image.Looking at your screenshot everything looks good,
In an earlier post you suggested unplugging the media drive,go ahead and unplug it,see what happens.
I need to know if you have tried Gparted live.

Sorry, I should have clarified. I was using the Ubuntu CD to check if it would see the 'new' space.
I used the same disc only days ago to install Ubuntu on my laptop, which I'm now using to write this, so it shouldn't be bad!

I just tried GParted Live and it booted fine to the setup part. There I ran into some trouble though. I tried the GUI interface with automatic setup but for some reason (unknown to me), the display was just a series of messy diagonal lines; almost as if the drivers weren't loading...
I tried a manual setup using appropriate selections (1280x1024, 24-bit colour etc) but didn't know which drivers to enter in to the selection. I looked it up and, as advised on the support website, used both of the following to no effect:
```
nouveau.modeset=0
nouveau.modeset=1
```I had no success leaving it as the default "Vesa" (or Veta, something like that) either. For the record my card is an NVidia GTX480 (supplied by ASUS).

I tried using the command line interface but don't know which commands to use, so avoided that in case I messed anything up.

I haven't tried unplugging the media drive yet but I'll give that a go.

Thanks for all the help so far, sorry to be such a bore!

---

### Post by tishtosh on 2011-04-09
> **ssulaco said:**
> Assuming your talking about the unallocated partition you made with 7's disk management,and are you talking about the Ubuntu live CD,or the Gparted live CD?
The reason I'm curious about Gparted is that if it see's your partitions and the Ubuntu CD doesn't,You may have a bad Ubuntu Image.Looking at your screenshot everything looks good,
In an earlier post you suggested unplugging the media drive,go ahead and unplug it,see what happens.
I need to know if you have tried Gparted live.
I dont see any HD's in the screenshot in post#10,its sensing the controllers,but no drives,Correct me if Im wrong,but I dont believe the live session will see your HD using the Disk Utility.
In reply to your recent edit, you may well be right about the Live session not registering the HDDs, but as I say I'm completely new to Ubuntu and Linux in general so I'm not the one to ask!

I'm pretty nifty with computers, and can figure stuff out, in general, pretty quickly; but I'm not a programmer of any sorts, much more than mid-range commands and I'm just copying whatever you say!

---

### Post by ssulaco on 2011-04-09
Not sure where to go from here since you cant get Gparted to run,Have you tried another iso.?,Alternate and or torrent?I understand it was used for the laptop,I'm stabbing in the dark.
I would try 3-4 off this page if I were in your shoes...
[http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/)
Desktop
Alternate
and Torrent,either/or........and unplug the external drive.
You probably are aware of this,check the hashes,and burn super slow.

---

### Post by tishtosh on 2011-04-10
Do you know of any issues with running GParted with a relatively new GPU? I would try onboard graphics but my MoBo doesn't have it.

I'll try burning another disc, and unplugging the drive (it's an internal drive, not external).

Thanks again!

---

### Post by ssulaco on 2011-04-10
Sorry,I thought it was an external drive,if you havent unplugged it already leave it for the time being,try the other downloads I suggested first.

---


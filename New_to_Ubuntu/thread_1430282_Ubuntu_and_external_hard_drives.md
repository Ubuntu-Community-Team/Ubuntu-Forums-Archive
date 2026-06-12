---
title: "Ubuntu and external hard drives"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by rsgangr on 2010-03-15
Good day to the Forum!

Does anybody have experience running the following Western Digital external drives with Ubuntu?

1. WD Elements External HDD
2. WD MyBook Essentials HDD

Local suppliers say "they are designed for Windows" and none of them have ever run any flavour of Linux.

Currently I am running Ubuntu 8.04 LTS / Windows XP dual-boot. Are there likely to be problems with Ubuntu? I shall appreciate hearing any recommendations regarding external drives for backup purposes.

Regards
rsgangr

---

### Post by cascade9 on 2010-03-15
> **rsgangr said:**
> Local suppliers say "they are designed for Windows" and none of them have ever run any flavour of Linux.

Your local suppliers dont know much....

They are just standard USB external drives. You might not be able to run the software that comes with the drives in linux, but the drives work fine. Theres even a 'review' on amazon specifially stating that they work with ubuntu- 

[http://www.amazon.co.uk/Western-Digital-Elements-External-DeskTop/dp/B001BYFP68](http://www.amazon.co.uk/Western-Digital-Elements-External-DeskTop/dp/B001BYFP68)

---

### Post by bumanie on 2010-03-15
I have only ever run external drives put together by myself, but I have never had any not being recognised by ubuntu - I have used  WD, samsung and maxtor drives in external enclosures with no problems. Any pre-cased external hard drives belonging to other people have always worked too. You shouldn't have any problems.

---

### Post by Grenage on 2010-03-15
Those drives will work fine; the WD software won't, but you're not missing out on anything!

---

### Post by mikechant on 2010-03-15
The drives will probably come pre-formatted as one big NTFS partition; Ubuntu can use this and if you're going to use the drives to exchange data with Windows, that's probably OK.
If not you may want to reformat them as ext2, ext3 or ext4, which are the 'native' Linux filesystems and better integrated and better supported by various utilities.

---

### Post by Jerry N on 2010-03-15
> **Grenage said:**
> Those drives will work fine; the WD software won't, but you're not missing out on anything!

First thing I do with those drives is reformat with NTFS.  That way, Windows and Linux are both happy and I have gotten rid of the unwanted backup software.  

Jerry

---

### Post by Grenage on 2010-03-15
I do the same thing.  All the drives inside my Linux rigs are Ext4 at the moment, but I keep external media like USB drives as NTFS; it makes life much easier.

---

### Post by srs5694 on 2010-03-15
I agree with the others, for the most part; Linux includes "generic" support for USB storage devices -- external hard disks, USB flash drives, etc. This works with most (maybe all) such devices.

One caveat, though: [Another thread](http://ubuntuforums.org/showthread.php?t=1428360) on this forum reports an issue with an external Samsung drive that comes down to the fact that the drive is reporting a 1024-byte sector size rather than the more common 512-byte sector size. Linux itself is fine with this, but partitioning software based on libparted (including the text-mode GNU Parted and the GUI GParted) flakes out. The simpler text-based fdisk tool works fine on such disks, but if you're more comfortable with a GUI tool, GParted's bugginess in this respect could be a problem.

That said, this one incident is the only time I've heard of an external hard drive claiming to have 1024-byte sectors. Most appear to the OS as having 512-byte sectors. It's something to keep in mind in case you have problems with a libparted-based tool, though.

---

### Post by Grenage on 2010-03-15
I 'think' the new release of Gparted has proper 1024k support; failing that, you can partition a 1024k drive with *fdisk -u* and specify 64 as the starting sector.

---

### Post by quadproc on 2010-03-15
> **rsgangr said:**
> Good day to the Forum!

Does anybody have experience running the following Western Digital external drives with Ubuntu?

1. WD Elements External HDD
2. WD MyBook Essentials HDD

rsgangr

I don't have experience with either of those two models but I did study them while I was choosing the external drive that I have now.  I eventually chose to get an Azio ENC311SU41 case and a 1TB Western Digital WD1001FALS disk rather than getting a preassembled unit.  Assembling the two was trivial and it worked fine right away.The Azio case only offers eSATA and USB; of course, the USB interface is much slower but I did not care because was planning to use only the eSATA port.

I chose the Azio case because a local computer store had that brand.  Since they were local, I knew that I could exchange it if it didn't work.  It did work.

You might wish to look at the Ubuntu Hardware Compatibility List (HCL) at UbuntuHCL.org.  There is also a hardware incompatibility list but I don't remember where it is located.

I do know of one external disk drive that does not work: the Buffalo HD-HSQ.  I bought one of these on my first attempt to get an external drive and it failed electronically the second time that I powered it on.  After much time and effort involved in getting it repaired under warranty, I finally received a replacement which functions on its Firewire port but not on its eSATA port.  The system can see that **something** is there on the eSATA port but gparted cannot interact with it.  I decided to scrap it.

quadproc

---

### Post by srs5694 on 2010-03-15
> **Grenage said:**
> I 'think' the new release of Gparted has proper 1024k support; failing that, you can partition a 1024k drive with *fdisk -u* and specify 64 as the starting sector.

It's possible that the non-512-byte bug has been fixed in an update; however, there's no need to specify a starting sector of 64 in this case. That's a different, but related, issue. Specifically, some recent hard drives from Western Digital (Caviar Green drives with model numbers ending in -EARS or -AARS) have 4096-byte physical sectors but report that they have 512-byte sectors, so GParted can partition them, but doing so can result in degraded performance. If partitions don't start on 4096-byte boundaries, the result is that some operations that should require reading or writing one sector will actually require reading or writing two sectors. The results can be quite dramatic (up to a 30x slowdown for some operations). Starting all sectors on multiples of 8 sectors (such as 64) fixes this problem.

The issue I was referring two is, in some sense, the opposite; the drive reports its sector size is 1024 bytes, which causes libparted to flake out. I suspect that the drive's physical sector size is actually 512 bytes and that it's just the USB interface that's faking a 1024-byte sector size, but I'm not positive of that. In any event, the performance-degradation issue with the recent WD drives doesn't come up in this configuration, so there's no need to take special care with partition alignment.

It'd all be much simpler if the manufacturers stopped playing games with such things. The reason for WD faking 512-byte sectors is for software compatibility. (Windows XP reportedly has problems if it's told the true sector size.) I have no idea why the external USB drive I was referring to specifies that it has a 1024-byte sector size. Maybe it really does, but I suspect it's lying for some reason I don't know, since I've never heard of a hard disk with a true physical 1024-byte sector size.

---

### Post by Grenage on 2010-03-15
Thanks for clearing that up!

---

### Post by quadproc on 2010-03-15
> **rsgangr said:**
> Good day to the Forum!
...
Local suppliers say "they are designed for Windows" and none of them have ever run any flavour of Linux.


This probably should have its own thread, but here goes: Have you considered taking a Live CD to your local computer people and showing them what Ubuntu looks like and how it operates?  You might get some converts.

quadproc

---

### Post by Jerry N on 2010-03-15
> **quadproc said:**
> This probably should have its own thread, but here goes: Have you considered taking a Live CD to your local computer people and showing them what Ubuntu looks like and how it operates?  You might get some converts.
quadproc

Yeah, right!  You think the folks at the Borg (big box store) are going to understand?  The best you will hear is "performance is terrible".  

Jerry

---

### Post by lyall on 2010-03-15
adding an external hard drive
see the link for MountUSB in Ubuntu documentation
it should answer your question and how to trouble shoot if you have a problem
[https://help.ubuntu.com/community/Mount/USB]("https://help.ubuntu.com/community/Mount/USB")

also look at titleindex
[https://help.ubuntu.com/community/TitleIndex]("https://help.ubuntu.com/community/TitleIndex")

you can also do a search from this page to find the info you might need

good luck and have fun learning

---

### Post by rsgangr on 2010-03-16
Thanks to all who took the time to answer my query. I remain amazed at how quickly people on this forum respond to questions !!!

cascade9: "Your local suppliers dont know much...."
You are absolutely correct! Even technical questions on Windows usually draw a blank stare.

bumanie & quadproc:
I am also looking at putting together a unit using an external enclosure. However, the WD external drives are currently on specials.

Grenage: "Those drives will work fine; the WD software won't"
Thanks - I was not planning to use any accompanying software.

mikechant , Jerry N & Grenage:
My intention is to use NTFS as, in addition to my dual-boot machine, I need to be able to use the drive with other Windows machines too.

srs5694 & Grenage:
Thanks for the discussion on the sector size issue. Having done a fair amount of programming in the dim-and-distant past (DOS & Windows systems, Pascal, HPL) I am comfortable in using command-line tools. At this point, however, I am not looking at partitioning an external drive.

quadproc: "Have you considered taking a Live CD to your local computer people and showing them what Ubuntu looks like ..."
I suspect the response might be "Does it run in Windows?"

lyall:
Thanks  for the links - I shall visit the sites later today.

---


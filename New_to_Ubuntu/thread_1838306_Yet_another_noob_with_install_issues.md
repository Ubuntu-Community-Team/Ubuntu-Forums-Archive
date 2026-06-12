---
title: "Yet another noob with install issues"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by AnthonyFernando on 2011-09-03
Hi people, my first post to the forums.  I have been trying to install Ubuntu on my machine for about a week, keep hitting problems that have appeared before in the forums, but my particular set of symptoms doesn't appear to be covered.  I have made some progress by downloading the DVD image of 11.04 (AMD 64) rather than the CD image.  However, I still can't get past the install stage, as the installer doesn't see any partitions on my hard drive.  What I am trying to do is keep Windows XP64 on one hard drive and install Ubuntu on the second hard drive, which has been cleared.  First, some hardware setup details.

Machine details:
Motherboard: Intel D975XBX
CPU: Intel Pentium D940 3.20 GHz
Hard drives: 2x Seagate ATA ST3320620AS 320GB, connected to SATA 0 and SATA 1

BIOS drive settings (active option in <> braces):
Automatic Mode: <Enable>/Disable
ATA/IDE:  <Enhanced>/Legacy
Configure SATA: <IDE>/RAID/AHCI

Now, I can boot from the Live DVD ok, but I can't install Ubuntu.  The install program only sees sda (the drive with Win XP), and no viable partitions on sda (a common problem, it seems).  I want to install to sdb. 

As suggested on several threads,  I have opened a terminal and  typed sudo fdisk -l, and both drives seem to be recognised.  I've run Gpartition, and confirmed it sees both drives, sda and sdb.  I have also managed to format the second drive sdb as a bootable Linux ext3 partition.  However, when I then go into Disk Utility things are (possibly?) a little odd.  The two drives are listed as PATA devices.  When I select sda (the Windows XP disk), it sees it as a 320GB RAID component (even though I don't have RAID selected in the BIOS), while sdb is correctly recognised as a Linux ext3 drive (320GB).  sdb can be mounted and unmounted no problem.  I have tried mounting it and then running install, but still no sign of sdb.

At this point I'm stuck.  Both drives seem to be there, but the installer still can't find the drive I want to install to.  Help, anyone?

Regrads,
Frustrated Noob.

---

### Post by kherring7383 on 2011-09-03
Anthony, If you're getting any error messages, if you could please post them it may help better understand the problem you're having. About two weeks ago I too was attempting to install 11.04, but during the install, my hard drive was not detected an a message stating that No Root File System was defined. And like you, I did every thing I could think of including formatting the drive with MSDOS. Finally though I did find the anwser on another forum. The solution was to boot with a live CD and then from Terminal, remove the DMRAID app like this: sudo apt-get remove dmraid, and then anwser yes when prompted. After I did this, I could install 11.04 straight from the install option icon on the desktop. I really don't know if this will help, since I don't know the nature of the problem, but maybe this post may help someone else.

---

### Post by Quackers on 2011-09-03
Welcome to UF :-)

Have you deleted the raid array? Were/are you using raid0 or raid1?
Is this a bios raid setup (like Intel )?

You may just need to remove raid metadata which has been left over, or it could be more involved than that.

Please give full details of what has happened on thaty system.

EDIT kherring7383, If you run that on a system using raid you will lose everything on the system! Be careful with that advice.

---

### Post by nipunshakya on 2011-09-03
^^^just an simple opinion...why not remove/unplug sata 1 or sda that has windows xp, and then boot from the live dvd and then try installations....i might be wrong here but just a simple guess..:) good luck

regards, NeptuneTech

---

### Post by AnthonyFernando on 2011-09-04
Thanks for the feedback, folks.

Quackers, as far as I know my machine has never actually used the RAID capabilities.   It was purchased at my workplace to run CAD programs (hence 64bit and 8GB RAM) and a system was set up with the option to run RAID if we wanted, but never did.  It is indeed an Intel BIOS RAID setup.  However, it has always been operated in IDE mode, with one disk for programs and the other for data storage.  Windows always saw both C: and D: drives (until I formatted D: to Linux, which it no longer sees); I gather with RAID running, it would only see a single drive?

NeptuneTech, I have seen people on the forums try disconnecting their Windows drive and installing Linux on the other drive, but then strange things happen when the Windows drive is reconnected.  I think it is best to avoid going down that route, as it is not addressing the root of the problem.

kherring, your solution looks promising, but I have taken heed of Quackers' advice.  All important data from Windows XP was backed up before I tried anything regarding partitioning in case Ubuntu was mixing up the drives somehow.  However, I'm pretty certain removing RAID should be safe in this case. I'll give it a shot and let you know how I go.  If you don't hear from me within a week, it's because I'm reinstalling everything on XP...  ;)

---

### Post by AnthonyFernando on 2011-09-04
Back again, without wiping my XP drive! :)

Hmm... kherring's solution doesn't seem to be the answer.  I tried "sudo apt-get remove dmraid", but I'm not sure it did anything much (see screenshot). 

[Kill_raid.png]("http://ubuntuforums.org/attachment.php?attachmentid=201437&stc=1&d=1315124199") 

What I do know is that after doing this, install doesn't get past the "Preparing to Install" screen.  The install process seems to freeze here without responding (screenshot 2).

[Install_freeze.png]("http://ubuntuforums.org/attachment.php?attachmentid=201438&stc=1&d=1315124322")

Not sure what actually happened here.  After forcing closure of install, it wouldn't start again when I clicked the icon for a fresh attempt.  The only solution was a reboot.  

I did this series of steps twice, same thing both times.

Just to clarify my earlier post, here is what Disk Utility sees on my system:
[Screenshot-320 GB Hard Disk (ATA ST3320620AS) [-dev-sda] ÔÇö Disk Utility.jpg]("http://ubuntuforums.org/attachment.php?attachmentid=201439&stc=1&d=1315124829")

[Screenshot-320 GB Hard Disk (ATA ST3320620AS) [-dev-sdb] ÔÇö Disk Utility.jpg]("http://ubuntuforums.org/attachment.php?attachmentid=201440&stc=1&d=1315124829")

Hope that helps someone out there.

---

### Post by racoffey63 on 2011-09-04
Are you having your installer remove the previous install before trying a new one?  I did my install from an USB drive(only 4 tries to get it right).  
 
Once you fix your RAID problem, try a HD install.
 
Also, is there a particular reason you wanted the install on the second drive?

---

### Post by AnthonyFernando on 2011-09-07
Ok, I've given up for now.  Fedora won't install either, similar symptoms but even less forgiving than Ubuntu.  I don't know why either installer ignores the BIOS setup and thinks the drives are in some sort of RAID configuration.  Or whatever... ](*,)  

Interestingly, when I booted up from disk with my external USB drive inadvertently plugged in, the installer recognised that as a partition while it couldn't find anything on either internal hard drive.  Does that clue help anyone?  And before anyone suggests it, no, I don't want to install on the removable drive.

To answer racoffey63, the reason I want to install on the second drive is that I don't want to squash up my Windows partition to make room for a Linux partition when there is an entire blank drive going begging.  Seems a simple enough proposition; Windows on one drive, Ubuntu on the other.  Also, there are no old installs on either disk.

---

### Post by westie457 on 2011-09-07
Probably barking at the wrong tree here. Is it possible that The installer is getting confused by the fact that the hard drives are the same size and from the same manufacturer. I am thinking that somehow they possibly have identical UUIDs and that is why only one is being recognised.

---

### Post by thefasterblueone on 2011-09-07
Try switching to 'Legacy ATA mode' in bios.

---

### Post by jroa on 2011-09-07
> until I formatted D: to Linux, which it no longer sees

What file extension did you format it to, and what software did you use?  Can you post a GParted screen shot?

---

### Post by AnthonyFernando on 2011-09-13
I have tried switching to Legacy ATA mode, no effect.  I vaguely remember early on, though, when I was fiddling with the 32-bit version and tried Legacy ATA, the installer did find something and offered to reformat it.  Don't remember the details apart from the mental warning lights...

@jroa: When I used GParted, I have tried both Ext3 and Ext4 to format the second drive, and tried either bootable or not.  Not sure what a screenshot of GParted would show; as I mentioned previously, GParted and Disk Utility seem to see both drives and their partitions ok, it's the installer that doesn't.

---

### Post by Quackers on 2011-09-13
Try booting up from the live cd/usb and selecting "try ubuntu" and when the desktop loads open up a terminal and run these commands. ```
sudo dmraid -rE /dev/sda
sudo dmraid -rE /dev/sdb
``` This assumes that your 2 hard drives are /dev/sda and /dev/sdb. If they aren't change the commands accordingly.
It should say that raid metadata has been removed or that no raid metadata was found. 

***** Please Note!!!
If your system is using raid you may lose everything on the system by running these commands!

---


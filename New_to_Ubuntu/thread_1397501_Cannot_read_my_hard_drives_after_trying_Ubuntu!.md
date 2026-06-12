---
title: "Cannot read my hard drives after trying Ubuntu!"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by john.kreelman on 2010-02-03
Hey there.

People, I tried Ubuntu 9.10 on my system by poping out my XP master drive & substituting it for a temp older drive & installing Unbuntu. I left the rest of the machine as is - 3 other drives with my docs, pics & music on.

When I put my XP drive back in place of the Ubuntu temp drive I find that I cannot read any of my data now in XP. All the drives are GDP! Data is all intact as I can read it in Ubuntu if I pop the other drive in. 

I'm furious. Any ideas on how to overcome this hiccup please? Had a quick surf but all I could find was info about getting this to work with servers or purchase Vista/7 64 bit.

Bit stuck!!! Any help would be very much appreciated.

Just as a thought, an absolute novice I am, but this is exactly the sort of scenario that burns prospective users fingers - I wanted to safe guard my XP install and never thought for one minute that it would effect my data like this? Would this have occurred with the live cd I wonder?

Sempron 3000, MSI board, XP home 32 bit. 4 drives total - NTFS about 1.2 TB in all.

---

### Post by audiomick on 2010-02-03
Hallo.
It wouldn't have occurred with the live CD ( or shouldn't, anyway).

The behaviour sounds like something I read the other day, but I am afraid I am hazy on the details. It seems that if windows detects what it considers to be an irregularity on a drive, it might decide the drive has a problem and lock it. I don't know exactly what might have triggered this in your case, but something like that would be my first guess.
Nothing that I am aware of about Ubuntu should have made your drives invisible, short of re-formatting them during the installation.

---

### Post by john.kreelman on 2010-02-03
Didn't do anything to data disks save for access them. No formats or owt. On the main O/S disc I uesd the whole disk. Would this then have looked for completely seperate disks and adjusted them to GPD?

---

### Post by audiomick on 2010-02-03
> **john.kreelman said:**
> Didn't do anything to data disks save for access them. No formats or owt. On the main O/S disc I uesd the whole disk. Would this then have looked for completely seperate disks and adjusted them to GPD?
GPD is the partition table format, right? No, I don't think that anything would have been changed there. If it were, then it wouldn't be possible to set up dual boot systems, would it? The process of installing Ubuntu would shoot down the windows file system every time.

---

### Post by Paqman on 2010-02-03
> **audiomick said:**
> 
The behaviour sounds like something I read the other day, but I am afraid I am hazy on the details. It seems that if windows detects what it considers to be an irregularity on a drive, it might decide the drive has a problem and lock it.

I think what you're talking about is an unclean shutdown of an NTFS partition. This can sometimes happen if your NTFS drives don't unmount when you shut down Ubuntu. This leaves a flag on the NTFS filesystem that prevents you from mounting it in Ubuntu. It will however mount in Windows. So for that reason I don't think it's the problem here.

What's more likely to have happened is that John has inadvertently formatted his data drives when he installed Ubuntu. I really hope that's not the case, though.

---

### Post by audiomick on 2010-02-03
> **Paqman said:**
> I think what you're talking about is an unclean shutdown of an NTFS partition. This can sometimes happen if your NTFS drives don't unmount when you shut down Ubuntu. This leaves a flag on the NTFS filesystem that prevents you from mounting it in Ubuntu. It will however mount in Windows. So for that reason I don't think it's the problem here.

What's more likely to have happened is that John has inadvertently formatted his data drives when he installed Ubuntu. I really hope that's not the case, though.

Don't think he formatted: from his first post
> Data is all intact as I can read it in Ubuntu if I pop the other drive in. 

I have to admit, though, that I don't have any firm ideas what the problem might be...

---

### Post by JayKay3000 on 2010-02-03
This is terribly odd.

I can't imagine how you would have done this as i've duel booted xp and Ubuntu (installed them side by side on the same drive) and not come across this.

The only solution I can think would be to re-format each drive in NTFS again (assuming you can see the disks in the computer management tool, under Disk Management).

Unless someone else has a better idea?

---

### Post by john.kreelman on 2010-02-03
JayKay - drives full of data. Backed up bout 2 weeks ago so don't really want to go down that route. Just as a point, not dual booting as I poped in a drive to take Ubuntu to have a lok at it and disconnected the XP drive.

Must be something to do with the fact that Ubuntu didn't see any other OS so decided to remove the windows file system table (MBR is it?) and put the ubuntu GPD on there?

---

### Post by cgb on 2010-02-03
Can you post the output of the below command in terminal on Ubuntu?  This should show what filesystem the drives are currently formated to.  

```
fdisk -l
```

---

### Post by LowSky on 2010-02-03
> **john.kreelman said:**
> JayKay - drives full of data. Backed up bout 2 weeks ago so don't really want to go down that route. Just as a point, not dual booting as I poped in a drive to take Ubuntu to have a lok at it and disconnected the XP drive.

Must be something to do with the fact that Ubuntu didn't see any other OS so decided to remove the windows file system table (MBR is it?) and put the Ubuntu GPD on there?

Yeah.... NO! Ubuntu doesn't change other hard drives settings, especially media only drives.

Go into BIOS and check the order of the drives from there. Check all you cabling and make sure everything is attached correctly. Windows XP should detect the drives and they should be readable.

---

### Post by warfacegod on 2010-02-03
> **john.kreelman said:**
> JayKay - drives full of data. Backed up bout 2 weeks ago so don't really want to go down that route. Just as a point, not dual booting as I poped in a drive to take Ubuntu to have a lok at it and disconnected the XP drive.

Must be something to do with the fact that Ubuntu didn't see any other OS so decided to remove the windows file system table (MBR is it?) and put the ubuntu GPD on there?

Your MBR ought to have been on the drive that Windows was installed on. If it wasn't in your system it would therefore be impossible for Ubuntu to overwrite it.

---

### Post by nhasian on 2010-02-03
> **john.kreelman said:**
> I find that I cannot read any of my data now in XP. All the drives are GDP!

> **john.kreelman said:**
> Must be something to do with the fact that Ubuntu didn't see any other OS so decided to remove the windows file system table (MBR is it?) and put the ubuntu GPD on there?

I think he's talking about GPT (GUID Partition Table)

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

Installing Ubuntu on one hard disk does not make any changes to any other hard disks (unless of course you tell the partition editor to delete or add new partitions but that would destroy the data so this is not the case)

I am inclined to agree with LowSky.  Its probably just a cabling or bios issue.  If you hava PATA drives you may have had to change jumpers as well.

---

### Post by john.kreelman on 2010-02-03
I'll post the fdisk in a mo. Pata is the Ubuntu drive, rest are Sata. Checked cable even though all working in ubuntu, all ok. still can't get any data on disks to show in xp. Just the fact there's a disk there in managment, no drive letters etc. Even tried putting windows 7 64 bit on another spare drive to read as somewhere I read that reads the linux file system but it doeas the same as xp, just sees the disk but no access. Triple darn it this is annoying! right fdisk.

---

### Post by john.kreelman on 2010-02-03
kreelman@kreelman-desktop:~$ fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
kreelman@kreelman-desktop:~$ fdisk -l
kreelman@kreelman-desktop:~$ fdisk-l
fdisk-l: command not found
kreelman@kreelman-desktop:~$ fdisk -l
kreelman@kreelman-desktop:~$ fdisk -l
kreelman@kreelman-desktop:~$ fdisk -l
kreelman@kreelman-desktop:~$ ^C
kreelman@kreelman-desktop:~$ fdisk /dev/hda

Unable to open /dev/hda
kreelman@kreelman-desktop:~$ fdisk /dev/sdc

Unable to open /dev/sdc
kreelman@kreelman-desktop:~$ 


I'm obviously not doing it correctly!!!

I think I'm just going to have to copy the data off the drives in ubuntu and then format the blasted things, copy it back. God only knows why I tried this.

---

### Post by audiomick on 2010-02-03
needs a "sudo"
```
sudo fdisk -l
```
lower case L, not figure one.

---

### Post by nhasian on 2010-02-03
I just realized that this is a windows problem.  you need to try to fix it in windows, not in ubuntu.  (its already working in ubuntu right?)

In windows, you should check the device manager and see if there are any devices that have a yellow or red circle indicating a device failure or driver problem.

also in Windows you should go into the disk manager to see if it sees all the drives, and the partitions on it.  it might be something as simple as just assigning drive letters to the unmounted drives.  if they already have drive letters, run scan disk on the drives.

---

### Post by john.kreelman on 2010-02-04
Windows fault that linux changed file system? Q here is why? How? and how to over come?

Can see drive in windows, but not access, assign a drive letter or owt. There must be a way to delete the file system indicater table as its obviously just made a minor change to the way its to be recognised. I really want to get to the bottom of this as it's a really important issue. I know my windows and would like to explore linux. No obvious changes were made to these drives - only literally accessed - and this problem occurs. Big issue here 'cos as I indicated before, this could burn many fingers to ubuntu/linux. I'll try that fdisk when I get back on tother machine. Cheers.

---

### Post by nhasian on 2010-02-04
john.kreelman your missing the point.  linux didnt change anything.  the change occured in your windows.  thats why you have to fix it in windows.

do the things i suggested in windows and let us know if you make any progress.

If i remember correctly, Windows XP will not be able to read SATA drives unless you have a particular service pack?

---

### Post by muteXe on 2010-02-04
Does seem a bit dodgy tho, that this chap's "windows problems" only started occuring after using linux...

---

### Post by audiomick on 2010-02-04
However it came about; does anyone know if it is possible to just go into gparted and change the partition tables from GPD back to whatever it is that windows likes? Or does that re-format the drive automatically?

---

### Post by warfacegod on 2010-02-04
I'm not sure if gparted can do that but I *think* testdisk can.

This is clearly a case of user error. Simply trying out Linux isn't going to change the partition table unless it is specifically told to by the user. If the OP was trying to view his NTFS partitions and make changes to them, or more specifically the files on them, it is very possible that he may have installed something or inadvertently given something permission to modify the partition table.

---

### Post by john.kreelman on 2010-02-04
> **nhasian said:**
> john.kreelman your missing the point.  linux didnt change anything.  the change occured in your windows.  thats why you have to fix it in windows.

do the things i suggested in windows and let us know if you make any progress.

If i remember correctly, Windows XP will not be able to read SATA drives unless you have a particular service pack?


Just to refresh order of events.

Had Windows XP Home up and running no probs on it's own HD with 3 other physical seperate drives for my data, music, movies, etc.

Wanted to try Ubuntu, so:
To safe guard my XP install, physically removed XP os hard drive.
Substituted with main drive for Ubuntu os. Disconnected my data drives. Installed Ubuntu fine, no hiccups, all dandy.

Power down, reconnected my sata data drives to see what could be seen. Accessed all drives ok, no formats no windows popping up to say 'Can I change file system' or anything what so ever. Could see all drives, read data etc.

Then after this needed to get XP back online, power down disconnected Ubuntu drive pop in my XP drive, power up and boot no probs, but no data drives. Disk management can see them but not assign any letters etc as the file system is now GPD or GUID as someone mentioned. Simple as, nothing else done.

If I reconnect the Ubuntu OS then I can see all data and access it. So logically Ubuntu HAS changed something. I'm not trying to fault anything and am not a Linux or Windows fanboy or hater. Situation has occured and I believe there must be an easy solution apart from me copying all 1.2 odd TB to another NTFS disk so that XP can read it. This has to be of major importance to the linux community as I know there is a whole worldful of woe when many people try these new OS's. I have nothing but admiration for the Lunix world and I'm trying to not let that be bashed by this. I really want to sort this as I cannot be the only person to have come accross this?

Device manager in XP sees all disks with correct drivers. In the old days the SATA drivers for some mobo bios's needed to be loaded before the microsoft os. Haven't come across any service pack issues unless you go way back (16 bit?) computing with issues on sectors/drive sizes.

---

### Post by john.kreelman on 2010-02-04
> **warfacegod said:**
> I'm not sure if gparted can do that but I *think* testdisk can.

This is clearly a case of user error. Simply trying out Linux isn't going to change the partition table unless it is specifically told to by the user. If the OP was trying to view his NTFS partitions and make changes to them, or more specifically the files on them, it is very possible that he may have installed something or inadvertently given something permission to modify the partition table.

I'll try testdisk, thanks. Getting a peeved with the user error thing. Yes, I'm new to linux, but I'm not stupid (or didn't think I was until I tried this, lol!!!). Nothing, repeat nothing indicated to me that I was changing anything whilst accessing the data drives. I didn't modify anything, just opened some pics, a document in openoffice, a video. Nowt else. Now maybe in doing that I did inadvertently change something? I would like to have knowledge.

I have backups so can recify the situation, but it's the effort envolved which narks me for such a harmless experiment.

---

### Post by Paqman on 2010-02-04
> **john.kreelman said:**
> Now maybe in doing that I did inadvertently change something? I would like to have knowledge.


I think the problem here is that you've stumped us too. There's no reason why simply installing Ubuntu should modify your data drives in any way. If something was going to make a serious change to a drive, it would have alerted you. Filesystems don't just change randomly.

Except in your case they seem to have, which is weird.

---

### Post by cgb on 2010-02-04
Yes, this is a very interesting problem and nothing should of changed by simply installing Ubuntu.  I still would like to know what Ubuntu is seeing the filesystems as for these drives.  If you get a moment try the fdisk command again except for with sudo.  The filesystems really should not of changed without some sort of prompt but from what you are saying it almost sounds like they did.  

```
sudo fdisk -l
```

---

### Post by john.kreelman on 2010-02-04
Will do that fdisk and post. 

Have ntfs'd a spare drive and pooled all the unbacked up data from  the data drives under ubuntu install. Was more than a tad nervous of conecting my backup drive to the ubuntu set up as you can imagine! Ntfs'd drive was ok though and was readable after the task on the windows install which caused me some consternation & confirms that Ubuntu doesn't automatically touch the structure as alot of you have mentioned. I'm so flummoxed by this I'm going to build a test rig and try to replicate the whole scenario as from what you guys are saying it just shouldn't have occured. I know I didn't grant any permissions for Ubuntu to do anything to the drives but theres alot of this on the web that seems to relate to this occurrance when using with servers and not being able to read drives.

Am bit wiping the other data drives (save one for fdisk)as cannot even access other drives to format them.

Just a thought. When disconnecting the data drives under Ubuntu I unmounted them and them safely ejected them, that was right wasn't it? Also, would the fact that when you install Ubuntu it asks for a password, that wouldn't have stopped the XP install seeing the data would it?

---

### Post by nhasian on 2010-02-04
I'm concerned about all this plugging and unplugging something might have gotten mixed up.  One more thing came to mind though, this new drive that you installed ubuntu on, is it also SATA?  and your Windows XP drive is PATA?  might that make a difference with bios settings and whatnot?

I'm guessing that if you blew away Ubuntu from that drive and installed Windows to it that it would also see the data drives just fine.

> **john.kreelman said:**
> To safe guard my XP install, physically removed XP os hard drive.  Substituted with main drive for Ubuntu os. Disconnected my data drives.

---

### Post by john.kreelman on 2010-02-04
I'm guessing that if you blew away Ubuntu from that drive and installed Windows to it that it would also see the data drives just fine.[/QUOTE]

Now that's an interesting thought but as you say I doubt that would make any difference. I will try though out of interest.

The output from the fdsik:

kreelman@kreelman-desktop:~$ sudo fdisk -l
[sudo] password for kreelman: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x73a373a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19458   156290903+  ee  GPT
kreelman@kreelman-desktop:~$ 


Any glimmers of light there? The 40GB Ubuntu is parallel and the 160 is serial

---

### Post by SecretCode on 2010-02-04
This is odd. Like the others, I can't think what could have happened to cause this, short of using a partition editing tool.

[COLOR="Gray"]Keen to see the *sudo fdisk -l* output.[/COLOR] eta: Seen it!

Testdisk can give information, but I wouldn't write any changes to the disks until we understand what has actually happened.

---

### Post by SecretCode on 2010-02-04
So it really is GPT.

Post output of ```
sudo parted -l
```
(Put the output between [ code ][/ code ] tags to keep the formatting)

---

### Post by SecretCode on 2010-02-04
Is there just one data drive, or three? (Obviously only one connected for your last post.) Were/are they all formatted NTFS? What sizes are they?

eta: Another thought: if the reported partition table is correct (and not a glitch in the cabling/jumpers), it can only have happened when the drives were connected to the ubuntu installation. Can you go into the system logs in ubuntu (System > Administration > Log File Viewer) and look in 'messages' and 'syslog' at the time you attached them? I don't know what we should look for, but there may be something.

---

### Post by john.kreelman on 2010-02-04
kreelman@kreelman-desktop:~$ sudo parted -l
[sudo] password for kreelman: 
Model: ATA WDC WD400EB-00CP (scsi)
Disk /dev/sda: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  38.3GB  38.3GB  primary   ext4            boot
 2      38.3GB  40.0GB  1686MB  extended
 5      38.3GB  40.0GB  1686MB  logical   linux-swap(v1)


Model: ST316081 1AS (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name                  Flags
 1      1049kB  160GB  160GB  ntfs         Basic data partition


kreelman@kreelman-desktop:~$

---

### Post by SecretCode on 2010-02-04
> **john.kreelman said:**
> Even tried putting windows 7 64 bit on another spare drive to read as somewhere I read that reads the linux file system but it doeas the same as xp, just sees the disk but no access.

Wait. Surely win7 has support for GPT? If it refused to mount the drives to a drive letter, then something else may be wrong. 

Do you remember (or can you test) what error message you got from win7?

---

### Post by john.kreelman on 2010-02-04
There were 3 data drives, all Sata, 160 x 1, 500 x2 plus the OS at 40GB Pata.

Had to crack on and get the others back in service I'm afraid.

---

### Post by john.kreelman on 2010-02-04
Argh, just wiped  the 7 (64 bit which is the one that apparently recognizes linux partitions) install this arvo! but it was the self same situation as with XP, no drive letter and thus no access to the disk although it recognized the disk through the controller and drivers all correct.

---

### Post by cgb on 2010-02-04
Even stranger..  Vista and Windows 7, even 32bit versions, should recognize GPT partitions by default.  Windows XP can read these drives with specific hacks but not by default.  The only thought I have at this point is the drives possibly were already set for GPT partitions, for whatever reason, before loading into Ubuntu and somehow corrupted when accessed.  You could possibly attempt to run a system check on the drives with the "fsck" command in Ubuntu and see if that makes any difference.  Otherwise your best course of action would probably be to complete the transfer of all files to new drives.

---

### Post by john.kreelman on 2010-02-04
CGB, you may have a very good point here. These data disks were originally used with vista, my machine of last year but ended up reverting to XP as Vista was a little gloopy to work with. Obviously they worked with XP but I wonder if you've 'nail hit head' as there may be some obscure 'something' that would cause an instability when working through Linux and then back to XP...... now this is what I like makes it all very interesting. Must have a play and try to replicate this.

fsck output

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

fsck.ext4: Permission denied while trying to open /dev/sda1
You must have r/w access to the filesystem or be root
kreelman@kreelman-desktop:~$ sudo fsck
[sudo] password for kreelman: 
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sda1: recovering journal
Clearing orphaned inode 951 (uid=1000, gid=1000, mode=0100600, size=248)
Clearing orphaned inode 859 (uid=1000, gid=1000, mode=0100600, size=1109)
Clearing orphaned inode 107 (uid=1000, gid=1000, mode=0140755, size=0)
/dev/sda1: clean, 143164/2342912 files, 812150/9357854 blocks
kreelman@kreelman-desktop:~$

---

### Post by SecretCode on 2010-02-04
> **john.kreelman said:**
> Had to crack on and get the others back in service I'm afraid.

Not sure what you mean by this.

Have you managed to get a workaround so you can read the data from the drives? Or are you still trying to rescue them?

It should be possible to write a normal MBR partition table to each drive without touching the partitions themselves (ie without reformatting), but I'm struggling to find information on this.

---

### Post by john.kreelman on 2010-02-04
> **SecretCode said:**
> Not sure what you mean by this.

Have you managed to get a workaround so you can read the data from the drives? Or are you still trying to rescue them?

It should be possible to write a normal MBR partition table to each drive without touching the partitions themselves (ie without reformatting), but I'm struggling to find information on this.

Low level format as cannot do anything with them under XP. Then treat them as a new drive under XP. Start again so to speak.

Yes, I would have though it possible to write a new MBR and used the HP utility for correcting missing ntldr problem but to no avail.

Just off for some tucker, be back in a while. TA.

---

### Post by cgb on 2010-02-04
Actually fsck would be the wrong command for this situation, I take back my previous recommendation.  fsck cant do a disk check on a NTFS partition and that is what we are working with.  The below thread has some instructions on installing and using another app called ntfsprogs that would be suitable.  Not sure if this will make any difference but could be worth a shot..

[http://ubuntuforums.org/showthread.php?t=729535]("http://ubuntuforums.org/showthread.php?t=729535")

---

### Post by audiomick on 2010-02-04
> **john.kreelman said:**
> kreelman@kreelman-desktop:~$ sudo parted -l
[sudo] password for kreelman: 
Model: ATA WDC WD400EB-00CP (scsi)
Disk /dev/sda: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  38.3GB  38.3GB  primary   ext4            boot
 2      38.3GB  40.0GB  1686MB  extended
 [COLOR=Red]5      38.3GB  40.0GB  1686MB  logical   linux-swap(v1)
[/COLOR] 

Model: ST316081 1AS (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name                  Flags
 1      1049kB  160GB  160GB  ntfs         Basic data partition


kreelman@kreelman-desktop:~$
  Just by the by John; if I am reading that right, you have a 40GB swap partition there. If you don't have a specific reason for this, it is probably about 10 times bigger than you need. Rule of thumb is a bit bigger than your RAM if you want to hibernate, otherwise just a GB or two if you have "modern" amounts of RAM installed.

---

### Post by SecretCode on 2010-02-04
So you still have one drive worth trying to recover?

I'd like to see what *sudo parted -l* says about this drive.

---

### Post by VernonA on 2010-02-04
Hi Michael
I think you did read it wrong (you looked at the End column, not the amount column, which says 1618Mb)!
Cheers
Vernon

---

### Post by audiomick on 2010-02-04
> **SecretCode said:**
> So you still have one drive worth trying to recover?

I'd like to see what *sudo parted -l* says about this drive.
That's the output in post #32, I think. The drive at sdb.

---

### Post by nhasian on 2010-02-04
please make sure that the partition you are running fsck on is [COLOR="Red"]NOT[/COLOR] mounted or data corrupt may result.

> **john.kreelman said:**
> WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes


---

### Post by SecretCode on 2010-02-04
> **audiomick said:**
> That's the output in post #32, I think. The drive at sdb.

Right, well spotted that man. :blush:


No luck finding a tool that will ***convert*** a GPT format to a MBR/msdos format. **testdisk** might be able to; at the minimum it should (could) work to create a new msdos partition table (msdos=MBR) and then get testdisk to find existing partitions.

---

### Post by oldfred on 2010-02-04
fdisk will not show gpt info, it is just smart enough to see it and quit so it does not damage it.

You can download gfdisk that will show gpt partitions the same as fdisk.

If it really was a MBR disk it can be converted back, but if not it may destroy everything:

[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by john.kreelman on 2010-02-04
Oh dear, it's all gone boobies up! Machine has just crashed and on restart it's saying that there's been a fsck error 722 & 721 mountall error. Ctrl D etc and nothing seems to want to run now. 

Oh well, it was fun!!!. I'm going to call it a day now and just go back to the start with fresh installs. I think the closest to a reason for this was the idea that maybe as the drives were origially formatted with Vista, then moved to XP, somehow this may have caused some sort of corruption to the windows portion mbr?

I'll definitely try and recreate this and let you all know the out come.

I would just lke to say a very large thank you to all of you very kind people whom have taken the time to respond to this and even though it's been very frustrating for me at times, I've very much enjoyed the experience.

I'm lookng forward to seeing the Ubuntu manual when it's released and I think for peace of mind I might just build a test rig that will be Ubuntu only to play on.

So thank you so much again. You're great people, maybe I can aspire to have a few more beans in the not too distant future...tongue in cheek as I've soooo much to learn...!!!

Sort of solved.

---

### Post by SecretCode on 2010-02-04
Oh no. I was almost excited when I saw [SOLVED].

Hope you haven't lost data.

---

### Post by john.kreelman on 2010-02-05
In hindsight I thought that I would mark this unsolved until I've done some more research on it.

---

### Post by knurledflanges on 2010-02-05
Just a thought, and I'm not a hardware expert or even an intermediate Linux user, but have you thoroughly checked all your BIOS settings? I don't know if this is really possible or not, but maybe some setting got changed automatically when you put a PATA drive in the mix, but didn't get changed back automatically, or somehow something else went wrong in BIOS-land. Maybe even try resetting the CMOS (making sure to note all settings first).

---

### Post by john.kreelman on 2010-02-05
> **knurledflanges said:**
> but have you thoroughly checked all your BIOS settings? .

Had a good beakie when this all occured but couldn't see owt wrong or changed. I really get a gut feeling it's to do with the original vista format.

---

### Post by audiomick on 2010-02-05
> **john.kreelman said:**
> Had a good beakie when this all occured but couldn't see owt wrong or changed. I really get a gut feeling it's to do with the original vista format.
I'd be guessing something along those lines too. I can't help feeling that you have managed to create a completely unanticipated sequence of events. Along the lines of "if I do this, but not before doing that or after doing the other, and hold my left hand just right, then all the wheels fall off..."

---

### Post by SecretCode on 2010-02-05
> **john.kreelman said:**
> I really get a gut feeling it's to do with the original vista format.

That seems likely. Could be like this: Vista formatted for "hybrid GPT" (google it and you'll know more than I do about it in 5 minutes); XP converted it to basic MBR but in place left all the extra sectors that GPT requires; something - ubuntu or gparted or leprechauns - saw these extra sectors and said 'OK, this is a damaged GPT, I'll just fix it by resetting these bytes here'; XP said :o

---

### Post by oldfred on 2010-02-05
I think secretcode hit the nail on the head.

Some more info here:
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
Win XP - Data Disk only [1] MBR takes precedence in hybrid MBR configuration.
Unless otherwise noted, OSes provide precedence to the GPT data when a hybrid MBR configuration is encountered.

---

### Post by john.kreelman on 2010-02-05
> **audiomick said:**
>  "if I do this, but not before doing that or after doing the other, and hold my left hand just right, then all the wheels fall off..."

Made me giggle!!! Yes, only me. The wheels not only fell off but went opposite to the direction to which they were spinning.

All drives bit wiped and loaded with data as before and nothing lost so all's well.

---

### Post by audiomick on 2010-02-05
> **john.kreelman said:**
> 
All drives bit wiped and loaded with data as before and nothing lost so all's well.
Great. Now don't do it again....
The live CD is your friend for trying things out. ;)

---

### Post by john.kreelman on 2010-05-26
Just to update all you kind people. Have tried to replicate this to no avail. Only thing that I found that isn't really the issue here, was that if you format the drive in the the linux native it isn't then (if you pop it into a machine) readable under windows which I guess is understandable. The only thing then is that a windows install won't even recognize the disc even to format it. I had to bit erase the drive with kill disk and then ntfs it under windows. Any way thanks all for you time. Regards.

---


---
title: "[SOLVED] Error creating partition"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by WASHAD on 2008-12-24
Pardon me if this is a duplicate post, but my first attempt didn't appear. 

I'm trying to install Ubuntu onto my work computer (XP at work, Ubuntu at home). I'm having a problem that I've not seen before (I've done a few installs on other computers.)

I keep getting an error that says something like "error writing partition to disk". This happens even if I manually set up partitions. 

I'm sure I'll need to provide you with more information, but I need help knowing what that might be and how to get it to you. 

Thanks, 

SteveJ

---

### Post by lykwydchykyn on 2008-12-24
Are you trying to set it up dual-boot? Have you resized the Windows partition?

---

### Post by albinootje on 2008-12-24
> **WASHAD said:**
> 
I keep getting an error that says something like "error writing partition to disk". This happens even if I manually set up partitions. 

I'm sure I'll need to provide you with more information, but I need help knowing what that might be and how to get it to you. 


Please post the output of :
```

sudo fdisk -l
mount

```
And you can install gparted during the "live session" from the Ubuntu installation cdrom like this :
```

sudo apt-get install gparted

```
And use it like this :
```

sudo gparted

```

---

### Post by WASHAD on 2008-12-24
Thanks for the response. I get the same error when I try to resize the partition as well. 

SteveJ

---

### Post by 73ckn797 on 2008-12-24
> **WASHAD said:**
> Thanks for the response. I get the same error when I try to resize the partition as well. 

SteveJ


I will assume that you are unmounting the drive to try to do this? I do not think you can make any changes without first unmounting the drive from within Gparted.

---

### Post by albinootje on 2008-12-24
> **WASHAD said:**
> Thanks for the response. I get the same error when I try to resize the partition as well. 


If you've tried gparted you should take a look at error-messages in the terminal that you have started gparted from, and in gparted itself (like e.g. the key symbol icon), and report back about those errors. 
Remarks like "Doesn't work again" are not so useful as "It says it can't work on /dev/sdc1 because it's mounted".
And indeed your partitions cannot be mounted if you want gparted to work on them, so booting from a Linux live-cd is recommended (The Ubuntu installation cdrom will do).

---

### Post by WASHAD on 2008-12-24
> **albinootje said:**
> Please post the output of :
```

sudo fdisk -l
mount

```


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2   *          10       14593   117145980    7  HPFS/NTFS

---

### Post by WASHAD on 2008-12-24
H'mm, I've installed Ubuntu several times and am doing it the same way. I haven't had to unmount in the past. 

Basically, I am using the live CD and running through the install from there. When I get to the partition section, I drag the slider so that I have avout 35Gb for the Ubuntu portion and go from there. 

Thanks, 

SteveJ

---

### Post by albinootje on 2008-12-24
> **WASHAD said:**
>  Basically, I am using the live CD and running through the install from there. When I get to the partition section, I drag the slider so that I have avout 35Gb for the Ubuntu portion and go from there. 

Can you please try gparted in a terminal while using the Ubuntu installation cdrom ?
```

sudo gparted

```
The Ubuntu partitioner software used by default during the installation doesn't give any useful error-messages, hence the question to use gparted to try to do the resizing instead.

---

### Post by WASHAD on 2008-12-24
> **albinootje said:**
> Can you please try gparted in a terminal while using the Ubuntu installation cdrom ?



Ok, it fails with Gparted as well. I tried attaching the error file - I'm not sure it took. I'll paste it here as well. 






========================================================================


GParted 0.3.8

Libparted 1.8.9

Shrink /dev/sda2 from 111.72 GiB to 72.66 GiB  00:00:17    ( ERROR )
     	
calibrate /dev/sda2  00:00:01    ( SUCCESS )
     	
path: /dev/sda2
start: 144585
end: 234436544
size: 234291960 (111.72 GiB)
calculate new size and position of /dev/sda2  00:00:00    ( SUCCESS )
     	
requested start: 144585
requested end: 152521109
requested size: 152376525 (72.66 GiB)
new start: 144585
new end: 152521109
new size: 152376525 (72.66 GiB)
check filesystem on /dev/sda2 for errors and (if possible) fix them  00:00:04    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda2
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 119957479936 bytes (119958 MB)
Current device size: 119957483520 bytes (119958 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 26402 MB (22.0%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 23796 MB 0
Multi-Record : 94612 MB 41745
$MFTMirr : 59979 MB 1
Compressed : 82252 MB 41845
Ordinary : 89794 MB 17340
You might resize at 26401292288 bytes or 26402 MB (freeing 93556 MB).
Please make a test run using both the -n and -s options before real resizing!
shrink filesystem  00:00:06    ( ERROR )
     	
run simulation  00:00:06    ( ERROR )
     	
ntfsresize -P --force --force /dev/sda2 -s 78016780799 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 119957479936 bytes (119958 MB)
Current device size: 119957483520 bytes (119958 MB)
New volume size : 78016774656 bytes (78017 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 26402 MB (22.0%)
Collecting resizing constraints ...
Needed relocations : 7191 (30 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1080 > 1024), not yet supported!
Please try to free less space.
check filesystem on /dev/sda2 for errors and (if possible) fix them  00:00:05    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda2
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 119957479936 bytes (119958 MB)
Current device size: 119957483520 bytes (119958 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 26402 MB (22.0%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 23796 MB 0
Multi-Record : 94612 MB 41745
$MFTMirr : 59979 MB 1
Compressed : 82252 MB 41845
Ordinary : 89794 MB 17340
You might resize at 26401292288 bytes or 26402 MB (freeing 93556 MB).
Please make a test run using both the -n and -s options before real resizing!
grow filesystem to fill the partition  00:00:01    ( SUCCESS )
     	
run simulation  00:00:00    ( SUCCESS )
     	
ntfsresize -P --force --force /dev/sda2 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 119957479936 bytes (119958 MB)
Current device size: 119957483520 bytes (119958 MB)
New volume size : 119957479936 bytes (119958 MB)
Nothing to do: NTFS volume size is already OK.
real resize  00:00:01    ( SUCCESS )
     	
ntfsresize -P --force --force /dev/sda2
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 119957479936 bytes (119958 MB)
Current device size: 119957483520 bytes (119958 MB)
New volume size : 119957479936 bytes (119958 MB)
Nothing to do: NTFS volume size is already OK.

========================================

Create Primary Partition #1 (ntfs, 38.09 GiB) on /dev/sda

========================================

Create Primary Partition #2 (linux-swap, 996.22 MiB) on /dev/sda

========================================

---

### Post by WASHAD on 2008-12-25
I'm afraid that this thread might have gotten lost in the Ether....

Anyone else have any ideas for me?

---

### Post by albinootje on 2008-12-25
> **WASHAD said:**
> 
GParted 0.3.8

Libparted 1.8.9

Shrink /dev/sda2 from 111.72 GiB to 72.66 GiB  00:00:17    ( ERROR )


Is your XP-partition pretty full or not ?

Did you defrag your XP-partition ?
It could help if you do.

---

### Post by WASHAD on 2008-12-25
Thanks for the replay, Merry Christmas. 



> **albinootje said:**
> Is your XP-partition pretty full or not ?

Did you defrag your XP-partition ?
It could help if you do.


> Got lots of room left - I'm using about 25G of a 120G drive. 
> I did defrag.

---

### Post by balaknair on 2008-12-25
> **albinootje said:**
> Is your XP-partition pretty full or not ?

Did you defrag your XP-partition ?
It could help if you do.

My thoughts exactly.
Either the drive is badly fragmented, or it doesn't have enough free space, or there are bad sectors/errors, as far as I can make out.
Defragment the drive and run a check-disk-for-errors while logged into XP.

---

### Post by albinootje on 2008-12-25
> **WASHAD said:**
> 

> Got lots of room left - I'm using about 25G of a 120G drive. 
> I did defrag.

Excellent.

Someone else in another thread recommended the gparted live cdrom (or usb) instead of the ubuntu gparted.
Can you try that instead ?
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by WASHAD on 2008-12-25
I'll try, and report back.

---

### Post by WASHAD on 2008-12-25
Hmm...

Tried Gparted off a live CD and get same error.

SteveJ

---

### Post by albinootje on 2008-12-25
> **WASHAD said:**
> Hmm...
Tried Gparted off a live CD and get same error.


Ouch :(
Can you try some resizing software in XP ? That might give other and perhaps more interesting error messages.

---

### Post by WASHAD on 2008-12-25
It looks like I'll have to. I wonder how Dell tech support would feel about my complaining that I can't resize my hard-drive so that I can install Linux :)

---

### Post by -kg- on 2008-12-25
You indeed have a strange problem.  First, read [https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition").  I have just re-written that section, and it might hold some information that you've overlooked.

A couple of things I saw concerned me, though.  In one of your posts I say the line:

> Compressed : 82252 MB 41845

Are you using disk compression on any or all of your partition?  Are you using encryption?  Disk Spanning?

You say you are attempting to manipulate your partitions on your work computer.  Do you have full control of your work computer?  I have heard tell that there is a way on some computers to put a password on any disk partitioning operations.  Is your computer set up that way, and do you have the password(s)?

I'm trying my best to wrap my mind around the problem and figure out what's wrong.  Can you boot to the Live CD and take a screenshot of the GPartEd Window?  It would help if I could see the partitions and the entries under the graphics.

---

### Post by WASHAD on 2008-12-26
It is certainly possible that there are some restrictions placed on partitioning. I didn't know that was possible. 

I'll get the screen shots and report back. 

SteveJ

---

### Post by -kg- on 2008-12-26
You indeed have a strange problem.  First, read [https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition").  I have just re-written that section, and it might hold some information that you've overlooked.

A couple of things I saw concerned me, though.  In one of your posts I say the line:

> Compressed : 82252 MB 41845

Are you using disk compression on any or all of your partition?  Are you using encryption?  Disk Spanning?

You say you are attempting to manipulate your partitions on your work computer.  Do you have full control of your work computer?  I have heard tell that there is a way on some computers to put a password on any disk partitioning operations.  Is your computer set up that way, and do you have the password(s)?

I'm trying my best to wrap my mind around the problem and figure out what's wrong.  Can you boot to the Live CD and take a screenshot of the GPartEd Window?  It would help if I could see the partitions and the entries under the graphics.

---

### Post by -kg- on 2008-12-26
Whoops!  Sorry about the double post!

:lolflag:

---

### Post by WASHAD on 2008-12-26
Kg;

Attached is the screen-shot from GParted. 

SteveJ

---

### Post by -kg- on 2008-12-26
Well, that answered a couple of questions.  No apparent reason that you shouldn't be able to resize the partition.

The only other things I can think of is that one (or more) of my list is the case.  I don't think you have disk-spanning enabled (do you have more than one hard drive?), so it's either the volume is compressed, encrypted (though I don't know why that would make you unable to resize it) or it's password protected against partition operations.

One thing I noticed from a previous post:

> I will assume that you are unmounting the drive to try to do this? I do not think you can make any changes without first unmounting the drive from within Gparted.

No matter under what circumstances you use GPartEd, you will not be able to perform operations on a partition that is mounted.  You won't get an error...any operations that you can't perform on the partition will be unavailable (i.e., grayed out) except for the selection to unmount the volume.  If that were the problem, you would have done it...you would have had no other choice.  This is in the Wiki page I pointed you to earlier.

I have read somewhere that there are standard BIOS passwords that various companies use...yep, here it is:

[http://www.measham.force9.co.uk/reference/biosp.htm]("http://www.measham.force9.co.uk/reference/biosp.htm")

I don't know whether this will help with your particular problem, and certainly pay attention to the caveats on the page.

---

### Post by WASHAD on 2008-12-26
KG;

Thanks again for all of your help. I went into the bios, and there are no passwords set. Everything seems to be wide open to allow my modification.

As far as disk-spanning goes, I'm not entirely sure how to check that but it doesn't seem likely that the company I work for would go to that kind of effort. What would be the purpose. 

As to the other comments, there is only one hard drive on the system. 

Thanks, 

SteveJ

---

### Post by -kg- on 2008-12-26
> As far as disk-spanning goes, I'm not entirely sure how to check that but it doesn't seem likely that the company I work for would go to that kind of effort. What would be the purpose.

As to the other comments, there is only one hard drive on the system. 

I thought as much.  Disk spanning involves extending one partition across two or more physical hard drives.  If there's only one hard drive installed, it wouldn't be possible to apply disk spanning.

If you can't find any other way to shrink that partition, the final alternative would be to back up the drive (not the partition...the drive...you want to be able to boot to Vista again after performing the following) to an image file on another drive (another hard drive or to CD-R/DVD-/+R), delete the partitions on the whole drive, then recreate them exactly the same size and configuration.  Once you do that, you can reload the image file to the disk and it will be recreated.  Once recreated, you should be able to resize the partition.

You might not want to do the above to a work computer, though.  There is always the possibility that the above process would be unsuccessful, and I imagine that your company wouldn't quite appreciate that.

I think that I might need to write a special "Back Up And Restore" section to the Wiki next.  I would need to do a little experimentation with it (I have a hard drive specifically for experimentation installed in my desktop) and be sure of what I speak, but it would be a major project, as I would have to make OS installations to that disk then experiment with backing it up using Linux tools to back up and then restore.

I just can't understand why you aren't able to resize that partition.  It might take a call to Dell support, if nothing else, to ask if there's such a thing as a password to be able to perform disk partitioning operations.  It might not be in BIOS...it might be whatever process they used to initially create the partitions.

I've been performing disk partitioning operations for many years now, and frankly, this one has me stumped.

---

### Post by WASHAD on 2008-12-28
When I get off vacation, I'll give Dell a call (I'm in Mexico right now). If they give me anything useful, I'll be sure to post it for the benefit of others. 

Thanks again;

SteveJ

---

### Post by -kg- on 2008-12-28
By all I've read Googling the subject (and this is true for Dell, as well) some manufacturers set a hard drive password to lock the hard drive in their systems.  If you install another hard drive, this will be locked as well, since this is done by the BIOS and is set in the hard drive's firmware.

There are quite a few companies that offer to "crack" the hard drive password (for a fee, of course!), but what I've read indicates that you should be able to get the password for the computer from the manufacturer.

Good luck!

---

### Post by lykwydchykyn on 2008-12-29
I don't know, I've run into situations like this before where I just couldn't write the partition; usually blanking the drive fixed it (at the expense of losing all the other partitions), though I don't know a less drastic solution.

---

### Post by albinootje on 2008-12-29
> **lykwydchykyn said:**
> I don't know, I've run into situations like this before where I just couldn't write the partition; usually blanking the drive fixed it (at the expense of losing all the other partitions), though I don't know a less drastic solution.

I wonder what happens if you use cloning software to backup, then wipe the disk, turn off the "hardware locking" in the BIOS, and restore from backup.
Is there some hidden software involved on the hard disk itself or is it all BIOS controlled ?

---

### Post by lykwydchykyn on 2008-12-29
> **albinootje said:**
> I wonder what happens if you use cloning software to backup, then wipe the disk, turn off the "hardware locking" in the BIOS, and restore from backup.
Is there some hidden software involved on the hard disk itself or is it all BIOS controlled ?

I've never encountered a locked disk, but I've always understood that it happened on the disk hardware level, not in the computer's BIOS or on the drive itself (i.e. -- in software).  Apparently there are scammers on ebay selling locked disks, and you can't do anything with them unless you have a special unlocking utility from the drive manufacturer and the unlock code.  I'm kind of hazy on the whole thing.

What I've encountered is usually just something goofed up in the partition table that prevents the drive from being altered.  Zeroing out the drive usually fixes this.  

I would imagine your strategy might work, but it depends on how you image it.  A bit-for-bit copy (dd style) is going to retain any issue with the partition tables, so you'd want to just grab the partition.  That can be potentially problematic, though, especially if you alter the size or location on disk of an ntfs boot partition.

---

### Post by WASHAD on 2008-12-29
None of my options sound very appealing since this is a work machine. I think I'll just have to settle for WUBI (which is what I've been using for the last few days). My computer is fast enough that I don't notice any performance issues. The only inconvenience is the inability to hibernate. 

Thanks everyone for your help on this.

---

### Post by -kg- on 2008-12-30
> I've never encountered a locked disk, but I've always understood that it happened on the disk hardware level, not in the computer's BIOS or on the drive itself (i.e. -- in software). Apparently there are scammers on ebay selling locked disks, and you can't do anything with them unless you have a special unlocking utility from the drive manufacturer and the unlock code. I'm kind of hazy on the whole thing.

Nor have I, though I have dealt with the issue once or twice.  I've Googled the issue and from what I have read this is an issue with certain computer (especially laptop) manufacturers trying to prevent the "appliance operators" (those with absolutely no technical computer skills) from screwing up their computers by trying to do things they shouldn't be trying to do (and thereby giving their warranty repair centers no end of headaches :) ).

Yes, by what I've read, the disks are locked in the firmware of the hard drive itself, and it requires the password used in locking the hard drive to unlock it.  There is freeware available to unlock these disks, though you will need the password used to lock it in order to unlock it. (I couldn't find the link to the site that had this freeware, but I did find it through Google)

I don't know anything about scammers selling locked disks on Ebay, but it might be that they don't realize the drives are locked by the manufacturers.  At any rate, I'm sure that if you call these manufacturers, they would supply you with the password so that you can unlock the disk.

> What I've encountered is usually just something goofed up in the partition table that prevents the drive from being altered. Zeroing out the drive usually fixes this.

I've experienced this as well (and the most recent episode was self generated! :oops: ).  I downloaded Partition Table Doctor (and paid for it), but the partition table (and the partitions themselves) were too far gone for it to be able to fix.  I had to wipe the entire drive and start over (which, really, was a blessing in disguise, since my former XP installation was at the point of being FUBAR, anyway :P ).

> I would imagine your strategy might work, but it depends on how you image it. A bit-for-bit copy (dd style) is going to retain any issue with the partition tables, so you'd want to just grab the partition. That can be potentially problematic, though, especially if you alter the size or location on disk of an ntfs boot partition.

Yes, and any other NTFS partition you might have, if accessed (and/or created) by Windows.  Linux partitions you can usually copy and transfer the files and you'll be good, but Windows has this habit of putting hidden "System files" on the disk, which necessitates a Sector by Sector save of the entire partition, requiring that the receiving partition (the one you are backing up to) be the exact same size (or bigger, but I don't know).

As far as the physical location on the disk, I don't know, but if you back up the entire physical hard drive, then the location would also have to be right, I think.  The MBR would have to point to the right place, if you saved that along with everything else.

> None of my options sound very appealing since this is a work machine. I think I'll just have to settle for WUBI (which is what I've been using for the last few days). My computer is fast enough that I don't notice any performance issues. The only inconvenience is the inability to hibernate.

Yes, I know this was an issue for you.  While I have never used Wubi, the fact that there is an entire sub-section of the Forums on this software indicates to me it is a viable solution to problems similar to yours.  This solves your type of situation without requiring you to alter the partition structure of a hard drive on a computer you don't own. ;)

As for hibernation:  I have been turned off to the idea of hibernation ever since my earlier laptop with Windows ME (you remember...the ***Crash King***?) installed on it.

I used that computer with DeLorme Mapping and a GPS receiver to find my way around while making city deliveries in my area.  In order to shorten reboot time between usages, I would hibernate it.  Well, when you hibernate the computer saves the exact point at which you shut it down.  This is the same as running the computer constantly without a reboot.

Well, you *do* remember the "Crash King," right? (Remember Bill Gates demonstrating it on stage and getting a BSOD? =D> )  I ran the computer without a proper reboot so long and so often that I finally couldn't boot it up...it would come up with a blue screen every time.  I finally had to upgrade the computer and install XP on it.  Ever since then, I've had nothing to do with hibernation on any other computer I've ever had (and I've had a bunch!).

---

### Post by WASHAD on 2008-12-31
Thanks for all of your help. You have really went above and beyond. I have been using Wubi for several days now, and it seems to work really well for me - I suspect that I will leave it that way. Were it my personal computer, I'd work like heck to get the drive unlocked. 

Thanks again, 

SteveJ

---

### Post by WASHAD on 2008-12-31
Thanks for all of your help. You have really went above and beyond. I have been using Wubi for several days now, and it seems to work really well for me - I suspect that I will leave it that way. Were it my personal computer, I'd work like heck to get the drive unlocked. 

Thanks again, 

SteveJ

---


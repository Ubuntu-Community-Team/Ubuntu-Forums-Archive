---
title: "Will installing Ubuntu create a partition in my hard drive?"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by mrtn474 on 2011-03-05
I'm trying out Ubuntu from a live USB flash drive. The Ubuntu website says that once I decide to install it, I "allocate" memory. Does this mean I can choose how much memory out of the mere 97 gigabytes that I have left on the drive of my HP mini 110 Ubuntu will take up? I assume that it doesn't need much, so would 30 gigabytes be a comfortable amount? Or should I split it evenly?

Right, and for the main question, once I decide to install it, will it create a partition on my drive all on its own?

Note: Would be installing netbook edition 10.10

---

### Post by Dutch70 on 2011-03-05
> **mrtn474 said:**
> I'm trying out Ubuntu from a live USB flash drive. The Ubuntu website says that once I decide to install it, I "allocate" memory. Does this mean I can choose how much memory out of the mere 97 gigabytes that I have left on the drive of my HP mini 110 Ubuntu will take up? I assume that it doesn't need much, so would 30 gigabytes be a comfortable amount? Or should I split it evenly?

Right, and for the main question, once I decide to install it, will it create a partition on my drive all on its own?

Note: Would be installing netbook edition 10.10


Welcome to UF mrtn474
Yes you can decide how much when you install & 30 GiB is enough.
You probably want to partition your hdd before you install though. 

Actually 10-20 GiB is enough for the system, just depends on how much you want to put on it.

---

### Post by Mark Phelps on 2011-03-05
If you're running Win7 on the PC (likely guess if it is a new PC), do NOT, repeat, NOT allow the Ubuntu installer to shrink your Win7 OS to make room for Ubuntu.  Doing so is asking for trouble, and if you're one of the unfortunate ones, you risk rendering your Win7 unbootable as a result.

Much better approach is to go into Win7 Disk Management and shrink the Win7 OS partition from there.  Leave the unallocated space alone after that.  The Ubuntu installer can then format that space as needed.

Also, when in  Disk Management, look to see if you already have four partitions (Win7 calls them Drives).  If you do, you can not simply shrink the OS and create another partition because four is the limit you have.  If you charge ahead and do that, you risk turning your Win7 machine into Dynamic Disks -- something you do NOT want to do.

---

### Post by mrtn474 on 2011-03-05
> **Mark Phelps said:**
> If you're running Win7 on the PC (likely guess if it is a new PC), do NOT, repeat, NOT allow the Ubuntu installer to shrink your Win7 OS to make room for Ubuntu.  Doing so is asking for trouble, and if you're one of the unfortunate ones, you risk rendering your Win7 unbootable as a result.

Much better approach is to go into Win7 Disk Management and shrink the Win7 OS partition from there.  Leave the unallocated space alone after that.  The Ubuntu installer can then format that space as needed.

Also, when in  Disk Management, look to see if you already have four partitions (Win7 calls them Drives).  If you do, you can not simply shrink the OS and create another partition because four is the limit you have.  If you charge ahead and do that, you risk turning your Win7 machine into Dynamic Disks -- something you do NOT want to do.
It turns out that I already have four partitions on my drive. My C drive, the others are labeled "SYSTEM," "RECOVERY," AND "HP TOOLS." Since I've already reached the four partition limit on my drive, like you said, does this mean that I have to delete one of them?

---

### Post by Jerry N on 2011-03-05
> **mrtn474 said:**
> Since I've already reached the four partition limit on my drive, like you said, does this mean that I have to delete one of them?

You got it - you will have to use the Win 7 utilities to shrink the Win 7 partition and then delete a partition and re-allocate the available space as an extended partition.  You can then create logical partitions in the extended partition where Ubuntu can be installed.  Which partition to delete?  If you delete the restore partition you have lost the capability to reinstall Windows if something goes wrong.  I don't know what happens if you delete the HP Tools partition but it appears to me to be the only viable candidate.  I haven't had the nerve to do that to my Mini 210 yet.  

Jerry

---

### Post by Knightwise on 2011-03-05
The other alternative is that you can use the wubi installer. This will install ubuntu on your windows system withput tpuching the partition scheme. 

[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

---

### Post by mrtn474 on 2011-03-05
Right now I'm reading the HP forums to see if it would be a bad a idea to delete the HP TOOLS partition.

I've also read about using wubi, which would install linux within my win7 system, right? would that still give me the full ubuntu experience? I feel that it would rely on windows.

---

### Post by Dutch70 on 2011-03-06
> **mrtn474 said:**
> Right now I'm reading the HP forums to see if it would be a bad a idea to delete the HP TOOLS partition.

I've also read about using wubi, which would install linux within my win7 system, right? would that still give me the full ubuntu experience? I feel that it would rely on windows.

Wubi runs nice, but you are correct. It would totally rely on windows.

 Can you run the live cd, open Gparted & take a screenshot of your partitions. Attach them to your next post. 

 I'm wondering if you can back up the HP Tools partition & put it into a logical parition later. A pic would be helpful.

---

### Post by mrtn474 on 2011-03-06
I'm not exaclty sure what you meant, but here is a screen shot of my partitions.

I read an HP forum, and it said that the HP tools are not *that* important. However, I still don't have the guts to remove it.

Please excuse me, I'm a total noob :\

Note: just as a reminder, I'm doing this in a netbook. I already have Ubuntu installed on a live USB, which means I've already tried it.

---

### Post by Dutch70 on 2011-03-06
> **mrtn474 said:**
> I'm not exaclty sure what you meant, but here is a screen shot of my partitions.

I read an HP forum, and it said that the HP tools are not *that* important. However, I still don't have the guts to remove it.

Please excuse me, I'm a total noob :\

Note: just as a reminder, I'm doing this in a netbook. I already have Ubuntu installed on a live USB, which means I've already tried it.

Wow, HP Tools is using a whopping 9MB of disk space & has it's own primary partition. Somebody smack HP. 

I don't feel comfortable advising you on this, but if you have your windows cd, you may want to use the recovery parition to install Ubuntu. It is just about the perfect size. 

On the other hand, an external hdd may be the way to go.

There may be some helpful info, or links here...
[http://h30434.www3.hp.com/t5/Notebook-Operating-systems-and/Hard-Disk-Partition/m-p/395431]("http://h30434.www3.hp.com/t5/Notebook-Operating-systems-and/Hard-Disk-Partition/m-p/395431")

---

### Post by Jerry N on 2011-03-06
> **Dutch70 said:**
> I don't feel comfortable advising you on this, but if you have your windows cd, you may want to use the recovery parition to install Ubuntu.

The OP has a netbook - no CD/DVD.  

Jerry

---

### Post by howefield on 2011-03-06
Just another option whilst you research and get comfortable with what you need to do.

You might be able to create a startup disk with persistence on your flash drive. This means you can save data and settings to it and they will be there next time you use it, unlike the Live CD/USB environment.

If the drive is decently sized, you could even run a full install from it.

Not for the long term, just something to consider.

---

### Post by Dutch70 on 2011-03-06
> **Jerry N said:**
> The OP has a netbook - no CD/DVD.  

Jerry

So what you're saying is, he has no options to reinstall windows if it should fail? Maybe I should have said "back up" but thank you for correcting me.

---

### Post by howefield on 2011-03-06
> **Dutch70 said:**
> So what you're saying is, he has no options to reinstall windows if it should fail?

Probably not if he uses the Recovery partition as has been suggested.

It would be unusual to have an included optical drive with a netbook, short of buying an external unit.

---

### Post by Jerry N on 2011-03-06
> **Dutch70 said:**
> So what you're saying is, he has no options to reinstall windows if it should fail? Maybe I should have said "back up" but thank you for correcting me.

I don't know if the HP netbook can build a restore image on a USB flash drive or not.  I will have to get mine out and try it.  I think I saw somewhere that HP sells a USB flashdrive with a recovery image but I don't know if that is correct.

One could use Clonezilla to create a disk image to an external hard drive (or USB drive?) and then, if necessary, recreate the hard drive from that image.  I think Win7 may have something like that built in.


Jerry

---

### Post by Jerry N on 2011-03-06
More information:  The user of an HP Mini 210 can create one (and only one)Recovery Media set, either on DVD(s) or a USB flash drive.  DVD(s) would of course require an external USB connected DVD drive.  The Recovery Media will restore the computer to its original factory condition.  A 16gb flash drive will probably be required.

The utility to create the Recovery Media set is accessed through through the Recovery Manager and should be done immediately after the computer is set up and certainly before any actions such as partition modification are undertaken.  

The problem, of course, is knowing where you stored the recovery media when the time comes that it is needed.  If the media was delivered with the computer, like it should have been, the user has exactly the same problem.  

Duct tape the flash drive to the lid of the computer? :P:P:P

Jerry

---

### Post by Dutch70 on 2011-03-06
> **Jerry N said:**
> More information:  The user of an HP Mini 210 can create one (and only one)Recovery Media set, either on DVD(s) or a USB flash drive.  DVD(s) would of course require an external USB connected DVD drive.  The Recovery Media will restore the computer to its original factory condition.  A 16gb flash drive will probably be required.

The utility to create the Recovery Media set is accessed through through the Recovery Manager and should be done immediately after the computer is set up and certainly before any actions such as partition modification are undertaken.  

The problem, of course, is keeping knowing where you stored the recovery media when the time comes that it is needed.  If the media was delivered with the computer, like it should have been, the user has exactly the same problem.  

Duct tape the flash drive to the lid of the computer? :P:P:P

Jerry

:lolflag: 

That's a real bummer though! I had no idea.

---

### Post by mrtn474 on 2011-03-06
Thank you all for the replies, I really appreciate it :)

Some of the advice that has been suggested seems helpful, but also I can't do most of it since I can't spend any money, and I do not wish to install Ubuntu externally.

I've been reading on the HP forums (Edit: actually, i got this info from the forums: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02085554&tmp_task=solveCategory&lc=en&dlc=en&cc=us&tool=&query=dv6-3107ax&product=4319313]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02085554&tmp_task=solveCategory&lc=en&dlc=en&cc=us&tool=&query=dv6-3107ax&product=4319313")) about this partitioning stuff. The website said the following:

> This document pertains to all HP notebook PCs with Recovery Manager.
The HP Recovery Manager loses functionality after performing one or more of the following actions on a hard disk drive (HDD) partition.
1. Extend, shrink, or delete volume to any partition.
2. Create or delete any partition.
3. Add mirror to any partition.
4. Change drive paths to any partition.

Additionally, an error message from the Recovery Manager appears after pressing F11 while the computer is loading.

"Error: Recovery Manager cannot run from the hard drive. Recovery Manager must be run using recovery media to perform a Factory Reset"

Create or Obtain Recovery Media
To resolve this issue, create recovery media (CD/DVD) prior to changing any hard drive partition. If recovery media is not available, obtain the appropriate System Software Requirement Disks (SSRD) by contacting HP.

So since this is a netbook, and I don't have an external CD/DVD drive, can i just back up everything to my free drop box account? I only need to back up my files right? not the entire system?

---

### Post by Jerry N on 2011-03-06
You can, and should, do the backup but that won't help you recover your Windows 7 operating system if you somehow trash your hard drive.  I wasn't aware of the possibility of screwing up the recovery manager if you resize a partition.

I think I will forget about putting Ubuntu on my HP Mini 210.  I don't use it much anyway.  

Jerry

---

### Post by Dutch70 on 2011-03-06
This seems like a perfect situation for a wubi install. It runs just as good. The down side is, if your windows crashes, Ubuntu will crash with it. It doesn't diminish the capabilities of Ubuntu AFAIK. My g/f has it on her pc, and it works great. 

Also, if windows crashes & takes Ubuntu with it, It'll be a perfect time to do a full install of Ubuntu. 

Best regards

---

### Post by mrtn474 on 2011-03-07
haha, those were such optimistic posts lol. 

Thank you so much for your help :D

I'm going to look into wubi.

---


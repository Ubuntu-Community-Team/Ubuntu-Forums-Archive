---
title: "RAID 1 during Ubuntu 9.04 Setup...Possible?"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by WoodySmith on 2009-07-16
Ok here is my dilemna. I am a total absolute newbie with Linux. I am setting up a computer to do some data handling (ftp). I have an Intel 975XBX MB with a P4 Extreme 3.73 GHz processor. I have installed 2 identical 120 GB G.Skill Solid State drives and 2 identical 1 TB WD Caviar Black drives. I would like to install a RAID 1 to the solid state drives and install Ubuntu 9.04. Then I would like to use the 1 TB drives as my data storage for the ftp site using RAID 1 to mirror the data uploaded there.
 
Task #1 Installing Jaunty with the alternate install CD (it was d/l'd yesterday and checked for errors) onto clean never before used solid state drives and setting up RAID 1. I have tried it with "fake raid" as several articles I've read said this should work. When I get to the point in my install that lets me decide to initiate the ATA Raid Devices I answer "Yes" and I get the menu which asks me:
 
Help with partitioning
<blank space>
Undo disk partition changes
Write changes to partition and continue
 
Not word for word I know but its close. Anyway, if I select the screen Undo partition changes I see a blue screen with a white area at the bottom that allows me to type text but no commands are recognized. I can open a shell (CTRL+ALT+F2) but I have no idea what to do with it. The articles I have researched all say at this point I should be good to go. Obviously I am not.:(
 
If I select the "write changes...." option I get an error window in red which tells me that there is no root system and to return to the partioner and change this. *sigh*
 
I am in some kind of loop that is telling me that the Jaunty install defintely does NOT recognize my "fake raid" or I am apparently doing something wrong. Any ideas?
 
Task#2 If I attempt the software RAID 1 do I need to delete the RAID sets in the on-board RAID BIOS screens?
 
No matter what I do my drives are seen as sda, sdb, sdc, sdd when I use the standard install CD. Is it easier just to do an install to a single drive and then implement RAID 1 on the solid states AFTER Jaunty is installed?
 
Big caveat is I can not connect to a network until Jaunty is installed because I have to use wvdial to configure a USB verizon modem which I am quite familiar with by now. But I do have other machines that I can d/l and many USB thumb drives to transfer data from. Any help with this would be greatly appreciated.

---

### Post by presence1960 on 2009-07-16
I am not versed in raid but the error about no root partition set is a common mistake. When you set partitions you must set parameters also such as "use as" (which selects filesystem type) and mountpoint. For mountpoint on your root partition select / 

you should then be able to continue.

---

### Post by ATSystems on 2010-05-03
Greeting folks!

Sorry to bump such an old thread but I am having an identical problem to woodysmith, and my google-fu is failing me. Ubuntu does not appear to be recognising my drives during install, which, apart from having windows 2003 on them, seem to be in perfect health otherwise.

I am on a HP Proliant DL140 G3 with 2x 80Gb disks, wishing to set up as an FTP and local file server. At the same point in the install I get the same screen, with the same options..

Help with partitioning
<blank space>
Undo disk partition changes
Write changes to partition and continue

I read over at [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) that this server has a "fake RAID", some sort of BIOS voodoo that makes SATA drives appear as a RAID. This seems to fit the description as during boot I get no options to access a RAID BIOS via <alt> + S or similar prompts, and standard BIOS makes no mention of RAID anywhere.

I suspect if I could access a partition manager from the install disk I could do it all manually (assuming a partition manager would see the drives), but there does not appear to be an option for this in the menu's or according to google. I'd pull down a live CD but i'm on a wireless dongle, not so good. I might go drop the desktop disk in and see if it has the same problem or not now I'm thinking, this may clarify where the fault lies.

My main query at this time though, is there a partition manager accessible on the install disk, or do any of you know how to get around this pesky problem?

TIA!

[edit; Jaunty saw each drive and allowed me to partition them individually, but I would still prefer to set them up as RAID 1 if anyone can advise?]

---


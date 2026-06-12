---
title: "Dual Boot Cranks up!!! - XP &amp; Lucid"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by randolf_ambrose on 2010-05-15
hi guys...

i've lucid workin so good in my notebook...

i want XP also for some pupose...

[IMG]http://lh6.ggpht.com/_CEPbkas_2SM/S-5Gm8EwJJI/AAAAAAAACpg/rpr98WjpfBM/s800/partition.png[/IMG]

i want to install XP in sda5... but every time i run the xp setup, select that volume and restart for installation, i get black screen, not even boot menu...

and even after selecting sda5 for xp installation which has 5G, xp gets installed in sda2!!!

what could be wrong...

i tried several times and had to reinstall my lucid everytime...

i dont wanna risk it anymore...

what could be wrong... how can i make sure that i can retrieve my ubuntu???

---

### Post by conradin on 2010-05-15
verify your xp media is intact.

---

### Post by randolf_ambrose on 2010-05-15
> **conradin said:**
> verify your xp media is intact.

i dont see any problems with that...

what i'm wondering is how the bootloader or whatever goes to sda2!!!

because after copying windows files and restart for installation, i get black screen, not even the screen to choose between windows setup or my lucid...

will, changing the boot flag to my lucid partition work???

---

### Post by randolf_ambrose on 2010-05-15
someone please help!!!

---

### Post by 4Orbs on 2010-05-15
"I think" the problem is that Windows automatically looks for the first Primary partition with the required filesystem format. Sda2 is a Primary partition and sda5 is a logical partition within an extended partition. Therefore Windows chooses sda2 as its home. I could be wrong.

EDIT: If this were my hdd, I would first delete the Ubuntu installation partitions (Meaning the entire extended partition. Now would be a good time because Ubuntu was just installed and there are no important files saved yet). Then I would create a Primary partition of the desired size for XP (which I presume would be the size of your current sda5). That newly created Primary partition would be flagged bootable and should be automatically named sda1. Then the remaining unallocated space located between sda1 and sda2 could be made the extended partition to contain a new install of Ubuntu.

EDIT2: And if you do make the Ubuntu install inside an extended partition, you would be able to make three logical partitions which could contain a separate / and /home partition in addition to the swap partition. Or as the post below by bennachie suggests, make just three new primary partitions (which would not allow for a separate / and /home partition for Ubuntu). And, as suggested below, Windows should be installed first, then Ubuntu. Obviously sda2 is already filled with important stuff so be careful not to erase that one.

EDIT3: It appears you would like to keep your current Ubuntu installation because you already have it tweaked and working nicely. It is possible to keep it and work around it but that would complicate things greatly. If you don't mind installing Ubuntu one more time, it's really the better option.

---

### Post by bennachie on 2010-05-15
@4Orbs

I'm pretty sure your understanding is correct.

Perhaps randolf_ambrose should simply start from scratch. He might, for example, create four primary partitions (sda1 formatted as NTFS, with, say, 15GB for XP, sda2 with 25GB for Lucid, sda3 for a 4GB swap space, and sda4, formatted as FAT32, using the rest of the disk for shared data). It would be easiest to do the Windows installation first, followed by the final Lucid installation.

---

### Post by jaycee23 on 2010-05-15
Just throw in my penny's worth

I like to go for 3 primary partitions
sda1 - NTFS for Windows
sda2 - NTFS / FAT (depending how large your files would be) for Data (to be shared between Windows and Lucid)
sda3 - Ext4 as a extended partition split into 3 to contain /, /home and swap

Totally agree install windows first - can do the other way around but requires a bit more messing around but this link 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

will help if you go for this.

---

### Post by randolf_ambrose on 2010-05-15
> **4Orbs said:**
> "I think" the problem is that Windows automatically looks for the first Primary partition with the required filesystem format. Sda2 is a Primary partition and sda5 is a logical partition within an extended partition. Therefore Windows chooses sda2 as its home. I could be wrong.

EDIT: If this were my hdd, I would first delete the Ubuntu installation partitions (Meaning the entire extended partition. Now would be a good time because Ubuntu was just installed and there are no important files saved yet). Then I would create a Primary partition of the desired size for XP (which I presume would be the size of your current sda5). That newly created Primary partition would be flagged bootable and should be automatically named sda1. Then the remaining unallocated space located between sda1 and sda2 could be made the extended partition to contain a new install of Ubuntu.

EDIT2: And if you do make the Ubuntu install inside an extended partition, you would be able to make three logical partitions which could contain a separate / and /home partition in addition to the swap partition. Or as the post below by bennachie suggests, make just three new primary partitions (which would not allow for a separate / and /home partition for Ubuntu). And, as suggested below, Windows should be installed first, then Ubuntu. Obviously sda2 is already filled with important stuff so be careful not to erase that one.

EDIT3: It appears you would like to keep your current Ubuntu installation because you already have it tweaked and working nicely. It is possible to keep it and work around it but that would complicate things greatly. If you don't mind installing Ubuntu one more time, it's really the better option.

yes... you're right... sda2 is primary partition...

and i've tried everything... i changed the boot flag from sda2 to  sda5, then i tried sda7 also... in both cases, windows copies system files but boot loader goes in sda2...

and when the system restarts to continue installation, on booting, i get black screen with a stupid cursor blinkin...

you guys wont believe... i started doing this in the morning... i'm still on it... by now, i've installed windows 7 three times, windows xp5 times, windows vista 2 times and lucid 4 times!!! i tried everything i know... 

i still am trying... i just made a fresh install of lucid in sda3, swap in sda1 and windows fat32 in sda2...

right now??? honestly, i'm blank... i still wanna do something to make it all work, but i dont wanna keep doing the same...

please someone help me... i'm badly in need of help...

i dont much about boot loaders and all...

---

### Post by oldfred on 2010-05-15
the first install of windows has to be in a primary partition and have the boot flag. Additional installs of windows can be in a logical partition but will boot thru the windows in the primary partition. Make a NTFS primary partition and put the boot on it and it will install there.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by 4Orbs on 2010-05-15
@randolf_ambrose - Is this the only computer you have? I can post a step by step instructions, but you'll need to be able to read it from another computer while working on your notebook. Or you'll need to be able to print the instruction before starting. Or you'll need to write down the instruction before starting.

---

### Post by randolf_ambrose on 2010-05-16
**[FONT="Arial Black"]@4Orbs[/FONT]**

i've two systems... but thats alright... i decided to sacrifice some time of mine... made a backup of my notebook files into my desktp... and gonna follow this...
> **bennachie said:**
> Perhaps randolf_ambrose should simply start from scratch. He might, for example, create four primary partitions (sda1 formatted as NTFS, with, say, 15GB for XP, sda2 with 25GB for Lucid, sda3 for a 4GB swap space, and sda4, formatted as FAT32, using the rest of the disk for shared data). It would be easiest to do the Windows installation first, followed by the final Lucid installation.

i'm gonna format the whole disk... the reason why i'm doing this is because i never got to see 160G as my HDD space since i was using windows... i wanna see 160G... and only Linux can do that... :D

lemme see if everything goes fine!!!

i'll let you guys know!!!

---

### Post by randolf_ambrose on 2010-05-17
guys, i failed again...

i used my lucid cd to create a new partition table...
sda1 > 5G - fat32 - for windows
sda2 > 10G - for lucid
sda3 > 4G - SWAP
sda4 > 141G - fat32 - data storage

and then i tried XP installation cd, selected sda1 (C) as the installation drive and formatted it as nfts and copied system files, then after reboot, got into xp installation, a min or before, my system shuts down!!! its like my HDD is damaged!!!

but i dont find any problem when i install Lucid.

Only when i try to install XP, system shuts down!!! first i panicked thinking if i damaged my HDD with last two days continuous formatting...

guys...

what the hell is happening... i got so pissed off that i just did this...
sda1 - 5G - lucid root
sda2 - 4G - swp
sda3 - 151G - /home

working fine!!!

but can you help me??? i really need xp... my sdricoh card doesnt work in ubuntu and i badly need it to access my MMC...

please help...

---

### Post by randolf_ambrose on 2010-05-17
**@4Orbs**

i really would appreciate it if you could help me with a step by step procedure!!!

i'm on my desktop now with my laptop with lucid just loaded!!!

---

### Post by randolf_ambrose on 2010-05-17
i still cant figure out why my notebook shuts down when i start windows installation!!!

just tried again... this time i partitioned using XP and went on...

still, system shuts down when installation starts...

today also i checked for ways to enable RICOH CARD READER to read my MMC-Pro... no hope...


so i badly need help in solving this mess!!!

please someone help me...

---

### Post by mastablasta on 2010-05-17
First of all i think 5Gb is not realyl enough for XP, especially if you plan to run some programmes on it.
 
You do have original windows don't you?
 
OK so here is what i would do. Simply divide your Hard drive into 2 parts (just for starters). C and D. Make C your winXP drive and give it 10GB. Format it with FAT 32 (or NTFS if you wish). Note here that FAT32 is also limited in full disk size. So maybe you will need to make 3 partitions or just leave one empty. Then go and install windows on it. What notebook you have? Because for some i know they don't really support XP out of box and a setting needed to be changed in BIOS for the WinXP to install. Search the web if there is anythign unusual reported for your model. 
 
 
Once you have windows installed put in the Linux CD and install Linux on your second (D) drive. During linux intalation prepare your disk (the one not taken by XP) to be the way you want it and let it format the disk and install the system. It should work after that. Hopefully.

---

### Post by 4Orbs on 2010-05-17
Hi randolf_ambrose. This stuff can drive a person nuts. You don't have to do everything at once. I suggest just working on getting Windows up and running first, since you are obviously not having any problem dealing with Ubuntu. So for starters, use your Ubuntu live cd to re-do the partitioning.

Note: When you boot into the Ubuntu live cd... as soon as you see the two little pictures at the bottom of the first screen.. hit the space bar to open the Options menu so you can "Try Ubuntu First without Changing Your System". This will take you to the desktop of the live cd. If the gray language selector screen blocks your view of the options menu, hit the Escape key to clear it out of your way (or choose your preferred language). 

Boot up the Ubuntu live cd and get to the desktop, and once there open the System>> Admin>> Partition Editor (or it might be called gparted). Delete each partition, one by one and click the "Apply" at the top of gparted so the entire hard drive shows as unallocated space. I suggest making the Windows partition 20 to 30 gb in size so you won't ever need to rework it, That's also a good size to keep it quite usable. Make sure it's a Primary partition and format it to ntfs so your defragmenter will be able to clean it up quickly on a regular basis. Assign the boot flag to this first partition. Don't do anything with the remaining unallocated space on the drive. When this first partition is ready, quit the Ubuntu live cd and install Windows. Windows should detect the partition. Tell it to do a quick format of the new partition and then install. Now, this is important... if Windows ejects the disk after copying files... or reboots... that doesn't mean the installation is finished. Keep the disk in the drive and hit Enter and XP will continue the installation. You might even need to do this one more time (but I don't think so) before the Windows installation is really finished. When you are certain the installation of XP is complete... reboot into Windows again after removing the install disk, just to be doubly sure and also give it the opportunity to run its automated file system check (but I doubt it will run the check, which is ok).

EDIT: Just to be sure you understand. You are going to remove the current installation of Ubuntu and start from a blank hard drive.

---

### Post by randolf_ambrose on 2010-05-17
> **mastablasta said:**
> First of all i think 5Gb is not realyl enough for XP, especially if you plan to run some programmes on it.
 
You do have original windows don't you?
 
OK so here is what i would do. Simply divide your Hard drive into 2 parts (just for starters). C and D. Make C your winXP drive and give it 10GB. Format it with FAT 32 (or NTFS if you wish). Note here that FAT32 is also limited in full disk size. So maybe you will need to make 3 partitions or just leave one empty. Then go and install windows on it. What notebook you have? Because for some i know they don't really support XP out of box and a setting needed to be changed in BIOS for the WinXP to install. Search the web if there is anythign unusual reported for your model. 
 
 
Once you have windows installed put in the Linux CD and install Linux on your second (D) drive. During linux intalation prepare your disk (the one not taken by XP) to be the way you want it and let it format the disk and install the system. It should work after that. Hopefully.

i dont plan to use XP for anything other than to access my RICOH CARD READER to access my Sony Memory Stick (MMC-Pro)...

i guess 5G is enough since XP would need 1.6GB and drivers would take another .5G... so, i'd say 5G is more than enough in my case!!!

:-D

---

### Post by randolf_ambrose on 2010-05-17
> **4Orbs said:**
> Hi randolf_ambrose. This stuff can drive a person nuts. You don't have to do everything at once. I suggest just working on getting Windows up and running first, since you are obviously not having any problem dealing with Ubuntu. So for starters, use your Ubuntu live cd to re-do the partitioning.

Note: When you boot into the Ubuntu live cd... as soon as you see the two little pictures at the bottom of the first screen.. hit the space bar to open the Options menu so you can "Try Ubuntu First without Changing Your System". This will take you to the desktop of the live cd. If the gray language selector screen blocks your view of the options menu, hit the Escape key to clear it out of your way (or choose your preferred language). 

Boot up the Ubuntu live cd and get to the desktop, and once there open the System>> Admin>> Partition Editor (or it might be called gparted). Delete each partition, one by one and click the "Apply" at the top of gparted so the entire hard drive shows as unallocated space. I suggest making the Windows partition 20 to 30 gb in size so you won't ever need to rework it, That's also a good size to keep it quite usable. Make sure it's a Primary partition and format it to ntfs so your defragmenter will be able to clean it up quickly on a regular basis. Assign the boot flag to this first partition. Don't do anything with the remaining unallocated space on the drive. When this first partition is ready, quit the Ubuntu live cd and install Windows. Windows should detect the partition. Tell it to do a quick format of the new partition and then install. Now, this is important... if Windows ejects the disk after copying files... or reboots... that doesn't mean the installation is finished. Keep the disk in the drive and hit Enter and XP will continue the installation. You might even need to do this one more time (but I don't think so) before the Windows installation is really finished. When you are certain the installation of XP is complete... reboot into Windows again after removing the install disk, just to be doubly sure and also give it the opportunity to run its automated file system check (but I doubt it will run the check, which is ok).

EDIT: Just to be sure you understand. You are going to remove the current installation of Ubuntu and start from a blank hard drive.

man!!! i was waiting for your reply all day...

first of all, thanks for replying...

i've read what you said and already started working on it...
now creating the new partition table using Gparted just the way you said...

will update...

:-)

---

### Post by randolf_ambrose on 2010-05-17
this is what really **** me off...

all that i'm doing is to use 100% of my HDD...

just now i tried the live cd and tried to format my hdd using gparted, there gpared showed only 146G instead of 160G...

what shall i do to get 160G full...

---

### Post by 4Orbs on 2010-05-17
There is a difference between GiB which Ubuntu uses and GB which is what manufacturers of hard drives use as a way of measuring disc space. I'd say you have a full allotment of space regardless what the numbers say.

And you also must consider that the file system (ext4, ntfs) is gonna reserve some of that space for keeping it's own stuff organized.

---

### Post by randolf_ambrose on 2010-05-17
alright... lemme see what happens...

i'll let you know asap...

---

### Post by randolf_ambrose on 2010-05-17
> **4Orbs said:**
> There is a difference between GiB which Ubuntu uses and GB which is what manufacturers of hard drives use as a way of measuring disc space. I'd say you have a full allotment of space regardless what the numbers say.

And you also must consider that the file system (ext4, ntfs) is gonna reserve some of that space for keeping it's own stuff organized.

i'm not able to flag the first partition as boot... not getting that option... it disabled... so is apply function...

so shall i just create the partitions as you said and forget about flagging???

EDIT: ok i had to apply it to be able to flag huh... its going fine now...

---

### Post by 4Orbs on 2010-05-17
When you deleted the partitions, were you able to click the "Apply these actions" so that it actually deleted them and wasn't just holding them in the to-do cue?

Gparted should re-scan the hard drive after each action you apply.

Hope your XP install disc isn't defective or coded in Klingon.

---

### Post by randolf_ambrose on 2010-05-17
same problem again...

i just cant install Windows...

the windows setup disc i'm using is 100% fine... i used that in the morning to setup my desktop... just to make sure, i tried an old copy of windows mediacenter disc, that also stopped in the middle of installation!!!

i dont know if you are getting... i feel this is really weird...

i can install lucid with no probs... no such shutdown or anything...

even after a full hdd formatting, i just cant finish windows installation... 

should i be feeling like mt problems are going off the limits of this forum??? i hope not...

in b/w, i've noticed that windows uses an 8mb of unpartitioned space... is this happening because i've not setup that 8mb???

should i format the entire partition using windows cd???

i'm going crazy!!!

---

### Post by 4Orbs on 2010-05-17
What do you mean by "stopped"? Sometimes it might appear to stop while it is unpacking or writing its files... you may not even get any indication of processor activity while this is going on.

Did the XP install disk confirm that it found the new partition you created? Is the install disk a full blown installation disk or just a recovery disk you made from the XP on your desktop?

Is it possible that your cd drive is fizzling out during the install?

That 8mb of unallocated space it's trying to use sounds as if it wants to set up a separate boot partition or recovery partition. Seems weird to me.

---

### Post by randolf_ambrose on 2010-05-17
> **4Orbs said:**
> What do you mean by "stopped"? Sometimes it might appear to stop while it is unpacking or writing its files... you may not even get any indication of processor activity while this is going on.

what did i mean by STOPPED!!!

what happens when you press the OFF button of your table lamp, it will be switched off in a blink right???

thats what is happening with me...

like the power just goes off...

like something is wrong with my HDD... i've seen systems having this issue due to faulty HDD... but in that case, it should happen all the time, even when i'm installing or using lucid... but this aint that... cos this is happening only with windows...

its funny... i feel like my notebook got addicted to Ubuntu since last 9 months and its spittin out windows!!!

---

### Post by 4Orbs on 2010-05-17
It sounds almost as if your power supply is being overtaxed. I wouldn't be surprised if Windows demands more system resources during installation than Linux.

Looking at your screenshot of gparted in your first post. Is that 8mb unallocated space at the very beginning of the drive still there? Were you not able to create your new partition to include that 8mb of space?

---

### Post by randolf_ambrose on 2010-05-17
> **4Orbs said:**
> It sounds almost as if your power supply is being overtaxed. I wouldn't be surprised if Windows demands more system resources during installation than Linux.

Looking at your screenshot of gparted in your first post. Is that 8mb unallocated space at the very beginning of the drive still there? Were you not able to create your new partition to include that 8mb of space?

till now i couldnt think of an explanation for whats happening... like you said, windows eating up my system's resources could be the thing...

i tried with and without that 8mb... still system get switched off!!!

i just tried partitioning and installing using windows cd... still same problem...

is it time for me to stop hoping for windows and just install my lucid???

---

### Post by 4Orbs on 2010-05-17
My question is still this... When you formatted the hard drive, were you not able to extend the first partition to the very edge of the drive and include that 8mb in the partition? Are you intentionally leaving that 8mb unallocated space at the beginning of the hard drive?

---

### Post by randolf_ambrose on 2010-05-17
> **4Orbs said:**
> My question is still this... When you formatted the hard drive, were you not able to extend the first partition to the very edge of the drive and include that 8mb in the partition?

extend???

didnt do anything like that...

first i created a new partition table...
created first drive with 10G as ntfs...
applied everything... flagged it as boot...
restarted...
tried to install XP in that nfts partition... rest you know!!!

and the good thing is, when you said its eating up my system resources, i unplugged the powercode, reduced screen brightness to min and tried... now i have xp installed in first drive... 

i dont know what should i say about that... its been two days i'm doing this...

now i've just put lucid cd...

i still wonder what was that all about!!!

---

### Post by 4Orbs on 2010-05-17
Do you mean that XP is actually working now? Almost unbelievable.

---

### Post by randolf_ambrose on 2010-05-17
> **4Orbs said:**
> Do you mean that XP is actually working now? Almost unbelievable.

YES!!!

can you believe it...

i've got no explanation on that!!!

all that i can say is that you were right... may be... may be it was the power consumption...

i wish if someone could explain this PHENOMENON???

i started off with windows 98, then i moved to XP, then i had tried Ubuntu Hardy... due to lack of resources such as a high speed internet i had to leave it...then i tried vista... then i tried win7... then jaunty... then karmic... then now lucid...

i have never been to anything unexplainable like this!!!

now...
sda1 - 10G ntfs with xp succesfully installed

how shall i divide the free space??? 150G...

i wish to create
sda2 - 146G ext4 for /
sda3 - swap

but in that case i wont be able to access the 146G through xp right???

so, what could be the right choice... i wish to know whats your suggestion...

---

### Post by jerome1232 on 2010-05-17
With your computer just shutting off like that though, I'd be really worried that your power supply is starting to go out, or there is perhaps a cooling issue.

Maybe put that thing through a stress test and see if it just shuts down, monitor the temperature of the cpu/gpu to rule those out. Maybe run a memtest to see if it sees anything wrong (if I remember right that test is pretty cpu intensive).

---

### Post by 4Orbs on 2010-05-17
If it were my notebook I would make the second partition for shared storage and format to FAT32 and 100 GB and the last two partitions for Lucid and swap.

---

### Post by randolf_ambrose on 2010-05-17
> **jerome1232 said:**
> With your computer just shutting off like that though, I'd be really worried that your power supply is starting to go out, or there is perhaps a cooling issue.

Maybe put that thing through a stress test and see if it just shuts down, monitor the temperature of the cpu/gpu to rule those out. Maybe run a memtest to see if it sees anything wrong (if I remember right that test is pretty cpu intensive).

:D actually... my battery is an old one... only 25% capacity... and i'm on a turion processor... heat cannot be compared with other systems... sometimes i can even touch the bottom of my notebook ;-)

STILL... why UBUNTU runs without a blink!!!

---

### Post by randolf_ambrose on 2010-05-17
> **4Orbs said:**
> If it were my notebook I would make the second partition for shared storage and format to FAT32 and 100 GB and the last two partitions for Lucid and swap.

alright... 
sda1 - 10G ntfs XP
**sda2 - 135G fat32 shared ----> should i mount this as /dos or /windows**
sda3 - 10G ext4 lucid
sda4 - 4G swap

**@4Orbs** thanks a zillion for your help... i really appreciate it... i couldnt have done this without your valuable suggestions...

but i dont think its time to tag this thread as SOLVED??? is it???

---

### Post by jerome1232 on 2010-05-17
One thing, fat has a 4 gb file size limitation, so if you (like me) store huge files (like huge tar archives, or dvd images, virtual machines hard drive files) then fat will not work for you. NTFS support is good enough these days that I don't see a reason to not use ntfs as your data partition.

If you don't store huge files then fat will be fine.

---

### Post by randolf_ambrose on 2010-05-17
> **jerome1232 said:**
> One thing, fat has a 4 gb file size limitation, so if you (like me) store huge files (like huge tar archives, or dvd images, virtual machines hard drive files) then fat will not work for you. NTFS support is good enough these days that I don't see a reason to not use ntfs as your data partition.

If you don't store huge files then fat will be fine.

for me, data storage means MOVIES and MUSIC...

but if i format it was NTFS, will i be able to use it with no issues in ubuntu???

i'm planning to automount that 135G fat32... so if i make it ntfs, will i be able to automount???

i dont think i'd be storing more than 4G files... in future???

---

### Post by randolf_ambrose on 2010-05-17
sda1 - 10G ntfs XP
**sda2 - 135G fat32 shared ----> should i mount this as /dos or /windows**
sda3 - 10G ext4 lucid
sda4 - 4G swap

---

### Post by 4Orbs on 2010-05-17
XP will automatically pick it up and mount it (first it will install the driver, then tell you to reboot).

For Lucid to auto mount, I would specify during Lucid partitioning the mount point as /mnt/data so it wouldn't show a desktop icon.

I actually prefer to use pysdm (Storage Device Manager) in Ubuntu to easily mount and unmount my storage partition and easily change permissions to umask=000 so Windows doesn't block my access to files and folders. Yes, Windows takes control of fat32 partitions, whether you like it or not. (Use Windows, not dos)

@jerome1232 The reason I prefer fat32 is because I often copy files back and forth to my son's Playstation3 which can not read ntfs. My storage partition is on a second hard drive that I sometimes remove from the desktop and put in an external enclosure for portability. Otherwise I would also prefer ntfs.

---

### Post by randolf_ambrose on 2010-05-17
> **4Orbs said:**
> XP will automatically pick it up and mount it (first it will install the driver, then tell you to reboot).

For Lucid to auto mount, I would specify during Lucid partitioning the mount point as /mnt/data so it wouldn't show a desktop icon.

I actually prefer to use pysdm (Storage Device Manager) in Ubuntu to easily mount and unmount my storage partition and easily change permissions to umask=000 so Windows doesn't block my access to files and folders. Yes, Windows takes control of fat32 partitions, whether you like it or not. (Use Windows, not dos)

@jerome1232 The reason I prefer fat32 is because I often copy files back and forth to my son's Playstation3 which can not read ntfs. My storage partition is on a second hard drive that I sometimes remove from the desktop and put in an external enclosure for portability. Otherwise I would also prefer ntfs.

i've tried pysdm once and didnt get what i wanted/had some minor issues...

i found editing fstab as the easiest and just what i wanted...

i put this in fstab and worked... 
/dev/sda3 /mnt/BLOOD vfat iocharset=utf8,umask=000 0 0 

gonna do the same here, for ntfs...

thanks for helping and sharing infos guys... i really appreciate it... :-)

---

### Post by corncob on 2010-05-17
I bought an eeebox running Xandros Linux.  When I went to install XP also it told me there was a nonDOS partition and would not continue unless I gave the OK to format it.  I finally did thinking of reinstalling Xandros after XP was installed.  XP wiped Xandros out all right but never did install.  It just went round and round with the partitioning and formatting.  I finally gave up and ended up installing Ubuntu and skipping Windows -- well, not entirely, I eventually did install XP into VirtualBox.

---

### Post by 4Orbs on 2010-05-17
I guess this would be a good time to mark the thread as Solved. I'm really happy your notebook is working randolf_ambrose, it was beginning to look hopeless. Best of luck.

@corncob - Do you think Windows deliberately pulls dirty tricks? I do.

---

### Post by corncob on 2010-05-18
> **4Orbs said:**
> 
@corncob - Do you think Windows deliberately pulls dirty tricks? I do.

I understand that you can't buy a Linux computer at Best Buy, Office Max, etc because Microsoft has threatened to cut them off or raise their prices if they get into Linux.  Also, remember "Lindows", a small (24 employees) company that was selling Linux Computers through Walmart?  Microsoft charged that "Lindows" was a copyright infringement of "Windows" and sent an army of lawyers at Lindows until the company went bankrupt answering all the charges.

---

### Post by jerome1232 on 2010-05-18
Dell sells computers pre-installed with Ubuntu, System76 sells Computers and Servers pre-installed with Ubuntu as well.

---

### Post by corncob on 2010-05-20
> **jerome1232 said:**
> Dell sells computers pre-installed with Ubuntu, System76 sells Computers and Servers pre-installed with Ubuntu as well.

Oh, yea.  They're avasilable.  Search for Ubuntu Computers on [www.amazon.com](www.amazon.com) or google it.

---


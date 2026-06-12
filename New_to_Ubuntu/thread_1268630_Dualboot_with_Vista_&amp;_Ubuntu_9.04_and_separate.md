---
title: "Dualboot with Vista &amp; Ubuntu 9.04 and separate partition for files"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by hazypictures on 2009-09-17
I am brand new to Ubuntu. I also have a new HPG60 Notebook PC with Pentium Dual Core T4200, 2 GHz, 4 GB RAM, 64 bit operating system, 350 GB Hard drive. (shows as 289.09 GB) It came with everything (including Vista) loaded on the D drive, which was unpacked and installed onto the C drive. So now I have three partitions:

C: NTFS, 285.98 GB - primary
D: NTFS, 12.11 GB - recovery
Unallocated 2MB

I want to partition the drive with the data on its own drive so that both OS can access. I have read how to partition for XP, but I don't have XP. [http://ubuntuforums.org/showthread.php?t=1264327](http://ubuntuforums.org/showthread.php?t=1264327)

1. Partitions: I don't have any files on the C drive right now. Should I partition that primary section so that Vista stays on 30GB, make a 30 GB Ubuntu partition, 5 GB Linux swap partition, and the rest for file storage? Or is it better to reformat the C drive into the pieces and reinstall the Vista OS from the D drive? (is this even possible?) How many partitions is too much?

2. File System: Will NTFS allow me to see the storage drive with both OS?

3. Windows OS: Are there any issues unique to Vista? When I get my Windows 7 upgrade, will I have to reformat all the partitions, or just the Vista partition? Will I need to make changes to the D (recovery) disc? (I'd like to get rid of Windows but I need to keep it for work.)

4. x86 64bit: I was going to use the 64 bit version to match my processor, but since it is my first time, I want to make sure that my hardware works OK, so I'm going with 32 bit. When the next version of Ubuntu is released, will it be easy enough for me to switch to the 64 bit version then?

Sorry for all the questions, but I just want to be sure before I start.

Thanks!

---

### Post by Paqman on 2009-09-17
Welcome to the forums!

> **hazypictures said:**
> 
1. Partitions: I don't have any files on the C drive right now. Should I partition that primary section so that Vista stays on 30GB, make a 30 GB Ubuntu partition, 5 GB Linux swap partition, and the rest for file storage?


Yep, that would be a pretty good partitioning scheme. I'd go for max 4GB of swap. Swap only ever needs to equal RAM at the most, and even then only so that you can hibernate.

> How many partitions is too much?

Four is the maximum. However, you can get around that if you needed to by creating an "extended" partition. You can then create extra partitions inside that one, breaking the four partitions limit. In your case you could put your Ubuntu root and swap partitions inside an extended partition. 

> 2. File System: Will NTFS allow me to see the storage drive with both OS?

Absolutely

> 3. Windows OS: Are there any issues unique to Vista?

It's recommended to use Vista's own partitioner to shrink the Vista partition, but apart from that, no.

> When I get my Windows 7 upgrade, will I have to reformat all the partitions, or just the Vista partition? Will I need to make changes to the D (recovery) disc? (I'd like to get rid of Windows but I need to keep it for work.)

Your upgrade will install over the top of Vista. I'd make sure to back up everything else before you start though, as Microsoft installers tend to be pretty dumb, and I wouldn't be at all surprised if it broke non-Microsoft systems.

> 4. x86 64bit: I was going to use the 64 bit version to match my processor, but since it is my first time, I want to make sure that my hardware works OK, so I'm going with 32 bit. When the next version of Ubuntu is released, will it be easy enough for me to switch to the 64 bit version then?

No, you'd have to reinstall to switch to 64-bit. I'd advise you to go 64-bit now. If your hardware works with the 64-bit LiveCD, it'll work with the proper install, so you don't need to worry about any nasty surprises after installing.

---

### Post by HarrisonNapper on 2009-09-17
I'm actually curious about this myself, as I have the same setup. What file system would the file storage partition need to be formatted under? And could I install programs in both Vista (sudo shakefist) and Ubuntu in the file storage partition? I'm trying to move everything over to VirtualBox, but alas, it doesn't work for everything.

---

### Post by tomBorgia on 2009-09-17
Beaten to the punch but spent ages typing -

1 - Use Vista's disk tool to resize your "C" drive so you have 30GB "C" drive and 30GB spare. If you don't use Vista's tool you'll break it... I'm not sure how you go about this specifically I'm assuming it's not too involved. I'm pretty sure if you use the recovery partition it'll repartition the disks to factory settings... if you have an actual Vista disk I think you can specify which partition to install it on and it will leave the partitions intact.

2 - If you need a file storage partition you'll have to have it either fat32 / ntfs as windows won't read anything else... linux ntfs support was a bit shakey in the past but it's ok these days.

4 - Windows 7 will install over the top of the vista partition... it won't repartition the disk (unless you tell it to). If you upgrade to Win7 your recovery partition will be pretty much useless... it's set up by the pc manufacturer to be specific to your hardware / software setup the laptop was shipped with... and it's designed to recover from all kinds of messing up... so it'll zap the entire pc (see it as a factory - reset button!). If you go Win7 you can probably get rid of the recovery partition and use it for storage (you may need to alter some BIOS settings for this... I'd check there is nothing system specific in the BIOS using it first).

4 - The best advice I can give is to set up a separate /home partition when you install... basically you separate all your personal files from the system files so reinstalling the O/s becomes quite a lot easier... you don't need to worry about updating... you just reinstall from scratch on the system partition and don't touch your personal files... I can't recommend this enough!!! 

You could partition as follows -

```
NTFS / Vista - 30GB
Ext3 / Ubuntu (system /) - 15GB
Ext3 / Ubuntu (home folders /home) - 15GB
Swap / Ubuntu (swap) - 4GB
NTFS / Storage (Vista "E:\" Ubuntu /Data) - Rest of disk GB
```

---

### Post by Bartender on 2009-09-17
hazy - 
You mentioned that Vista was on a separate partition and you had to "unpack" it to get a C: drive?
I don't understand that, but seems like the manufacturers try something different every few years just to keep everyone guessing.  I'd suggest making recovery DVD's in case you want to wipe the drive and reinstall Vista down the road.  There should be an HP utility that allows you to do so.

---

### Post by Zimmer on 2009-09-17
Some reading for you before you start..

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

For creating the space using Vista software:
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2)



Been using a Vista/Ubuntu setup like you describe for the past 12 months...

oh, and a download link for EasyBCD
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by HarrisonNapper on 2009-09-17
> **tomBorgia said:**
> Beaten to the punch but spent ages typing -

4 - The best advice I can give is to set up a separate /home partition when you install... basically you separate all your personal files from the system files so reinstalling the O/s becomes quite a lot easier... you don't need to worry about updating... you just reinstall from scratch on the system partition and don't touch your personal files... I can't recommend this enough!!! 

This is a glorious recommendation; I wish someone had told me this two years ago. I may very well set up my desktop this way.

---

### Post by Paqman on 2009-09-17
> **HarrisonNapper said:**
> I'm actually curious about this myself, as I have the same setup. What file system would the file storage partition need to be formatted under?


Linux can read a whole host of different file systems, but Windows is extremely picky. Windows will need either FAT32 or NTFS. FAT32 has a lot of quite ugly drawbacks, so i'd always recommend the more modern NTFS.

> 
 And could I install programs in both Vista (sudo shakefist) and Ubuntu in the file storage partition?

Short answer: no.

Long answer: maaaaaybe, but only in special cases.

The only apps you'd be able to do this with were ones that were:

[LIST=1]
[*]Self contained
[*]Cross-platform
[/LIST]

A good example would be a Java app. Another possibility would be one of the Windows [portable apps]("http://portableapps.com/"), running through Wine.

Anything which requires a proper install, either Linux or Windows, isn't going to be an option.

---

### Post by hazypictures on 2009-09-18
Thanks for all the tips!

---

### Post by hazypictures on 2009-09-18
> **Bartender said:**
> hazy - 
You mentioned that Vista was on a separate partition and you had to "unpack" it to get a C: drive?
I don't understand that, but seems like the manufacturers try something different every few years just to keep everyone guessing.  I'd suggest making recovery DVD's in case you want to wipe the drive and reinstall Vista down the road.  There should be an HP utility that allows you to do so.

Yes, the system software is all on a D partition labeled "Recovery" so you can restore your base system if necessary. They don't give you a CD of Vista -- only what is on the Recovery drive.

---

### Post by hazypictures on 2009-09-18
> **Paqman said:**
> No, you'd have to reinstall to switch to 64-bit. I'd advise you to go 64-bit now. If your hardware works with the 64-bit LiveCD, it'll work with the proper install, so you don't need to worry about any nasty surprises after installing.
Thank you so much for all your answers.

So if I have Ubuntu on its own partition, could I later reinstall to 64 bit without disturbing my files partition and Vista partition?

---

### Post by Eric Warren on 2009-09-18
[U][I][B]Making partition's for Linux should be easy well i mean linux-ubuntu
when you start linux while installing you make a separte partition and split the partittion in half vista is not really good use's too much cpu but just make a partittion with the ubuntu CD - Or w.e

:guitar:

Gl.
[/B][/I][/U]

---

### Post by Eric Warren on 2009-09-18
If that does not work please contact me at [email]activeric@hotmail.com[/email]

Good luck.

---

### Post by Eric Warren on 2009-09-18
Oh didn't read "dualboot" oh ummm i have no idea but try with the cd much more easier.

---

### Post by hazypictures on 2009-09-18
> **tomBorgia said:**
> 4 - The best advice I can give is to set up a separate /home partition when you install... basically you separate all your personal files from the system files so reinstalling the O/s becomes quite a lot easier... you don't need to worry about updating... you just reinstall from scratch on the system partition and don't touch your personal files... I can't recommend this enough!!! 

You could partition as follows -

```
NTFS / Vista - 30GB
Ext3 / Ubuntu (system /) - 15GB
Ext3 / Ubuntu (home folders /home) - 15GB
Swap / Ubuntu (swap) - 4GB
NTFS / Storage (Vista "E:\" Ubuntu /Data) - Rest of disk GB
```

What is the difference between the Storage partition and the /home partition? I was planning to put all my personal files on Storage. Or do you mean personal Ubuntu files?

---

### Post by tomBorgia on 2009-09-18
/home is like windows "documents % settings" - You'll have your Desktop there, /.programname directories containing user configs for various programs (like windows' local settings / application data) pictures / docs folder etc...

Neat thing is if you reinstall the O/s... when you reinstall your programs (e.g. thunderbird email) all the configs are still there... in this case account settings... mail filters... emails etc!

Storage would be somewhere to put all your mp3's... videos... etc... it'd be visible to both ubuntu and windoze. :D

---

### Post by Paqman on 2009-09-18
> **hazypictures said:**
> 
So if I have Ubuntu on its own partition, could I later reinstall to 64 bit without disturbing my files partition and Vista partition?

Of course. And if you make a separate /home partition you won't even lose any of your preferences and settings in Ubuntu.

---

### Post by hazypictures on 2009-09-18
Very clear. Only one question remains (for now). I can only make 4 partitions, but I will need 6 -- the five that you mentioned above and I have that pesky Recovery drive for Vista.

So, do I use Vista tool to shrink the current C drive, and the then partition the newly formed partition into 4 different sections for Ubuntu system, /home, swap and storage. Should I do that final partition with Ubuntu or Vista?

One more Q: what file format should I make the swap partition?

---

### Post by HarrisonNapper on 2009-09-18
On the last question, I believe GParted actually has a partition format called "swap" for the swap partition. Happy *nixing!

---

### Post by Zimmer on 2009-09-18
> **hazypictures said:**
> Very clear. Only one question remains (for now). I can only make 4 partitions, but I will need 6 -- the five that you mentioned above and I have that pesky Recovery drive for Vista.

So, do I use Vista tool to shrink the current C drive, and the then partition the newly formed partition into 4 different sections for Ubuntu system, /home, swap and storage. Should I do that final partition with Ubuntu or Vista?

One more Q: what file format should I make the swap partition?

Read a bit more about extended partitions. You can only have 4 Primary, I reckon 2 will already be taken by Vista (the install and the recovery partition... have you made recovery disks from it as instructed in your computer documentation?? I suggest you take the time to do so before you start any partitioning etc to avoid future tears..)

For example, with Vista loaded first you will see sda1 is the NTFS Vista Install, sda2 is the HP recovery .
That will leave you (when you create the space) room to create sda3 and sda4.
Oh, and although I had plenty of disk space Vista refused to let me have any more than 50% of the disk!!!

sda3 can be your Ubuntu install.
sda4 can then be made an extended partition so that it can be split into 'logical' partitions and space allocated within it.

In my case there are two parts to sda4 - sda5, which is my swap  and sda6, which is my 'storage'.  

I do not have a separate /home partition, but do not let that influence you in your decision... if you read further about extended partitions you may find that you can mount /home on a further logical partition.
(in my case I would have to allow room on sda4 and create sda7 on it.)

Note also that external drives are not too expensive these days if you want to consider that as a further method of storage.

How mine is set up is not ideal, I should have made my Ubuntu partition(32gb)  smaller (less than 5 gig is currently used!!) and given more to the storage.

Go to the Ubuntucat site, or Herman's dual boot site and read a bit more on the partitioning side of things before you start and plan what you want to do...

---

### Post by hazypictures on 2009-09-18
Thanks again for all your help on this!!! I've already made recovery backups.

> **Zimmer said:**
> Oh, and although I had plenty of disk space Vista refused to let me have any more than 50% of the disk!!!
I've now re-read Herman's partitioning info and it is much clearer. If Vista would only let you have 50% of your drive, what did you do? Did you sacrifice it to Vista? Or were you able to reclaim any of it?

So just to be clear, I should:

1) reduce the size of my Vista drive using Vista
2) create another primary partition and an extended partition (that will be the largest part). Should I use GParted for this? Or Ubuntu disk?
3) Carve the extended partition into the necessary pieces that I need for Ubuntu (/, /home, swap). Again: should I use GParted or Ubuntu to do this?

Thanks!

---

### Post by Zimmer on 2009-09-19
> **hazypictures said:**
>  Did you sacrifice it to Vista? Or were you able to reclaim any of it?

So just to be clear, I should:

1) reduce the size of my Vista drive using Vista
2) create another primary partition and an extended partition (that will be the largest part). Should I use GParted for this? Or Ubuntu disk?
3) Carve the extended partition into the necessary pieces that I need for Ubuntu (/, /home, swap). Again: should I use GParted or Ubuntu to do this?

Thanks!
I concur with the steps you have described..

I (sadly ) sacrificed it to Vista on this occasion to avoid any MS induced problems (brand new laptop.. plenty of space, considering I also have two spare HDs and an enclosure for them so they can be mounted as external drives if required.)


As for using Gparted etc. I believe I just ran the Ubuntu install and chose the manually partition drives option and carried out the tasks there . I was careful to leave sda1 and sda2 untouched..

(if it is the first time you have done anything like this the nerves can be frayed and palms can sweat as you read the on-screen instructions extremely carefully, making sure you understand what you have done, and hoping the partitioner does, too! :) that's quite normal.. )
Good Luck...

ps. if you are going to use EasyBCD remember when asked  to put GRUB on the Ubuntu partition, NOT the MBR.

---

### Post by Bartender on 2009-09-19
About a year ago I helped some folks set up their new HP laptop.  The hardcopy HP manual stated that the Recovery partition would be rendered unusable once you'd made your recovery discs, so you could remove it if you wanted to.
If that's still true for HP, and you've made your recovery discs, and you feel pretty certain the burn went OK (no power outages or other major disruptions right in the middle of the process) then I'd suggest deleting the Recovery partition using a GParted LiveCD or the Vista partitioner.
One less complication, and a little bit of free space to use for Linux.

[Here's]("http://ubuntuforums.org/showthread.php?t=1249374") a post I made a few weeks ago.  There are pictures of a few different dual-boot schemes.  That might help give you an idea.

---

### Post by theozzlives on 2009-09-19
Here's an idea as opposed to a Data partition: [http://ubuntuforums.org/showthread.php?t=1244185]("http://ubuntuforums.org/showthread.php?t=1244185") (it's Users instead of Documents and Settings in Vista).

I would use half of Drive C: for Ubuntu:
10 GB /
4-8 GB swap
the rest of the half for /home

So in Linux Terms, you'd have something like:
SDA1 = Vista
SDA2 = /
SDA3 = Extended (automatically created)
SDA5 = /home
SDA6 = swap

Actually if it were me I'd take Vista off as I did my laptop, but if I were to dual boot, that's how I'd do it.

---

### Post by hazypictures on 2009-09-19
I did it! But I did something wrong because Ubuntu does not boot up. I tried the esc key during start up but did not see a way to get it to swap over to Ubuntu. Sad.

Vista would only let me shrink the Vista partition to 202 GB, so I only had 84 GB for my Ubuntu install. I suspect that I made three errors:

1. I wanted to create a large partition for files to be read by both Windows & Ubuntu, but all I had left was 51 GB. I wanted it to be NTFS but that wasn't a choice, so I selected Fat32, with a mount point of /windows (other choice was /dos). I wasn't sure what to do here and think that my choice was wrong.

2. The instructions said to put a mount point for windows, but to do that, I would have to erase my Vista partition. Maybe that's not a problem? I don't know. So no mount point was in the table before I hit "go". 

3. I was told that in Easy BCD, when asked to put GRUB on the Ubuntu partition, NOT the MBR. I clicked on advanced and wasn't sure what to choose here. I selected boot loader to sda6 which is supposed to be my / drive.

How can I get Ubuntu to boot up?

---

### Post by PatWb on 2009-09-19
Wow - lots of talk re Vista and Ubuntu in dual-boot config. I tried two ways :1 using Acrons Disk Director partioned the drive etc and installed Ubuntu that way - worked well with no boot problems; also made use of the Ubuntu install file selection allowing you to install it within Windows. Neat it appears, no boot problems, provides the operating system selection opportunity and away you go. I especially like the ability to look at/into the files that are in the Windows area while running Ubuntu - unfortunately windows can't get see the Ubuntu files.

Just as ann aside, Windows 7 versus Vista seems not too grand -- lots of stuff for the system operators with remote clients etc but for the casual user not much difference near as I could tell.  The Release Candidate (RC) version of 7 didn't have any email capability as has the previous version of windows (Outlook Express/WIndows Email). Just some thoughts.

I'm up against the wall trying to get the Linux 'tar' configuration driver files for a Dymo Lable Writer to install.

Patb

---

### Post by Zimmer on 2009-09-20
HAve you rebooted to VIsta and put an entry for Ubuntu in Easy BCD ?

---

### Post by hazypictures on 2009-09-20
> **Zimmer said:**
> HAve you rebooted to VIsta and put an entry for Ubuntu in Easy BCD ?
I have rebooted but I'm not sure what Easy BCD is. Do I need to download it? And how do I put the entry in?

I booted Ubuntu with the CD and I could see all the partitions and files, I just could not get them to boot. So close...

Thanks again for all your help!

---

### Post by Zimmer on 2009-09-20
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

did I miss that link in an earlier post?  Yes, download it and install it in Vista!

There is a tutorial on it in one of my earlier links!

---

### Post by Zimmer on 2009-09-20
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4)

Screenshot tutorial for it..

---

### Post by HarrisonNapper on 2009-09-21
> **hazypictures said:**
> I did it! But I did something wrong because Ubuntu does not boot up. I tried the esc key during start up but did not see a way to get it to swap over to Ubuntu. Sad.

Vista would only let me shrink the Vista partition to 202 GB, so I only had 84 GB for my Ubuntu install. I suspect that I made three errors:

1. I wanted to create a large partition for files to be read by both Windows & Ubuntu, but all I had left was 51 GB. I wanted it to be NTFS but that wasn't a choice, so I selected Fat32, with a mount point of /windows (other choice was /dos). I wasn't sure what to do here and think that my choice was wrong.

2. The instructions said to put a mount point for windows, but to do that, I would have to erase my Vista partition. Maybe that's not a problem? I don't know. So no mount point was in the table before I hit "go". 

3. I was told that in Easy BCD, when asked to put GRUB on the Ubuntu partition, NOT the MBR. I clicked on advanced and wasn't sure what to choose here. I selected boot loader to sda6 which is supposed to be my / drive.

How can I get Ubuntu to boot up?

Something else to consider is to install another vista partition in the 84 GB space, transfer your files and settings using the file transfer wizard, then you have 202 GB left to expand Vista, install Ubuntu, and/or create a storage partition.

---

### Post by hazypictures on 2009-09-29
> **HarrisonNapper said:**
> Something else to consider is to install another vista partition in the 84 GB space, transfer your files and settings using the file transfer wizard, then you have 202 GB left to expand Vista, install Ubuntu, and/or create a storage partition.

Is it possible for me to use the Recovery drive on my laptop (or the Recovery DVD that I made) to install Vista on the 84GB partition? Then I could wipe Vista off the 202 GB and use it as mixed Windows/Ubuntu storage (for docs, imgs, etc.) I don't have any files or settings on the current Vista C: drive bec it is a brand new laptop and I haven't moved my files over yet. Or is it impossible to install Vista on another partition?

---

### Post by Zimmer on 2009-09-29
> **hazypictures said:**
> Is it possible for me to use the Recovery drive on my laptop (or the Recovery DVD that I made) to install Vista on the 84GB partition? Then I could wipe Vista off the 202 GB and use it as mixed Windows/Ubuntu storage (for docs, imgs, etc.) I don't have any files or settings on the current Vista C: drive bec it is a brand new laptop and I haven't moved my files over yet. Or is it impossible to install Vista on another partition?

It is highly likely (99% certainty) that the recovery program WILL restore your computer to how it was when you unpacked it new!

You will not get a chance to partition etc. it will have a script to work to which will be format space except for recovery partition to NTFS, and install windows on that space (wiping out any other partitions and OS's on the way).... and unless you can find valid info to the contrary I suggest you assume that is what will happen.

Having just 'recovered ' a laptop in similar circumstances I can ASSURE you that I was given no opportunity to tweak the install.. 

Sorry that is the best advice I can give, but if there is anyone out there that can tell us a different tale I would sure like to hear it ... (I could do with snaffling more space from my Vista install..)

---

### Post by hazypictures on 2009-09-30
I'm getting the Windows7 upgrade when it is available (bec my laptop is a recent purchase) but I wonder if I'll be able to install it on any partition or only where Vista was installed?

---

### Post by HarrisonNapper on 2009-09-30
Should be able to install on any ntfs partition; I haven't used the partition editor that ships with Windows 7, but Vista's can do this. Win7 beta should be out on msdn somewhere if you want to give it a whirl.

---

### Post by hazypictures on 2009-09-30
I made a big error. Yesterday I tried to do this...
>  					Originally Posted by **HarrisonNapper** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7984838#post7984838") 				
 				*Something else to consider is to install another vista partition in the 84 GB space, transfer your files and settings using the file transfer wizard, then you have 202 GB left to expand Vista, install Ubuntu, and/or create a storage partition.*


I booted Vista and I could see a 78GB partition and so I thought that I'd wipe out Ubuntu, move Vista over and then reinstall Vista. So, I used Vista to reformat the disk to NTFS. Then I could not figure out how to get Vista over, but discovered that Ubuntu was still there. The only drive that I formatted was my storage disk, which was originally 51GB of FAT32, but is now only 48.2GB NTFS.

How can I restore my dual access (Ubuntu/Vista) storage drive? Should I reformat that drive with Vista to FAT32? Will I lose another 30 GB? 

Should I just go to my recovery D: drive and tell my computer to start again? (Right now, this seems like the smartest idea...)

Any tips on how to get more out of the Vista shrinking tool? I only got 202GB.

---

### Post by HarrisonNapper on 2009-09-30
Can't do much about the Vista shrinking tool except use the original installation CD or Recovery Partition (maybe) to install on the empty ntfs partition then reformat the existing Vista partition. Both Windows and Linux are able to access ntfs partitions and ntfs is better than fat32, so you shouldn't need to reformat. At this point, it might be a good idea to read the Partitioning section of the Ubuntu Community Documentation.

---

### Post by hazypictures on 2009-10-11
Just wanted to update to say that my dual boot is working very well. 

I used my HP recovery disks to go back to my original setup. At that point, I could shrink a lot more of the Vista share, but I wanted more. So, I used GParted and reduced Vista to only 90GB. Then I set up the large partition for file storage and a smaller partition for Ubuntu install. So far, things are good.

Thanks to everybody for the invaluable tips and advice!

---


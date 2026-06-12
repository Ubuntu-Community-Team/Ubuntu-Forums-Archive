---
title: "Ruined windows. How do I get to my partition?"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by Lucypie on 2011-07-27
Alright, on my previous post, I was going to simply go and get my wubi install and move it.
Guess what, I screwed everything up.
I know how to fix it. Yeah. Wipe the entire system clean.

But first I want my crap off of windows. Most the files are backed up, but I want my program files and crap.
I'm going to put it on my old laptop drive so i can hold all of it, but how do I get to the windows partition!??!

Could someone be so kind as to link me to an idiot-proof guide to installing windows & ubuntu (11.04) side by side? If not I'll find my own, but I'm up to my ears in STRESS right now. Every @#&(ing time I do something, I screw it up. All I'm asking is to have windows & ubuntu side by side. If nothing else, I'll do a bloody ubuntu only system. 

Sorry if this comes by as rude, i'm trying to be calm but I'm so stressed right now.

---

### Post by Beacon11 on 2011-07-27
Hey, relax man-- you'll get it. Can you be a little more specific about what steps you took to "screw everything up?"

---

### Post by Lucypie on 2011-07-27
Yeah, sorry.
I installed ubuntu 11 on a new 100GB partition. I kept going back and forth from my ubuntu wubi and new partition. I decided it wasnt' working out right and I'd just wipe it all out so I went to Windows to get my crap but it wouldn't boot. It would say "starting windows" and reboot.

---

### Post by bodhi.zazen on 2011-07-27
It sounds as if you did a wubi install.

While this allows you to try Ubuntu, it is more difficult to manage, IMO. If you are going to use Ubuntu I suggest a standard installation.

So two parts:

1. remove wubi . see: [https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

If you have an error message of some sort we need to know what it is to fix it.

2. Set up a dual boot. First back up your data, then install windows and restore your data.

Then install Ubuntu, not wubi ;)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

This means burning the iso to a cd or flash drive (see unetbootin) and partitioning your hard drive. If you stay with the installer defaults you will be fine, if you change the defaults you need to understand what you are changing ;)

---

### Post by Lucypie on 2011-07-27
Here is extra information:
When I boot, I cannot go into recovery. Booting into my recovery device is NOT working.
Does this mean I cannot install windows again?
When I press boot into windows normally, i see the starting windows thing, it freezes and a millisecond long blue-screen flashes, then a black-screen with text, and then it reboots.
Running sudo fdisk -l in my terminal is not listing a NTFS system

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x79120785

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *           1          26      203776   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3              26       20320   163012608   42  SFS
/dev/sda4           20320       38914   149352449    5  Extended
/dev/sda5           20320       21293     7811072   82  Linux swap / Solaris
/dev/sda6           25548       38914   107360256   83  Linux
/dev/sda7           25165       25548     3073024   82  Linux swap / Solaris
/dev/sda8           21293       24782    28024832   83  Linux
/dev/sda9           24782       25164     3073024   82  Linux swap / Solaris

Partition table entries are not in disk order

I can still get to my old ubuntu which was inside windows, but i cannot boot into windows.


Hey, Bodhi.zazen. I can't back up what I can't access. How can I get into windows partition or files of windows? Am I just not going to be able to do this?
Do you know how to reinstall windows? My computer did not come with this stuff, it told me to make a recovery disk, but i cant boot off it. I have a recovery drive with the recovery crap but I cant access this either!

---

### Post by Beacon11 on 2011-07-27
bodhi.zazen, it sounds like he can't even GET to Windows. Lucypie, I'd plop in your Windows disk and have it repair your install. Have you tried that?

EDIT: Ah, we posted at the same time, sorry. If you tried to boot to a recovery device, does that mean you don't actually have a Windows disk? (i.e. your laptop came preinstalled with Windows).

---

### Post by Lucypie on 2011-07-27
Exaaaactly.
My dad has a VISTA disk, but Id on't want vista, I want 7.

---

### Post by Beacon11 on 2011-07-27
> **Lucypie said:**
> Exaaaactly.
My dad has a VISTA disk, but Id on't want vista, I want 7.

Yeah I don't blame you. Did your computer at least come with some sort of recovery disk? Is that what you meant by "recovery device?" If so, what do you mean when you say it's not working?

EDIT: Gahh, I didn't read the last bit of your post above. "Recovery device" then I assume is a partition put on there by your manufacturer, correct?

---

### Post by Lucypie on 2011-07-27
It came with a partition called recovery and a note saying "First thing you should do before doing anything: Make a recovery disk. Click here" xD

Which I did. Which is not working. I cannot boot off it. No errors or anything, I just hit boot off disk and it pauses, and then boots into the normal grub.

---

### Post by Beacon11 on 2011-07-27
> **Lucypie said:**
> It came with a partition called recovery and a note saying "First thing you should do before doing anything: Make a recovery disk. Click here" xD

Which I did. Which is not working. I cannot boot off it. No errors or anything, I just hit boot off disk and it pauses, and then boots into the normal grub.

Haha, helpful eh? Okay, I've never used this product before, but I'd give the following guide to Paragon Rescue Kit (Free) a shot: [http://www.intowindows.com/repair-windows-xp-vista-windows-7-without-installation-cddvd/](http://www.intowindows.com/repair-windows-xp-vista-windows-7-without-installation-cddvd/) .

---

### Post by Lucypie on 2011-07-27
I am on a limited internet usage and I don't want to go over so I can't get that. :/ Sorry.
It looks like you have to be in windows to use the thing :/ Oh well.

---

### Post by Beacon11 on 2011-07-27
You can't use your dad's computer to burn a bootable cd? Regardless, if you can't download anything I think you're kinda screwed. You need to download something to repair your install if you don't have a Windows 7 disk available to do it for you. Sorry man.

---

### Post by oldfred on 2011-07-27
Part of your windows problem is that you used windows to create partitions. Then windows popped up and said it was converting from basic - standard MBR(msdos) with 4 primary partitions to dynamic which is a logical volume system unique to windows. Some windows tools do not even work with that system.

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

One user used these two:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)

Dual boot - minor difference in screens between versions but process is the same:
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by o15977 on 2011-07-27
If you're going to wipe your Windows, you can't have the programme running on the entire new Windows... i'm sorry.

so.... how did you screw it up exactly? lol
when i started using linux, i had heaps of the prob as well
now i have ubuntu, fedora, backtrack and windows on my computer at the same time, ;) and a beautiful Grub2 bootloader X)

---

### Post by Noncon on 2011-07-27
> **Lucypie said:**
> It came with a partition called recovery and a note saying "First thing you should do before doing anything: Make a recovery disk. Click here" xD

Which I did. Which is not working. I cannot boot off it. No errors or anything, I just hit boot off disk and it pauses, and then boots into the normal grub.

If you are trying to boot from a recovery disk, it goes through a pretty long (10 min) pause before you get to recovery options.  

Also, can you try to run Ubuntu from the CD, instead of installing it?  That way, you may be able to copy your important files from the Windows partition.  Actually that is how I first heard about Ubuntu, when a drive crapped out on me and I needed to get the data. 

Finally, your drive most likely has a hidden recovery partition, where you don't even need the recovery disk.  I know most Gateway notebooks, you have to hit F8 while booting to get to the this partition.  Try a Google search for the mfg of your notebook to see how to access the partition. 

KJ

---

### Post by N00b-un-2 on 2011-07-27
Okay so I hate to be the bearer of bad news but the easiest way to fix your computer is going to be a fresh install.  As far as recovering data from your Windows partition, you should be able to do so using an Ubuntu live CD if your Wubi install is not detecting your Windows NTFS partition.

In my opinion, Wubi is not the way to go.  You're going to want to do a true dual boot.  So I'm going to try and be as clear and orderly about fixing your computer, starting with a bill of materials.

What you'll need:
1) an Ubuntu Live CD
2) a Windows 7 install disk
3) an external hard drive

Step 1:  Recover your data
Make sure that your external hard drive has adequate storage to back up your files.  You're going to need to wipe your entire hard drive before all is said and done,  so you'll need to grab EVERYTHING off your hard drive you don't want to lose.
Boot into the Ubuntu CD and choose "Try Ubuntu".  Once you're looking at the desktop, open up nautilus and see if it is detecting your NTFS partition.  If so, open it and copy your files to your external hard drive.  Your documents and such will be at C:\Users\*your user name*\
If it doesn't automatically detect your NTFS partition, you may have to mount it manually.  open up a terminal and type
```
sudo fdisk -l
```
then figure out which partition is your Windows partition and then mount it to /mnt.  Eg:
```
sudo mount /dev/sda1 /mnt
```
I understand that your Wubi install wasn't seeing the NTFS partition, but that's probably because Wubi isn't a true Linux install, it resides on the same partition as Windows so it may not detect Windows properly if their is a problem.  After mounting your Windows partition to /mnt, back up your files and proceed with the next step.

*** If you have files that you need to back up from you Wubi install, do so now.  Wubi is going bye bye after this ***

Step 2: Reinstalling Windows
DO NOT PROCEED WITH THIS STEP UNTIL YOU HAVE BACKED UP ALL YOUR VALUABLE DATA.  YOU WILL NEED AN INSTALL DISK TO DO THIS.

Now here comes the upsetting part of this process.  Most computers nowadays do not come with Windows on a CD/DVD anymore for reasons unbeknownst to me and it is extremely frustrating in case of catastrophic failures.  If there is a recovery partition on your computer, you may be able to restore your computer to the "factory image" (the way it was configured the day you bought it) but in my experience, this has only ever worked on ONE computer out of the dozens I've fixed over the years.

If you need an actual disk to install Windows from, your computer manufacturer is required BY LAW to provide you with the install media for the version of Windows that is keyed to your machine if you request it from them.  Your mileage may vary, but you may end up waiting several weeks for a new disk from your manufacturer.

*** NOTE ***
This is the proper and legal way to recover your copy of Windows.  I'm not a Windows user and I avoid having to use Windows at all costs but I fix computers and the vast majority of people use Windows and DO NOT HAVE an install disk.  That doesn't mean there aren't alternative methods of getting a Windows install disk.  You could always go and buy a copy from a store, but it seems a little ridiculous to spend money on a product you already have a valid license for right?  You can side-step the legal issues a little bit by downloading a copy of a Windows "AIO" (all install options) disk from somewhere on the web...  I use one frequently when installing or recovering other people's computers.  Although the copy of Windows is of questionable origin, the fact of the matter is you still require a serial key for each copy of Windows so if someone's laptop came with Windows 7 Home Premium, sure I can use the AIO disk to install Ultimate, but I can't validate that install without a serial key.  If I install the same version of Windows that the computer came with, I can use the same serial key and no laws (well, almost no laws) have been broken and my conscience is appeased.

I'm not telling you to break the law, I'm just passing on some information.  So anyway proceeding with the process of fixing your computer.

The first step before installing any operating system should be to choose your partitioning scheme.  I would highly recommend you use the Ubuntu Live CD and fire up *gparted *before you do anything.  The Windows Install disk does some really goofy things with partitioning if you let it.

Now, this is not necessary but it is a good idea.  After my first catastrophic system failure since I switched to using Linux, I discovered how invaluable keeping your /home on a separate partition can be.  You can easily reinstall a new operating system without losing any data or even having to back anything up.  Not only that, but if you use a program on Windows called Ext2IFS, you can mount your Linux partitions under Windows (as long as they're EXT2 or EXT3.  There is no support for EXT4 under Windows yet).  The operating systems themselves and the applications and drivers do take up a bit of room, but I find that between music, documents, photos, videos and downloads my personal data takes up a far greater amount of space than the system itself.  I like to use my home partition as my user data storage space for all operating systems.  That way I don't have duplicate data floating around on my limited hard drive space and I don't have to search for my files.  They're in the same place for each operating system I run.  But anyway...
Partition your hard drive:
```

/dev/sda
   /dev/sda1 NTFS (at least 25GB)
   /dev/sda2 EXT2/3 (at least 10GB) This is your "/" for Ubuntu
   /dev/sda3 EXT2/3 the rest of your hard drive space, except for twice the amount of your RAM.
   /dev/sda4 SWAP (should be twice the size of your RAM)

```
Apply the changes in gparted and then your ready to install Windows.

Boot into the Windows disk and do a fresh install to your NTFS partition.  It's important to install Windows before Ubuntu since you if you install Windows after Ubuntu, the Windows NTLDR overwrites GRUB on the MBR (you lose the ability to boot into Ubuntu).  It's not terribly hard to reinstall GRUB after installing or recovering Windows, but why go through the additional trouble if you don't need to?

Once you've installed Windows, you should spend some time installing updates, making sure you have all of your drivers installed, etc.  At this time if you so choose, install EXT2IFS and configure it to mount your Linux /home partition (I would shy away from mounting the system partition because you can mess things up from Windows).  Then if you want to use your Linux Home folders by default from Windows 7, go into your documents folder (it's under C:\Users\your user name\) and right click each of the folders **EXCEPT THE DESKTOP!!!!** and change the target to the equivalent folder in your Linux home.  For example, I set my home to mount under Z: in Windows, so I would change the target of C:\Users\me\Documents to Z:\me\Documents.
... I really hope that makes sense....

Step 3: Install Ubuntu!
The Ubuntu install is a straightforward process.  Just pop in the live CD, reboot and choose install Ubuntu.  DO NOT INSTALL UBUNTU FROM WITHIN WINDOWS!!!  Just remember that you already partitioned your hard drive, so when it asks you DO NOT FORMAT your partions.  Set your small EXT partion as "/" and set the large one as "/home".  Proceed with the install as normal and you're done.

The next time you reboot, you should be greeted by the GRUB boot screen and be able to choose between Windows or Ubuntu.

I hope this helped!

---

### Post by walt.smith1960 on 2011-07-27
Possible help re bootable Win7 disk.   I found a legitimate download source for Win 7 Pro, Home Premium and Ultimate.  You download the appropriate .iso file in Ubuntu and do the usual burn to DVD. These are 30 day trials.  You need the key to activate the install.  I bought keys from a Microsoft partner, you should have a sticker somewhere on your PC.    Perhaps this will help you, I hope so.

[http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/](http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/)

---

### Post by Lucypie on 2011-07-27
Alright. Yes, I do wish to wipe the system and reinstall. 
BUT I need my stuff off the windows partition FIRST! 
My computer has a recovery partition, but it craps out. Does nothing. Asks for the install disk.

Process to get into recovery:
Boot, press esc, press F11 for system recovery. I get a screen saying something about a missing device? Then it gives instructions for recovery, place install disk in drive, reboot, then repair. Says then if i don't have install disk, call support.
>_<


Noncon: It does nothing, it can't find a recovery on the disk or won't boot. Something.
Also, how do I get to my windows partition? That's the whole point: I can't figure out how to get to it.


N00b-un-2:
Thank you! I got my stuff now!

NOW I will be trying to follow your posts to reinstall everything. Thanks much! Updates soon!

---

### Post by Mark Phelps on 2011-07-27
> **N00b-un-2 said:**
> 
I understand that your Wubi install wasn't seeing the NTFS partition, but that's probably because Wubi isn't a true Linux install, it resides on the same partition as Windows so it may not detect Windows properly if their is a problem.  After mounting your Windows partition to /mnt, back up your files and proceed with the next step.
Your Windows OS file are already available under "/host".

> If you need an actual disk to install Windows from, your computer manufacturer is required BY LAW to provide you with the install media ...
NO -- they are NOT!  They are required to provide you a WAY to restore your system -- which they DO when they include a Recovery partition (or file) on the drive and a way to invoke Factory Restore.  They are NOT required to provide you a physical disk.

> You can side-step the legal issues a little bit by downloading a copy of a Windows "AIO" (all install options) disk from somewhere on the web...
This is tantamount to condoning piracy -- and is forbidden in the Rules of Conduct for this forum!  

> If I install the same version of Windows that the computer came with, I can use the same serial key and no laws (well, almost no laws) have been broken and my conscience is appeased.
True -- and since all retail/OEM MS Windows Vista DVDs contain ALL the different versions, a reinstall can be done from ANY of them.

Other comments -- if the PC can't boot from the Recovery CD the OP made, there's either a problem in the boot sequence, the CD is bad, or there's a problem with the optical drive.  I've made over a half-dozen Repair CDs and have yet to encounter a problem with any of them.

So, if the optical drive is bad, the OP is not going to be able to restore or reinstall anything -- without first replacing the optical drive.

---

### Post by Lucypie on 2011-07-27
Oh Mark xD Just a bit of a buzz kill? 
Guess what. Status update! I have ordered the disk from HP. My warrenty was out by 25 days (which it is REALLY supposed to be out in october, but I wasn't bothering argueing.) 16.45 for a windows 7 64B + Su & Drivers. Crazy, but who cares.
I need opinions now.

Do i continue using ubuntu live disk until the disk comes in the mail (2-8 days) or do I install ubuntu now, install windows later? Or do I install ubuntu now, clear it when the new disk comes in, and reinstall everything?

I also hear that deleting the not-so-hidden hidden partition (200MB for Recovery and MBR) will cause hellish errors. Is this true? I figure its true if you have windows /installed/ but if you don't, I figure it wont. 

Another thing, how can I clear my mbr? Its got GRUB still trying to boot with errors. Will installing 7 or ubuntu solve this?

--OOH nother question. If I were to say, install windows 98 or 95, When should I do that?  Now? After 7 is installed? Or after Ubuntu & 7 are installed? Or should I just not do it at all? I have a bunch of games made for 95 and I have a 98 disk I know where is (and I was told I have a 95 disk SOMEWHERE) and I wanted to tri-boot it. possible?

---

### Post by Mark Phelps on 2011-07-27
> **Lucypie said:**
> Do i continue using ubuntu live disk until the disk comes in the mail (2-8 days) or do I install ubuntu now, install windows later? Or do I install ubuntu now, clear it when the new disk comes in, and reinstall everything?
Sorry, no real simple answer ...

When you go to install Windows, if your disk is fully-allocated with Linux partitions, since Windows can't read these, it will become confused and NOT allow you to install.

If you leave some unallocated space at the beginning of the drive, Windows will see that and you can install it there.  Windows will (as always) overwrite the MBR code with its own, removing access to Ubuntu.

You will then have to boot from an Ubuntu LiveCD and reinstall GRUB -- which will (temporarily) remove access to Windows.

Then, when you reboot Ubuntu, open a terminal and enter "sudo update-grub".  This will regenerate the default GRUB menu and add an entry for Windows. When you reboot, you'll be presented with a menu allowing you to choose which OS.


> I also hear that deleting the not-so-hidden hidden partition (200MB for Recovery and MBR) will cause hellish errors. Is this true? I figure its true if you have windows /installed/ but if you don't, I figure it wont.
It will NOT cause problems if you delete that.  That is used to store the Windows boot loader code.  But if it does not exist, and your drive already has other partitions on it, Windows will simply write the boot loader code into its own OS partition. The MBR has nothing to do with that partition. 

> Another thing, how can I clear my mbr? Its got GRUB still trying to boot with errors. Will installing 7 or ubuntu solve this?
Installing Win7 will rewrite the MBR anyway -- so I would just live with it for a short while.  You'll end up overwriting it a second time when you reinstall GRUB for Ubuntu access.

---

### Post by cmcanulty on 2011-07-27
+1 on MiniTool Partition Wizard has saved partitions for me that nothing else could access.Free too

---

### Post by Lucypie on 2011-07-27
Thanks Mark. 
Any more ideas? And any ideas about how I should go about or if I should even install Windows98?

---

### Post by cmcanulty on 2011-07-28
Have you considered adding virtual box to ubuntu and running windows in that unless you use mostly windows

---

### Post by Noncon on 2011-07-28
> **cmcanulty said:**
> Have you considered adding virtual box to ubuntu and running windows in that unless you use mostly windows

Or want to play any Window based games.  Getting video card acceleration on a VM is really tough, if not impossible. :(

KJ

---

### Post by Mark Phelps on 2011-07-28
> **Lucypie said:**
> Thanks Mark. 
Any more ideas? And any ideas about how I should go about or if I should even install Windows98?

I thought you were going to reinstall Win7.  If you're getting the Pro version, it comes with the ability to run XP-era apps in a form of virtual machine.

Even without that, you can try to install XP-era and 98-era apps using different compatiblity modes.

So, I would NOT install Win98, if it were me.

---

### Post by Lucypie on 2011-07-28
The only problem with that is that my screen resolution is 1366x768 and those games were made for somewhat 800x600 or less.. I can't window them (even using the -w command) and some games actually won't compatible-ify even when I use the compatability mode thing. I guess I can deal without these.

---

### Post by N00b-un-2 on 2011-08-30
> The only problem with that is that my screen resolution is 1366x768 and those games were made for somewhat 800x600 or less.. I can't window them (even using the -w command) and some games actually won't compatible-ify even when I use the compatability mode thing. I guess I can deal without these.

Unfortunately, there is no simple answer here. Unless the game itself is capable of scaling graphics up (and very few are) you're pretty much stuck with that.  However, in my experience there are often after market patches and mods to support higher resolutions than were available when a legacy game was released, eg; Final Fantasy VII for PC.  Your results may vary.

---


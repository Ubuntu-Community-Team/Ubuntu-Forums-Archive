---
title: "Complete uninstall and format"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by beeben on 2011-07-10
Hello,

  I am having an extremely frustrating time trying to just remove Ubuntu completely and format my MAIN drive. I do not have a second drive, I want to format my harddrive. In an HP laptop. I do not have a clue why this is so difficult. There are many posts about dl'ing this and that application to do this very simple task. I am obviously not a programmer and thought that it would be fun to try and learn. Well it has not been fun for me at all. So, someone, please, in plain English explain to me how to uninstall completely Ubuntu 10.04 whatever and format my drive. Thank you to all who can help and recognize my level of frustration.

---

### Post by riemann_zeta on 2011-07-10
I assume you want to reinstall Windows? Do you have your Windows installation discs around?

---

### Post by critin on 2011-07-10
I can feel your frustration--I've been there a few times myself.  Just put a live linux in and boot it.  Find Gparted in System or Administration and open it.  Choose delete all partitions, then format it.

If you're going to install another os, it usually does a good job of formatting for itself as it installs-- unless you need special custom partitions.  It overwrites all data and formats.  No need to uninstall first.

critin

---

### Post by fabricator4 on 2011-07-10
> **beeben said:**
> Hello,

  I am having an extremely frustrating time trying to just remove Ubuntu completely and format my MAIN drive. I do not have a second drive, I want to format my harddrive. In an HP laptop. I do not have a clue why this is so difficult. There are many posts about dl'ing this and that application to do this very simple task. I am obviously not a programmer and thought that it would be fun to try and learn. Well it has not been fun for me at all. So, someone, please, in plain English explain to me how to uninstall completely Ubuntu 10.04 whatever and format my drive. Thank you to all who can help and recognize my level of frustration.

The problem is, you can not format a Linux hard drive while you are booted off it.  If you boot off the LiveCD that was used to install Ubuntu, you should be able to remove the partitions off the drive using the Gparted utility which you will find under the system utilities.

Note however that if you remove all the partitions off the hard drive it will not be able to boot anything at all.  You would need the Windows boot disks to re-install Windows, assuming that is what you intend to do.

The other thing is, if you're set up with two operating systems, you need to be clear how you installed Ubuntu if you want to keep the Windows boot.  If you used the Wubi install it's as simple as booting windows and uninstalling the Wubi Ubuntu.

If you set up a proper dual boot system then you are going to need the Windows boot disk or a Windows recovery partition to re-install the MBR so that it boots only Windows.

Chris

---

### Post by nevius on 2011-07-10
> **beeben said:**
> Hello,

  I am having an extremely frustrating time trying to just remove Ubuntu completely and format my MAIN drive. I do not have a second drive, I want to format my harddrive. In an HP laptop. I do not have a clue why this is so difficult. There are many posts about dl'ing this and that application to do this very simple task. I am obviously not a programmer and thought that it would be fun to try and learn. Well it has not been fun for me at all. So, someone, please, in plain English explain to me how to uninstall completely Ubuntu 10.04 whatever and format my drive. Thank you to all who can help and recognize my level of frustration.

We'll need some more information. 

Did you install Ubuntu inside Windows (WUBI), did you replace Windows with Ubuntu, or did you install them side by side (dual-boot)?

Why do you want to remove Ubuntu? 

Do you want to install Windows back on your computer?

Does your hard drive have multiple partitions?

Do you need to retain some data on your hard drive (ie a Windows Partition)?

----------------------------------
If you replaced Windows with Ubuntu and you want to reinstall Windows, then you just need to put the windows CD in your drive and boot from it. When you reinstall windows you can choose to reformat your hard drive.

If you are just trying to remove the GRUB bootloader, you can boot from the Windows CD and run 'fixmbr' from the recovery terminal. (I think this is right - the last version of Windows I used was Windows XP.)

---

### Post by dFlyer on 2011-07-10
Before you do anything please answer this? Do you have your windows install disk? or at least a clone of your original OS?

---

### Post by beeben on 2011-07-11
Hiya friends,

 I installed Ubuntu on a fresh drive from an install disk I downlaoded from my sisters laptop. There is no native Windows system of any kind on the HD. When I run fdisk all it shows is the Linux system there. So, I tried to install from Windows disk and as I read elsewhere before Windows says 'duh.... no NTFS file system.. duh... Installation will not continue...duh' Well, okay, it didn't say duh, but ya know. ;) The ONLY reason I need to go back to windows is because I just got a bunch of music and video editing work that I cannot afford to pass up, and I have never had luck using WINE to run anything. I do want to come back to Linux eventually, for the millions of reasons it makes sense, it just I don't have the time to learn how to code things in and I need the dough that I can make if I format the disk with NTFS and just throw Winshit on here. So, how do I do that? Thanks gents.:guitar:

---

### Post by wildmanne39 on 2011-07-11
Hi, boot the livecd then open gparted, you may have to install it but I do not think so,then click on the partitions and reformat them into one ntfs partition then shut down your computer and start it with the windows disk and follow the on screen instructions.

---

### Post by elliotn on 2011-07-11
I assume he want to install windows boot with your windows CD and format your drive and install windows...you can uninstall wubi in add and remove

---

### Post by rushikesh988 on 2011-07-11
> **beeben said:**
> Hiya friends,

 I installed Ubuntu on a fresh drive from an install disk I downlaoded from my sisters laptop. There is no native Windows system of any kind on the HD. When I run fdisk all it shows is the Linux system there. So, I tried to install from Windows disk and as I read elsewhere before Windows says 'duh.... no NTFS file system.. duh... Installation will not continue...duh' Well, okay, it didn't say duh, but ya know. ;) The ONLY reason I need to go back to windows is because I just got a bunch of music and video editing work that I cannot afford to pass up, and I have never had luck using WINE to run anything. I do want to come back to Linux eventually, for the millions of reasons it makes sense, it just I don't have the time to learn how to code things in and I need the dough that I can make if I format the disk with NTFS and just throw Winshit on here. So, how do I do that? Thanks gents.:guitar:
just run live Cd of ubuntu and format HDD using Gparted..or (I am not sure but) you might will be able to farmat HDD in windows setup too if its Win 7 ...

---

### Post by fabricator4 on 2011-07-12
> **beeben said:**
> Hiya friends,

 I installed Ubuntu on a fresh drive from an install disk I downlaoded from my sisters laptop. There is no native Windows system of any kind on the HD. When I run fdisk all it shows is the Linux system there. So, I tried to install from Windows disk and as I read elsewhere before Windows says 'duh.... no NTFS file system.. duh... Installation will not continue...duh' Well, okay, it didn't say duh, but ya know. ;) The ONLY reason I need to go back to windows is because I just got a bunch of music and video editing work that I cannot afford to pass up, and I have never had luck using WINE to run anything. I do want to come back to Linux eventually, for the millions of reasons it makes sense, it just I don't have the time to learn how to code things in and I need the dough that I can make if I format the disk with NTFS and just throw Winshit on here. So, how do I do that? Thanks gents.:guitar:

Hi beeben, as already said, boot off the LiveCD and run Gparted.  You don't need to install it as it's already there.  Delete the partitions and proceed with the Windows install normally.

I believe there's some very good sound and audio editing/arranging software available for Linux/Ubuntu.  Those in the field seem to think it is better than some of the Windows offerings - it's not my field so I can't vouch for that.  You might want to revisit Ubuntu again and see what's available.

In the meantime, I suggest you don't format the entire drive with Windows at this time. Make the Primary partition just large enough to do what you need to and leave the rest for now.  That way you could install Ubuntu on the rest of the drive later and have a dual boot system - that way Windows would always be available if a bit of work comes along and you need to use it, but you could be working on Linux/Ubuntu to get familiar and learn new programs.

Chris

---

### Post by ClientAlive on 2011-07-12
For future reference:

Video Editing -

[http://cinelerra.org/about.php]("http://cinelerra.org/about.php")

[http://youtu.be/jBs-biS8-y4]("http://youtu.be/jBs-biS8-y4")

[http://www.cyberciti.biz/faq/top5-linux-video-editing-system-software/]("http://www.cyberciti.biz/faq/top5-linux-video-editing-system-software/")

Audio Editing -

[http://en.wikipedia.org/wiki/List_of_Linux_audio_software]("http://en.wikipedia.org/wiki/List_of_Linux_audio_software")

Image Edtiting:

Inkscape -

[http://inkscape.org/]("http://inkscape.org/")

[http://inkscape.org/screenshots/index.php?lang=en]("http://inkscape.org/screenshots/index.php?lang=en")

[http://youtu.be/TLqhBroA_q0]("http://youtu.be/TLqhBroA_q0")

Gimp -

[http://www.gimp.org/]("http://www.gimp.org/")

[http://www.gimp.org/screenshots/]("http://www.gimp.org/screenshots/")

[http://youtu.be/8LmW5ndnEqw]("http://youtu.be/8LmW5ndnEqw")


I know it doesn't address your original question but it's info for you if you want it.  :wink:

HTH

---

### Post by hookitup on 2011-07-14
[http://www.dban.org/download](http://www.dban.org/download) boot and nuke will erase everything on the HD then find a windows torrent and create bootable disk then install drivers and ur good to go



good luck

---

### Post by 3rdalbum on 2011-07-15
If you've got Vista or 7, just put your Windows disc in and at the stage where it asks you where to install Windows, just use the window to remove the Ubuntu partitions and create a new NTFS partition.

If you've got Windows XP, then you need to boot up the Ubuntu CD in "Try Ubuntu" mode, and then use the Partition Editor program in System > Administration to remove the partition and create a new NTFS partition. Then before installing XP, go into your BIOS setup and change the SATA mode to "IDE" or "compatibility", because Windows XP's installer can't recognise SATA hard disks unless you make your BIOS pretend that they are IDE.

If that sounds like complete gobbledegook - then just get Windows 7. It's still not very good, but it's better than XP.

---


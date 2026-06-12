---
title: "Does Ubuntu partition?"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by Stargeezer59 on 2010-09-23
Hi
 
I dabbled in Linux years ago when a separate partition had to be created, root and user directories defined, and a boot menu built so you could add new kernals as you built them. Or choose Windows to start with. 
 
I am curious about the present crop of graphical distributions. Ubuntu has a Windows installer option that installs the program from within Windows, as do many modern versions of Linux. Do these installers move the existing Windows partitions and create new ones for Linux? Can you install other distributions such as Kubuntu or Debian in the same way? Does this create boot menus for the different versions? When is a manually created partition needed, or is it required anymore? I am confused with how these new distros cohabit with Windows on the same hard drive. 
 
Thanks

---

### Post by Calash on 2010-09-23
The installer you are speaking of, where it is installed as an application in Windows, is called Wubi.  It makes use of a virtual hard drive that exists as a file in your Windows directory structure.  Being that it is not a true partition no major changes occur to the computer.  Most people recommend it for testing as it can have issues with larger updates.

The Ubuntu disk, if you boot from it, also contains a LiveCD enviroment.  This gives you a CD based OS where you can test all the features, as well as perform diagnostic and repair functions.

Finally, if you choose to install Ubuntu will partition the disk however you want.  In this case it will also install the GRUB bootloader to the main drive, allowing "true" booting to all installed operating systems.  If you go this route be sure to defragment your Windows install before hand.  You may also want to do some searching for Windows 7 and Ubuntu dual boot so you can be prepared should anything go wrong.


Edit:  For some reason I thought you had said you were running Windows 7.  The last part is still important for any version of Windows but it seems to be more prevalent on the forums with the latest version.

---

### Post by Stargeezer59 on 2010-09-23
> **Calash said:**
> Finally, if you choose to install Ubuntu will partition the disk however you want. In this case it will also install the GRUB bootloader to the main drive, allowing "true" booting to all installed operating systems. If you go this route be sure to defragment your Windows install before hand. You may also want to do some searching for Windows 7 and Ubuntu dual boot so you can be prepared should anything go wrong.
 
That is the heart of my question. Does Ubuntu create true partitions from the existing Windows partition ( if, lets say, you only have one partition on the hard drive ). We did that in the old days with Partition Magic, which had is challenges. Or, do you have to create a new partition manually first, so that Ubuntu has something to work with. Which means formatting the hard disk, creating new partitions, then reinstalling Windows and all software?

---

### Post by Calash on 2010-09-23
If you are doing the full install it will shrink the existing Windows partition to the size you specify.  Then, by default, it will create 2 additional partitions for the Ubuntu install, swap and /.  This is all done by the installer, you just tell it the sizes you want and it will take care of the process.

The reason I posted so much the first time is that you described a Wubi install.  This is different in that it does not create a partition at all.  It uses a virtual disk that is a file in your Windows setup.

So, the answer is yes or no depending on the install you do but in neither case do you have to do any partitioning beforehand.

---

### Post by bowens44 on 2010-09-23
> **Stargeezer59 said:**
> That is the heart of my question. Does Ubuntu create true partitions from the existing Windows partition ( if, lets say, you only have one partition on the hard drive ). We did that in the old days with Partition Magic, which had is challenges. Or, do you have to create a new partition manually first, so that Ubuntu has something to work with. Which means formatting the hard disk, creating new partitions, then reinstalling Windows and all software?

Ubuntu will create partitions. It uses a tool called gparted to do this.This is part of the installation procedure. It would involve shrinking your windows partition and creating a partition for ubuntu. Although I have never installed linux along side of windows , I am sure that it steps you through the process.

ooops. Calash beat me to it.......

---

### Post by kendoori on 2010-09-23
I started with Wubi and used that until I felt comfortable to install Ubuntu as a dual boot. Wubi is completely safe and painless and is non destructive to Windows. At whatever point you are either ready to commit to Ubuntu, or back out, you just uninstall and you are back where you started. If you are squeamish about the whole partitioning thing, it is a great way to start.

As a long time Windows user, who previously used tools like Partition Magic, I've ultimately found Ubuntu/Linux partitioning pretty easy, either while using the LiveCD and stock installer, or from GParted. I eventually blew away my Windows partitions completely and now use VirtualBox when I need to access Windows specific application that don't run well under Wine.

---

### Post by QIII on 2010-09-23
If you dual boot, use the WINDOWS tool to defrag the drive (I recommend doing that twice) and the WINDOWS tool to manage the size of your Windows partition.

You never know what you are going to do to Windows if you blindly repartition with GParted.

Windows can be finicky about how much you can shrink your partition, so you may have to fiddle a bit.

Install Ubuntu on what space you are able to wrestle out of Windows' greedy paws.

---

### Post by uRock on 2010-09-23
> **QIII said:**
> If you dual boot, use the WINDOWS tool to defrag the drive (I recommend doing that twice) and the WINDOWS tool to manage the size of your Windows partition.

You never know what you are going to do to Windows if you blindly repartition with GParted.

Windows can be finicky about how much you can shrink your partition, so you may have to fiddle a bit.

Install Ubuntu on what space you are able to wrestle out of Windows' greedy paws.
That is why I prefer to back everything up and start a new partition table from scratch.:)

---

### Post by QIII on 2010-09-23
> **uRock said:**
> That is why I prefer to back everything up and start a new partition table from scratch.:)

That's why I wipe the drive clean and only use Windows in a vm!  ;)

---

### Post by Stargeezer59 on 2010-09-23
Well it all sounds good and I am keen to try the 10.10 release. Much of my software is Windows specific. Things like Cad programs, GIS and Photoshop. Also Astronomy software to capture photos and control the telescope. I suspect that Wine and Virtual Box are Windows emulators?  How well does Windows specific software run under Linux?

---

### Post by uRock on 2010-09-23
> **Stargeezer59 said:**
> Well it all sounds good and I am keen to try the 10.10 release. Much of my software is Windows specific. Things like Cad programs, GIS and Photoshop. Also Astronomy software to capture photos and control the telescope. I suspect that Wine and Virtual Box are Windows emulators?  How well does Windows specific software run under Linux?
VBox is a program where you have to install an OS and run it. [Wine is an emulator.]("http://appdb.winehq.org/") If you can't run your software in Windows in a VBox, then I recommend running Windows apps within Windows on its own partition.

---

### Post by Mark Phelps on 2010-09-24
> **Stargeezer59 said:**
> Well it all sounds good and I am keen to try the 10.10 release.
You DO understand that 10.10 just recently entered Beta testing, right?  As such, it is likely to have more bugs and be less stable than a prior release.  If you're eager to try out Ubuntu, you would do better going with 10.04 -- they've had some time to work out the bugs.  If you DO install 10.10, be sure to post your questions in the Maverick Development forum, not in this forum.
>  Much of my software is Windows specific. Things like Cad programs, GIS and Photoshop. Also Astronomy software to capture photos and control the telescope. I suspect that Wine and Virtual Box are Windows emulators?  How well does Windows specific software run under Linux?
To answer that for Wine, you need to go to the WineHQ application compatibility site and look up each app and version you want to run.  The link is below:

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

Anything rated Silver or below, or not listed, is pretty much a waste of time.

---


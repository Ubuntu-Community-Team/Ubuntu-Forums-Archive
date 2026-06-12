---
title: "dual booting with xp"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by nick1785 on 2009-11-08
Hello
 
I'm new to Ubuntu - thinking about dual booting with my existing xp - never partitioned a disc before - can I do it without losing all my files or will I always have to reinstall from back-up?
 
Thanks nick1785

---

### Post by kansasnoob on 2009-11-08
Do you know what your basic system specs are?

Especially CPU and RAM.

---

### Post by phillw on 2009-11-08
> **nick1785 said:**
> Hello
 
I'm new to Ubuntu - thinking about dual booting with my existing xp - never partitioned a disc before - can I do it without losing all my files or will I always have to reinstall from back-up?
 
Thanks nick1785


Follow the advice here, but DO make a backup in case you mess up, or get hit by a power cut 1/2 way thru'.

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

It has most bases covered ;-)

Welcome to ubuntu,

Phill.

---

### Post by arochester on 2009-11-08
Have a look at "How to dual boot Windows XP and Linux (XP installed first) -- the step-by-step guide with screenshots" on [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by gdonwallace on 2009-11-08
To determine if Ubuntu will run on your system, I would first start by burning the ISO to a cd and then boot from that cd.  It will give you an option to run Ubuntu from the cd and not install anything.  If that works, then you can start looking at dual boot.  The easy way of doing this is to do it through XP.  

After booting into XP, insert the Ubuntu CD and a menu will appear.  There will be an option to install inside windows.  Choose that option and it will set defaults as to how and where to install Ubuntu.  It will also setup the duel boot menu so that you can choose your OS at boot time.  This will keep your XP install complete and allow you to check out Ubuntu full power.  

As to accessing windows files through Ubuntu, you can do that.  Your windows partition will show up as another mount point in Ubuntu.  Just a matter of finding it.  Generally this is under /media or /mnt.  You will just need to use Nautilus to do this.  It is easier this way.

---

### Post by Paqman on 2009-11-08
> **nick1785 said:**
> never partitioned a disc before

It's actually not even compulsory to partition the disk to install Ubuntu. There is an installer called Wubi that gets it installed without partitioning. Just boot into Windows, pop the LiveCD in the drive and run the installer from within Windows. It'll create a clever virtual partition that sits on the Windows partition.

[More info about Wubi]("http://wubi-installer.org/").

---

### Post by phillw on 2009-11-08
> **gdonwallace said:**
> To determine if Ubuntu will run on your system, I would first start by burning the ISO to a cd and then boot from that cd.  It will give you an option to run Ubuntu from the cd and not install anything.  If that works, then you can start looking at dual boot.  The easy way of doing this is to do it through XP.  

After booting into XP, insert the Ubuntu CD and a menu will appear.  There will be an option to install inside windows.  Choose that option and it will set defaults as to how and where to install Ubuntu.  It will also setup the duel boot menu so that you can choose your OS at boot time.  This will keep your XP install complete and allow you to check out Ubuntu full power.  

As to accessing windows files through Ubuntu, you can do that.  Your windows partition will show up as another mount point in Ubuntu.  Just a matter of finding it.  Generally this is under /media or /mnt.  You will just need to use Nautilus to do this.  It is easier this way.


As a note to that, I'd actually run the live cd in "do not make changes mode", let you and it be happy that ubuntu can 'talk' to your computer systems various bits .. Some of that is detailed in my 9.10 blog, The rest of my expeirience of popping Ubuntu on is in my 'info' link.

For my own personal reasons, I do prefer ubuntu to be on a safe area of it's own to be able to rescue an 'infected' windows area. But, that's just IMHO.

Phill.

---

### Post by Pauly BC on 2009-11-08
+1 to Phillw. I founf Ubuntu worked better on a fresh partition rather than a virtual partition.

I have my PC triple-booting P, Vista and Ubuntu and it is very successful. I agree with the others that you should run off the live CD a few times to make sure Ubuntu is comfortable with your PC and you are comfortable with it.

I recommend making a backup of all your files both via the Windows backup utility and also just by copying your files to another media. The UNPLUG that media from your PC before you muck about with the hard drive. Two weeks ago when I reformatted my PC I forgot to unplug the backup media and I deleted the FAT. I recovered most files but that is an experience I would wish upon nobody.

Use the free utility nView to update your XP install CD with the latest service packs, plus you can slipstream in your device drivers from the start. It turns a multi-day reload process into a quick install. Install nView, make a new folder on your HDD, copy the XP install into that folder, download drivers and service packs, launch nView and use it to inject the drivers into the CD, then burna  new disk. Very slick! 

p

---

### Post by Paddy Landau on 2009-11-08
Just a couple of points about what's been discussed.

Yes, you can just go ahead and partition. BUT sometimes things go wrong for no apparent reason, and then you will be ECSTATIC that you backed up first! 

I recommend that you use [CloneZilla]("http://clonezilla.org/") to back up your entire hard drive (you'll need an external hard drive to back it up onto), so in the worst case scenario, you can just restore the entire hard drive.

Before you partition your drive, on Windows run [CCleaner]("http://www.ccleaner.com/") then System Cleanup, then [Auslogics Disk Defrag]("http://www.auslogics.com/disk-defrag"). It will aid the process. If possible, shrink your Windows partition using Windows software, because sometimes GParted causes problems.

[Wubi]("http://wubi-installer.org/") is an **excellent** way to become used to Ubuntu and to experiment. It installs into Windows as though it were just another program -- no worries about partitioning, GParted and so forth.

But, Wubi does come with limitations, so use it only to experiment and decide whether you want to go serious.

Then, if you wish to go serious with Ubuntu, uninstall Wubi and install Ubuntu properly.

---

### Post by sailor2001 on 2009-11-08
#1 Defrag you windows

#2 download Ubuntu 9.10 (32 bit?) and burn it as an ISO

#3 boot into ISO an check if everything is working properly (wireless, etc.)

#4 Install with icon on desktop

#5 select "side by side" mode

#6 slider.. set your windows partition to what ever you want it to be.. If you have enough room, I'd suggest leaving your ubuntu partition at least 20 gigs to allow a lot of room to move about. If you are a collector (mp3, mpeg) give it more room.

---

### Post by phillw on 2009-11-08
> **Paddy Landau said:**
> Just a couple of points about what's been discussed.

Yes, you can just go ahead and partition. BUT sometimes things go wrong for no apparent reason, and then you will be ECSTATIC that you backed up first! 

I recommend that you use [CloneZilla]("http://clonezilla.org/") to back up your entire hard drive (you'll need an external hard drive to back it up onto), so in the worst case scenario, you can just restore the entire hard drive.

Before you partition your drive, on Windows run [CCleaner]("http://www.ccleaner.com/") then System Cleanup, then [Auslogics Disk Defrag]("http://www.auslogics.com/disk-defrag"). It will aid the process. If possible, shrink your Windows partition using Windows software, because sometimes GParted causes problems.

[Wubi]("http://wubi-installer.org/") is an **excellent** way to become used to Ubuntu and to experiment. It installs into Windows as though it were just another program -- no worries about partitioning, GParted and so forth.

But, Wubi does come with limitations, so use it only to experiment and decide whether you want to go serious.

Then, if you wish to go serious with Ubuntu, uninstall Wubi and install Ubuntu properly.


The tend of this thread is to BACKUP !!, As one of the regulars has in his sig .... if you do not back up your important data, you're data is obviously not important.

As noted in my installation of Ubuntu - Make sure the ethernet cable is un-plugged if you have WiFi. I don't know if this has been fixed in 9.10, but it caused me soooooo much grief.

As I use a script for my backups (certain things I prefer to roll me sleeves up and get done the 'old-fashioned' way) I cannot state for any GUI app, I've always used boot from 'liveCD' and tell it what I want backing up. But, again, that's just IMHO

Phill.

---


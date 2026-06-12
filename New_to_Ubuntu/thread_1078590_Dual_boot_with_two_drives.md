---
title: "Dual boot with two drives"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by henrywm on 2009-02-23
I have played with Linux from time to time (mainly Ubuntu), but the laptop I have used is so old that it is hard to give a fair assessment. I now use a desktop with a spare bay for another drive. The current drive uses Windows MCE 2005. I am thinking of building a dual boot with Ubuntu or a derivative (Mythbuntu or Linux MCE) in another drive. How can I do this?

---

### Post by sleepyjon on 2009-02-23
Just boot from the liveCD and install onto the second drive. That easy.

---

### Post by Doug11 on 2009-02-23
> **henrywm said:**
> I have played with Linux from time to time (mainly Ubuntu), but the laptop I have used is so old that it is hard to give a fair assessment. I now use a desktop with a spare bay for another drive. The current drive uses Windows MCE 2005. I am thinking of building a dual boot with Ubuntu or a derivative (Mythbuntu or Linux MCE) in another drive. How can I do this?

This should help you,,
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dual+boot+drives](http://ubuntuforums.org/showthread.php?t=179902&highlight=dual+boot+drives)

---

### Post by Therion on 2009-02-23
Having done this in the past I don't suggest it.  Do as you will, it's your system, but I don't suggest it.  

I build nothing BUT dual-drive systems and I have separate drive cages for this: One marked "Stable" and one marked "Experimental".  I hope that's self-explanatory.  
The two minutes it takes it to swap drives/cages is well worth it in terms of overall stability and experimental freedom.  

Just my advice.

---

### Post by henrywm on 2009-02-23
What are the problems?

---

### Post by cjv8888 on 2009-02-23
I have six computers at home and four of them are dual booting Ubuntu with Windows . One is triple booting with 2 versions of windows.  They all have dual harddisks.  It is very easy if you prepare a bit and read up a bit about grub like [this page]("http://users.bigpond.net.au/hermanzone/p15.htm#17")
 If you run into problems you can always post here for help.

---

### Post by henrywm on 2009-02-25
Do I need to make a fresh install of Windows to make it work properly, or can I do it on a system which already has Windows without reinstalling?

---

### Post by cjv8888 on 2009-02-26
> **henrywm said:**
> Do I need to make a fresh install of Windows to make it work properly, or can I do it on a system which already has Windows without reinstalling?

You can do it on a system which already has Windows, no need to make a fresh install.

---

### Post by tarps87 on 2009-02-26
You can do it on a system already running windows, if you set the Ubutnu drive as the master drive grub will be installed onto this drive, this means that if you remove the Ubuntu drive and set the windows drive as master it will run normally (I do this when I reinstall windows so I don't have to reinstall the grub).
I have been running Ubuntu and xp on a dual boot, dual hard drive system for about three years now and haven't has any problems so far. I also have a triple boot with Ubuntu, Slackware and Fedora on one hard drive and have see no problems or notice any difference between having them on the same hard drive or separate ones.
One thing I would suggest is to backup the important data from the windows drive first, just incase you accidentally select the wrong drive to format

---

### Post by caljohnsmith on 2009-02-26
> **tarps87 said:**
> You can do it on a system already running windows, if you set the Ubutnu drive as the master drive grub will be installed onto this drive, this means that if you remove the Ubuntu drive and set the windows drive as master it will run normally (I do this when I reinstall windows so I don't have to reinstall the grub).
Setting the Ubuntu drive to master drive when installing Ubuntu is one way to help ensure that Grub gets installed to the Ubuntu drive and not the Windows drive, but it's not really necessary to go to that trouble. **Henrywm**, when you go through the Ubuntu installer to install Ubuntu to its own drive, click the "Advanced" button near the end of the installation process, and there you can specify to have Grub installed to "/dev/sdb" or whichever is the drive you are installing Ubuntu to. That way your Windows drive will remain untouched. To boot the Ubuntu drive, simply change your BIOS boot order, or if you have a quick boot menu via F10/F12 or some key like that, you can specify to boot the Ubuntu drive that way. Good luck and let us know how it goes.

---

### Post by tarps87 on 2009-02-26
> **caljohnsmith said:**
> Setting the Ubuntu drive to master drive when installing Ubuntu is one way to help ensure that Grub gets installed to the Ubuntu drive and not the Windows drive, but it's not really necessary to go to that trouble. **Henrywm**, when you go through the Ubuntu installer to install Ubuntu to its own drive, click the "Advanced" button near the end of the installation process, and there you can specify to have Grub installed to "/dev/sdb" or whichever is the drive you are installing Ubuntu to. That way your Windows drive will remain untouched. To boot the Ubuntu drive, simply change your BIOS boot order, or if you have a quick boot menu via F10/F12 or some key like that, you can specify to boot the Ubuntu drive that way. Good luck and let us know how it goes.

True, it's one of these historic things that I should do the proper way. I use to do it when I first started using GNU/Linux.

---

### Post by Radioman991 on 2009-02-26
My 0.02

I have a Dell desktop with 2 IDE drives.  I dual boot XP or Ubuntu.

I used this after a couple weeks of screwing up my Windows MBR...


[http://ubuntuforums.org/showthread.php?t=538245](http://ubuntuforums.org/showthread.php?t=538245)

Follow the links in this post, and it should accomplish the OP's goal...at least it did for me.

YMMV

PK

---


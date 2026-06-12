---
title: "How to dual boot Windows 7, and Ubuntu?"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by php111 on 2011-08-11
Hey everyone,

How's everyone doing? I'm new here, and new to Linux as well.

I am thinking about saving up some money to get a MacBook Pro. I have to see how my finances are. My main goal is to get rid of MS. I know this is an Ubuntu forum. I won't talk about Apple.

Does someone have time, and patience to walk me through the dual booting process of getting Ubuntu, and Win 7 up and running without the command line? I don't know how the /dev, or /hda, or whatever it's called. I don't know how to do it even if I had a tutorial in front of me.

I have a could of partitions setup on my PC. I don't have a USB HD either. I wanted to go the whole process for free since I don't have money. I am kind of worried that my Music partition will get destroyed.

Would someone help me get all of my drivers working?

Would I be able to run 32-bit Windows apps under Ubuntu without using Ubuntu's apps? I am familiar with Windows apps.

Where can I download Ubuntu from?

Thank you,

---

### Post by pckrfan75 on 2011-08-11
I'm somewhat new as well, but from what I understand, if you download ubuntu from ubuntu.com it comes with a very hands free installer that comes with a dual boot software on the GRUB2 bootloader. So all you would need to do is partition your HDD into to make room for the new OS and then the installer will do the rest of the work if you select the install side by side option.

---

### Post by php111 on 2011-08-11
Thank you. I'm totally confused. I'll say I wait until more replies comes. I would have to say this is way above my level. I'm sorry about that.

---

### Post by pckrfan75 on 2011-08-11
We all encounter something that is above our level at some point. Also, I plan on running the exact install you're talking about later tonight, so when that is done I will post my results for you.

---

### Post by php111 on 2011-08-11
> **pckrfan75 said:**
> We all encounter something that is above our level at some point. Also, I plan on running the exact install you're talking about later tonight, so when that is done I will post my results for you.

Thank you! Are you planning on dual booting with Windows 7 may I ask? Do I have to delete all of my Windows partitions except for Windows? What should I do about all of my drivers to get them recognized?

---

### Post by BlinkinCat on 2011-08-11
You both could look at this guy's Signature links - :)

[http://ubuntuforums.org/showpost.php?p=11139774&postcount=3](http://ubuntuforums.org/showpost.php?p=11139774&postcount=3)

---

### Post by pckrfan75 on 2011-08-11
> **php111 said:**
> Thank you! Are you planning on dual booting with Windows 7 may I ask? Do I have to delete all of my Windows partitions except for Windows? What should I do about all of my drivers to get them recognized?

yes I am going to dual boot with win7. All I plan on doing is taking around 15 gigs of my main Windows partition (the one used for file storage) and making 10gb for the OS and 5 for the swap partition. Then running the installer and directing it to put the OS into the 10gb slot. Then I will just mount the data storage Windows partition to the linux desktop and changing program directories to save there. As far as your drivers, I'm confused as to what you're asking.

---

### Post by x-D on 2011-08-11
> **php111 said:**
> Thank you. I'm totally confused. I'll say I wait until more replies comes. I would have to say this is way above my level. I'm sorry about that.

Hey, I take it that you have Windows 7 currently installed, already?

If so, then all you would need to do is go to: 
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

And download the newest version of Ubuntu (currently 11.04). Choose either 32 or 64-Bit, depending on what type of Computer you have. To find out in Windows 7, go to the Start Menu, right-click on Computer and press properties, the system properties will come up and you will be able to see if you have a 32 or 64-Bit Computer.

Then when you have downloaded the Ubuntu file (.iso) download a program called InfraRecorder and then insert a CD or DVD into your CD/DVD Drive. If you don't have a CD Drive, tell me and I will tell you how to do this with a USB (more complex). Burn the ISO to the Disk, at the lowest possible burn rate.

Then leave the Disk in the tray, shut down your computer, and then reboot. You will come to the Ubuntu Installer.

Click "Install Ubuntu". Then "Install Ubuntu alongside Windows 7". 

Choose how much space you wish to allocate to each Operating System. I will help you with the rest after you have done all this, as it can start to get more difficult and I need to have more of a think about it and what you really want.

Hope this helps....

x-D :guitar:

---

### Post by BlinkinCat on 2011-08-11
It is for XP but system is similar - This is for Windows 7
[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

---

### Post by x-D on 2011-08-11
> **BlinkinCat said:**
> It is for XP but system is similar - This is for Windows 7
[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

Don't worry about it, I will give them a 1 to 1 bit of help, just in case they run into any trouble. Giving them links could confuse them if they don't understand some of the things mentioned.

---

### Post by php111 on 2011-08-11
Hey x-D,

Yes, I have Windows 7. I'll follow your instructions. Thank you so much for your time, and help. I have an iPhone, so I can post away.

---

### Post by x-D on 2011-08-11
> **php111 said:**
> Hey x-D,

Yes, I have Windows 7. I'll follow your instructions. Thank you so much for your time, and help. I have an iPhone, so I can post away.

Alrighty, have you started with the download yet, I usually get around 250 - 350 kb/s around here, and it took around 55 - 60 mins to download, so I'm not sure how long it will take wherever you are. :P

Internet is slow here for big downloads, but for doing web activities and games, there is no difference, because the pages etc are so small. Except some games lag badly for the first 20-30 secs, until they properly load haha :) 

x-D :guitar:

---

### Post by php111 on 2011-08-11
> **x-D said:**
> Alrighty, have you started with the download yet, I usually get around 250 - 350 kb/s around here, and it took around 55 - 60 mins to download, so I'm not sure how long it will take wherever you are. :P

Internet is slow here for big downloads, but for doing web activities and games, there is no difference, because the pages etc are so small. Except some games lag badly for the first 20-30 secs, until they properly load haha :) 

x-D :guitar:

The download is done. It took about 20 mins, and I already burned it. I'll post back.

---

### Post by x-D on 2011-08-11
> **php111 said:**
> The download is done. It took about 20 mins, and I already burned it. I'll post back.

Looks like you get decent Internet speeds :). I have to wait too long for it to download haha. Oh well, it is bearable and at least everyday and recreational tasks are fine.

I will continue to support you here :)

---

### Post by php111 on 2011-08-11
> **x-D said:**
> Looks like you get decent Internet speeds :). I have to wait too long for it to download haha. Oh well, it is bearable and at least everyday and recreational tasks are fine.

I will continue to support you here :)

LOL. I went ahead with along the side option as well as Install Now. Would that be fine?

---

### Post by Mark Phelps on 2011-08-11
> **php111 said:**
> LOL. I went ahead with along the side option as well as Install Now. Would that be fine?

If by that, you mean you used the Ubuntu installer to shrink your Win7 OS to make room for Ubuntu -- maybe NOT.

That has a history of corrupting Win7 installs and rendering them unbootable.

If you've already done this, then boot back into Win7 first channce you get and confirm it will restart.  If it does, then use the Backup feature to create and burn a Win7 Repair CD.  This will come in handy later, should you need to repair Win7 for any reason.

If you've NOT already done this, then DON'T. Instead, use the Win7 Disk Management utility to shrink the Win7 OS partition.  Leave the new space as unallocated and let the Ubuntu installer format it.

---

### Post by php111 on 2011-08-11
Neither Ubuntu, or Win7 won't boot. I checked the BIOS settings, and CD-ROM was set first, and HDD was set second. I switched them around, neither OS will boot. However, a few days ago I did made a Win7 Repair CD.

---

### Post by x-D on 2011-08-11
> **php111 said:**
> Neither Ubuntu, or Win7 won't boot. I checked the BIOS settings, and CD-ROM was set first, and HDD was set second. I switched them around, neither OS will boot. However, a few days ago I did made a Win7 Repair CD.

So you have resized the partition? That SHOULD work. Well, if this is the case, try booting up from the Live CD, and then maybe it's to do with Windows and GRUB? Well we'll see. Once you're in the Live CD go to Try Ubuntu, Install a utility called "Boot-Repair" and then run it (System====> Administration =======> Boot-Repair)
or search for it in Unity, allow it to reinstall GRUB, putting - go to advanced options to choose whether Ubuntu or Windows will be the default Operating System. Then post back with what happened!

x-D :guitar:

---

### Post by php111 on 2011-08-12
Hey,

I'll give it another try. This time I'll wait for replies instead of jumping the gun.

How do I partition my HDD to have Windows 7? 

How do I setup my boot loader, so I can have a choice of what OS I can pick from?

The first time I didn't get any OS, so I took my Windows, and put it back on.

I'll be more patient this time.

---


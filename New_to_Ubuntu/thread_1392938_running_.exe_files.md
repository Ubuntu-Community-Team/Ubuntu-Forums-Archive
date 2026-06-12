---
title: "running .exe files?"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by pink87 on 2010-01-28
how do I run a exe. file in Ubuntu?

---

### Post by Paqman on 2010-01-28
Generally you don't. 

.exe files are for Windows. If you let us know what you're trying to run, we can help you find a Linux equivalent.

There is a system called Wine that you can install that will let you run some Windows apps, sometimes, but you're better off with a Linux app if there's one available.

---

### Post by pink87 on 2010-01-28
well i am actually trying to install Windows and the setup is .exe. I would like ti dual boot.

---

### Post by Paqman on 2010-01-28
Ah, right. You'll need to boot from your Windows disk to do that.

First, i'd create some space on your drive to install Windows into. You can do that by booting into your LiveCD and using Gparted (System > Admin > Partiion Editor) to shrink your Ubuntu partition and leave some free space, you'll need about 20GB, plus space for programs.

Then you can boot into your Windows disk and install it into the free space. Make sure you don't accidentally wipe out your Ubuntu install.

After that you'll need to [reinstall Grub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") to get your boot menu back.

---

### Post by pink87 on 2010-01-28
LiveCD? Is that my Ubuntu installation CD? Can you explain partitions and will shrinking one hurt the files?

---

### Post by Techsnap on 2010-01-28
Yes that is your Ubuntu installation CD. You should ideally install Windows before Linux.

---

### Post by Paqman on 2010-01-28
Yep, your LiveCD is the one you installed from. Besides being able to install Ubuntu with it, you can run a full version of Ubuntu completely off the CD, which is very handy when you don't want the hard drive to be in use (such as when you're modifying partitions).

In order to have a dual boot system you have to create partitions. Shrinking a partition doesn't hurt the data on that partition, although it's always a good move to take a backup before messing about with your drive.

When you installed Ubuntu it would have created partitions for you. You'll have one big one formatted as EXT3 or EXT4 that will take up almost all the drive. Then you'll have a tiny one called swap that might have something called an extended partition around it. Don't worry too much about that. When you're in Gparted, just right click on your biggest partition > Resize > drag the handle on the bar to create at least about 20,000MB of space before it and hit apply. It will take quite a while to do this, so make sure it's on AC power if it's a laptop, and just let it run.

This puts a large area of free space on the drive, so that when you fire up the Windows installer you can easily spot where you should install Windows on the drive.

Make sure you've left at least about 20% of extra room on the Ubuntu partition, by the way. If a system fills up too much of the available space, performance will start to suffer.

---

### Post by pink87 on 2010-01-28
So in creating a partition I will have a part that is for Windows only and a part for Ubuntu only?

---

### Post by Roger Allott on 2010-01-28
> **pink87 said:**
> well i am actually trying to install Windows and the setup is .exe. I would like ti dual boot.

You don't install Windows with an .exe file. My guess is that you already run Microsoft Windows, you're looking to have a dual-boot set-up with Ubuntu, and you want to install Ubuntu using the wubi.exe file.

Is that a bit more like what you want to do?

---

### Post by pink87 on 2010-01-28
> **Roger Allott said:**
> You don't install Windows with an .exe file. My guess is that you already run Microsoft Windows, you're looking to have a dual-boot set-up with Ubuntu, and you want to install Ubuntu using the wubi.exe file.

Is that a bit more like what you want to do?

@Roger No I have a blank hard drive with no Windows version of any kind on it. 

@Paq thank you for your help so far. I have booted the CD how do I get to the Gparted? Or am I missing a step...

---

### Post by chaanakya_chiraag on 2010-01-28
System->Administration->Partition Editor (or something like that)

---

### Post by Psyco430404 on 2010-01-28
assuming he doesn't have any real work done, wouldn't it be easier to format his drive, clean install windows, then using disk manager shrink his partition and then install Ubuntu again in the free space, more importantly, why do you need windows? Most main stream aps can be run using wine

---

### Post by pink87 on 2010-01-28
I am not seeing Partition Manager any where on my desktop.

---

### Post by Paqman on 2010-01-28
IIRC they changed the name in the menu at some point. It'll either be under System > Admin > Gparted or System > Admin > Partition Editor.

Or you could just hit Alt-F2 and type:
```
gksu gparted
```

---

### Post by Psyco430404 on 2010-01-28
sudo apt-get gparted

---

### Post by chaanakya_chiraag on 2010-01-28
I think you mean
```
sudo aptitude install gparted
```

---

### Post by Paqman on 2010-01-29
It's on the LiveCD already anyway. And if it wasn't, the best place for newbies to get their software is Applications > Ubuntu Software Centre. Terminal witchcraft not required ;)

---

### Post by chaanakya_chiraag on 2010-01-29
@Paqman: I know it's not REQUIRED, but it's much easier to post a command rather than a whole list of "click on this", "select this", etc.  Besides, a little terminal knowledge never hurt anyone :D

---

### Post by Merk42 on 2010-01-29
I hope you have a full retail (or OEM) copy of Windows and not an upgrade copy...

---

### Post by Prodromus on 2010-01-29
No, an upgrade copy of windows should work- if it's windows 7 that is.  The upgrade  disk is capable of a full new install- that's how I did mine.  Surprisingly it never asks for the key to your old copy, maybe at some point in the future microsoft will shut your  copy off if you can't input a key, but for now it works fine to install from an upgrade disk. :)

---

### Post by Paqman on 2010-02-03
> **chaanakya_chiraag said:**
> it's much easier to post a command rather than a whole list of "click on this", "select this", etc.

Easier for *you* maybe, but not for the person reading it.

---

### Post by chaanakya_chiraag on 2010-02-03
I know.  That's why I try to give GUI directions if possible, but when it would get too tedious, I usually opt for the command-line solution :)

---


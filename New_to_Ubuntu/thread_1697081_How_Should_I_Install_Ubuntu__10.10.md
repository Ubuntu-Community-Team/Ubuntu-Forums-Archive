---
title: "How Should I Install Ubuntu  10.10  ?"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by KingLex on 2011-02-28
Hey I recently formatted my 500 external HDD due to grub problems and i decided to re-install Ubuntu
I wanted to know how should I set up my boot , root files and such so that i wont have problems after 
installing and im using Windows Vista Home Version...
and also im trying to have Ubuntu boot from any computer with no hassle at all how would i go about it 
that way as well ? Thanks in advance

---

### Post by turtle153 on 2011-02-28
The easiest and most supported way is to Dual-boot Ubuntu and Windows, so you choose between them at startup.
It's really very simple and all you need to do is create an Ubuntu install disk and boot up with it in your computer. In the installer you'll get asked how you want to install Ubuntu; you need to select "Install side by side, choosing between each at startup". If you want you can specify the about of space each system has, but Ubuntu can take care of that for you.

Wait for the install to finish and when the computer restarts you'll get the option to boot Ubuntu or Windows

---

### Post by YesWeCan on 2011-02-28
If you are installing Ubuntu on the external drive make sure the Grub bootloader is installed to this drive's MBR. View the "advanced" menu in the partitioner. Otherwise, you won't be able to boot into Vista when the external drive is disconnected.

---

### Post by seawolf167 on 2011-03-01
Here is a [how-to ]("https://help.ubuntu.com/community/WindowsDualBoot")for installing Windows & Ubuntu for dual booting

At the very least, I suggest separate /home and / partitions. You can set this up in the installer prompts.

---

### Post by KingLex on 2011-03-01
> **YesWeCan said:**
> If you are installing Ubuntu on the external drive make sure the Grub bootloader is installed to this drive's MBR. View the "advanced" menu in the partitioner. Otherwise, you won't be able to boot into Vista when the external drive is disconnected.

yes im kinda stuck on how do install Ubuntu on it tho...with out messing up something 
it keeps giving me the Windows Vista HDD - when i simply want the external 
im doin this from USB - like how do install it all on that - and still can swap thru grub ?

> **seawolf167 said:**
> Here is a [how-to ]("https://help.ubuntu.com/community/WindowsDualBoot")for installing Windows & Ubuntu for dual booting

At the very least, I suggest separate /home and / partitions. You can set this up in the installer prompts.

how should i install it manually is what im asking ? instead of using the whole hdd - use like 
200GB of it and still be able to use windows - if thats possible :confused:

---

### Post by seawolf167 on 2011-03-01
> **KingLex said:**
> how should i install it manually is what im asking ? instead of using the whole hdd - use like 200GB of it and still be able to use windows - if thats possible

When you get to the partition setup while running the installer, select the "specify partitions manually" option. 

You'll then be able to select the drive you wish to partition and setup the drive's partition table. If you have to resize your Windows partition, you should resize it using the builtin Windows partition editor rather than GParted or similar.

You can then set your / partition (at least 10GB is recommended), your swap partition (I suggest whichever is less: 2GB or 2x your amount of RAM), and finally your /home partition (all the rest of the space).

Before you install though, I highly suggest you clone you drive with [Clonezilla ]("http://www.clonezilla.org")in case something goes wrong and you have to recover your data. With Clonezilla you can just reimage back to the drive as if nothing ever happened and try again.

---

### Post by KingLex on 2011-03-01
> **seawolf167 said:**
> When you get to the partition setup while running the installer, select the "specify partitions manually" option. 

You'll then be able to select the drive you wish to partition and setup the drive's partition table. If you have to resize your Windows partition, you should resize it using the builtin Windows partition editor rather than GParted or similar.

You can then set your / partition (at least 10GB is recommended), your swap partition (I suggest whichever is less: 2GB or 2x your amount of RAM), and finally your /home partition (all the rest of the space).

Before you install though, I highly suggest you clone you drive with [Clonezilla ]("http://www.clonezilla.org")in case something goes wrong and you have to recover your data. With Clonezilla you can just reimage back to the drive as if nothing ever happened and try again.

thanx - but im installing it on my external hdd - i just wanted to know a way of goin about it - with no hassle and if possible boot from other PC's as well

---

### Post by YesWeCan on 2011-03-01
> **KingLex said:**
> yes im kinda stuck on how do install Ubuntu on it tho...with out messing up something 
it keeps giving me the Windows Vista HDD - when i simply want the external 
im doin this from USB - like how do install it all on that - and still can swap thru grub ?

The way it works is that two things are installed: Ubuntu and Grub. Grub will give you a menu that allows you to boot either Ubuntu or Vista. But it is important the Grub is located on your external HDD along with Ubuntu.

I cannot recall the install details (it has been a while). But I have a feeling that the installer will default to putting Grub on your internal HDD unless you tell it to do otherwise.

---

### Post by KingLex on 2011-03-01
> **YesWeCan said:**
> The way it works is that two things are installed: Ubuntu and Grub. Grub will give you a menu that allows you to boot either Ubuntu or Vista. But it is important the Grub is located on your external HDD along with Ubuntu.

I cannot recall the install details (it has been a while). But I have a feeling that the installer will default to putting Grub on your internal HDD unless you tell it to do otherwise.

well how about this when i get ready to install it since u can 
be on the internet while setting it up could i give u a run down and such - do u think u can help me during that part ?

---

### Post by walt.smith1960 on 2011-03-01
> **KingLex said:**
> thanx - but im installing it on my external hdd - i just wanted to know a way of goin about it - with no hassle and if possible boot from other PC's as well

I haven't done this and could be full of it so take this for what it's worth.  If your PC BIOS wil let you boot from an external HDD and you can set boot order, here is how I'd do it.  Plug the external drive in and make sure it's recognized from a LiveCD or LiveUSB setup.  I'd start the installer and when it get to "where to do you to install this?"  select manual or advanced.  See if your external hard drive is an option.  If so, install everything including GRUB on the external hard drive, this can be tricky because it's not obvious.  Let it install on the external drive and it shouldn't touch the internal hard drive.  

When you want to run Linux plug the external hard drive in, it should boot before the internal hard drive.  When you want to run Windows, shut down Linux, unplug the external hard drive and restart.  Windows should load normally I would think.  It shouldn't be that different from running a Live install except you can save settings and data.  I'm not sure the external hard drive would work properly when plugged into other PCs with different hardware than the one on which the external hard drive install was done.  Linux doesn't have a registry (thank goodness!!) but it still looks at hardware when it installs.

---

### Post by amjjawad on 2011-03-01
> **KingLex said:**
> Hey I recently formatted my 500 external HDD due to grub problems and i decided to re-install Ubuntu
I wanted to know how should I set up my boot , root files and such so that i wont have problems after 
installing and im using Windows Vista Home Version...
and also im trying to have Ubuntu boot from any computer with no hassle at all how would i go about it 
that way as well ? Thanks in advance

It depends what Boot Loader you want it to take the control over booting your system?

A) If you want GRUB2 to be your main Boot Loader then during Installation, make sure GRUB2 will be installed in the MBR of your "Internal HDD".

**Note that:** If you want to get rid of Ubuntu later on, you'll need to restore the MBR using Windows Disc.

B) If you're looking for more flexibly, make sure to install GRUB2 during the installation of Ubuntu in the MBR of your "External HDD".

**Note that:** The MBR of your internal HDD won't be used at all so you'll not mess around with it. Your machine will be able to boot from your External HDD as long as it's connected AND your BIOS set to boot from USB/External HDD.
As long as your External HDD is not plugged in, your machine will boot normally into Windows.


Hope that what you were looking for!

---

### Post by KingLex on 2011-03-01
> **amjjawad said:**
> It depends what Boot Loader you want it to take the control over booting your system?

A) If you want GRUB2 to be your main Boot Loader then during Installation, make sure GRUB2 will be installed in the MBR of your "Internal HDD".

**Note that:** If you want to get rid of Ubuntu later on, you'll need to restore the MBR using Windows Disc.

B) If you're looking for more flexibly, make sure to install GRUB2 during the installation of Ubuntu in the MBR of your "External HDD".

**Note that:** The MBR of your internal HDD won't be used at all so you'll not mess around with it. Your machine will be able to boot from your External HDD as long as it's connected AND your BIOS set to boot from USB/External HDD.
As long as your External HDD is not plugged in, your machine will boot normally into Windows.


Hope that what you were looking for!

i think C - would be more likely to what i need to do (not installing it at all)  - the computer im on is not my computer but the external hdd is - im not tryna install noting on the internal hdd and have problems in the future - is it possible for me to have Ubuntu to run off my hdd but just adding a swap ? and or other computers as well ? if not ill just stick to using Windows :(

---

### Post by amjjawad on 2011-03-01
> **KingLex said:**
> i think C - would be more likely to what i need to do (not installing it at all)  - the computer im on is not my computer but the external hdd is - im not tryna install noting on the internal hdd and have problems in the future - is it possible for me to have Ubuntu to run off my hdd but just adding a swap ? and or other computers as well ? if not ill just stick to using Windows :(

If what you're asking for and need is to install Ubuntu on an external HDD/USB to avoid messing the internal HDD then the 3rd link in my signature ([http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)) is what are you looking for.

Keep in mind that every machine has different Hardware Configuration than the other (obviously) so don't expect your external HDD (with Ubuntu installed on) will work "out-of-the box" on any machine. Sometimes, you need to do some extra steps. Yes, to be more specific, I'm talking about the Graphics Card.

However, the Live CD does exist for a reason. You can "TRY" Ubuntu from the Live CD and see how it will work on that machine and if everything is okay, you can go a head and install to your external HDD. 

You could do the same with your own PC/Laptop. I mean you could install Ubuntu on an external HDD/USB if you don't want to mess with the internal HDD.

Trust me, once you'll "understand" Ubuntu and start using it, you will NOT go back to Windows ;)

---

### Post by YesWeCan on 2011-03-01
> **KingLex said:**
> well how about this when i get ready to install it since u can 
be on the internet while setting it up could i give u a run down and such - do u think u can help me during that part ?
I would be happy to help you. I am not sure whether we will be online at the same time.
Don't get too confused by all the stuff being discussed here. Keep it simple. It isn't hard to do a guided install (I think that is what i is called) on your external USB. And you just have to keep an eye open for the place where you can choose to install grub. Don't worry about getting it wrong, it can be fixed afterwards. Just take your time and it will all make sense.

Just make sure you don't install to your Vista disk by mistake (probably called sda) bcause that cannot be fixed afterwards. :)

---

### Post by KingLex on 2011-03-02
> **YesWeCan said:**
> I would be happy to help you. I am not sure whether we will be online at the same time.
Don't get too confused by all the stuff being discussed here. Keep it simple. It isn't hard to do a guided install (I think that is what i is called) on your external USB. And you just have to keep an eye open for the place where you can choose to install grub. Don't worry about getting it wrong, it can be fixed afterwards. Just take your time and it will all make sense.

Just make sure you don't install to your Vista disk by mistake (probably called sda) bcause that cannot be fixed afterwards. :)

I see - im full aware of Ubuntu - as i stated b4 i had install 
it once b4 on my external hdd i just couldnt get my grub figured out and decided to re-install it.....

As far as the install part - how could we go about it ? as in the different time zones as u stated ? could pictures work ? ill screen shot the manually set up and u can tell me how to do the 
root , home , and the rest...cool ? :lolflag:

---


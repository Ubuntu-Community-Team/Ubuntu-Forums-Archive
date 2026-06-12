---
title: "Dual-boot Ubuntu/WIndows 7 on Dell Studio 15"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by Bv202 on 2010-10-11
Hey,

A few years ago, I've tried to work with Ubuntu, but my experiences weren't that positive.

I've tried running Ubuntu 10.10 on a VM yesterday and I liked it, so I would like to create a dual-boot with Windows 7. However, I have a few concerns before doing this. My specs are:

Model: Dell Studio 1558
CPU: i5 520m
GPU: ATI HD5470
Battery: 9-cell
Screen: 1920x1080 Full HD resolution
Wireless: Intel 6200
RAM: 4GB

1) Do I have to install the 32-bit or 64-bit version? I heard you can use the full 4GB RAM on 32-bit with Linux, is that true?

2) The dual-booting itself. A few years ago, I had to create all partitions itself with a nice tutorial (I don't know how to do it anymore anyway with all these partitions like swap). Now, it seems the installer can do the partitioninn for you, but I also read this could destroy your Windows installation. Is this true? How to do this correctly?

3) Updating the OS. Every 6 months, a new version is released. It was recommended to reformat and use a new installation as the updrade often failed. Is this still the case? Won't this give trouble with the dual-boot in some way?

4) Most important, drivers. I would like to use my laptop with all it's functions. So I want to use my graphics card, wireless, sound, touchpad and function keys. When I tried to use Ubuntu in the VM with vmWare, the sound and touchpad didn't work correctly (it was fine in VirtualBox though). Will this be possible? If I google "Dell Studio 15 Ubuntu", I only get a bunch of problems, which scaries me off.

5) Battery. I've heard Ubuntu and batteries aren't a good choice. How will my battery length be compared with Windows 7?

Thank you very much,
Bv202

---

### Post by spydeyrch on 2010-10-11
My biggest recommendation would to use a live CD first to test everything out. Using a live CD or live USB is very different from using a VM to test things.

With the live cd you will be able to see if all your hardware is recognized, works, any perks, etc. One thing I bet is going to happen is that it may not recognize your wireless card. with the live cd booted, connect your machine to the internet via a wired connection. Then go to system -> admin -> hardware. It will scan your hardware to see if it has any proprietary drivers for your hardware. this should help with the wireless issues (if there is one)

Also, another recommendation would be this:

if you have two hdd in your machine, not two partitions but two actual physical hdd, then keep win7 on the one and install ubuntu on the other. This will weed-out any possible issues that you have with doing a dual boot setup. But to be honest, I have installed ubuntu as a dual boot on the same hdd in a second partition many a time with win7 and it has never had any issues for me. but by installing it on a separate hdd, you can save yourself some possible headache down the road. let me know if you want more details about this.

But to reiterate, use the live cd right now to see if you can detect any possible issue prior to installing.

--------------------

To answer your original question:

> 1) Do I have to install the 32-bit or 64-bit version? I heard you can  use the full 4GB RAM on 32-bit with Linux, is that true?You don't have to install one or the other, it really is up to you. I usually go with 64 bit because I like the ability to do heavy computing more efficently with 64 bit. some say you might run into program issue, meaning that a certain program isn't available in 64 bit, but I haven't had that issue yet. If it comes down to it, you can go with the 32 bit, it is stable (the 64 bit is too) and has stood the test of time.

> 2) The dual-booting itself. A few years ago, I had to create all  partitions itself with a nice tutorial (I don't know how to do it  anymore anyway with all these partitions like swap). Now, it seems the  installer can do the partitioninn for you, but I also read this could  destroy your Windows installation. Is this true? How to do this  correctly?well, I mentioned a little about this already. Yes the installer will auto-partition your hdd if you would like it to. It defaults to doing this. If you want more details about setting up a dual-boot system on separate hdd, just ask. :)

> 3) Updating the OS. Every 6 months, a new version is released. It was  recommended to reformat and use a new installation as the updrade often  failed. Is this still the case? Won't this give trouble with the  dual-boot in some way?I always do a fresh install. But seeing as I have been using 10.04 for 6 months and REALLY like it. I won't install 10.10 until probably way later. If you were to do an update from a prior version to a newer one, I would recommend doing a fresh install instead of an upgrade. But that is my opinion.

> 4) Most important, drivers. I would like to use my laptop with all it's  functions. So I want to use my graphics card, wireless, sound, touchpad  and function keys. When I tried to use Ubuntu in the VM with vmWare, the  sound and touchpad didn't work correctly (it was fine in VirtualBox  though). Will this be possible? If I google "Dell Studio 15 Ubuntu", I  only get a bunch of problems, which scaries me off.that is why using a live cd/usb is important. It allows you to test out your system before committing it. 

> 5) Battery. I've heard Ubuntu and batteries aren't a good choice. How  will my battery length be compared with Windows 7?I cann't really comment on this one, sorry. I don't have a laptop. Anyone else????


-Spydey :KS

---

### Post by Bv202 on 2010-10-11
Hey,

Thank you for the reply.

I only have one HDD, so I will have to do it with partitions. But is it safe to use the Ubuntu installer to create the partitions? I've read it could be dangerous:confused:

I'll have a look at the live CD, thanks. I'm just still not sure whether I should use the 32-bit or 64-bit version.

Thanks

---

### Post by Quackers on 2010-10-11
Are you using XP, Vista or W7?
It is much safer (and quicker with Vista and W7) to shrink your Windows partition by using the Windows Disk Manager. Right-click on the drive and select shrink. It does have limits though, as it will only let you shrink it by about half.

---

### Post by spydeyrch on 2010-10-11
Well, if I were you, I would use the live cd to test out the system and see if it works and meets your expectations. Once you have used the live cd and found it to your liking, then you could try out wubi.

Wubi gives you a dual boot setup but in a much different way. You actually install ubuntu from within windows. It isn't a VM. then when you boot your system, you are given an option of booting win7 or ubuntu. This will allow you to try out ubuntu even more in depth and see what kind of issues you run into. In the end, if it doesn't work for you then you can uninstall it, just like a normal program, from with in windows. Always read a little about wubi and the version you are going to use just to make sure it will work.

If you do like ubuntu via wubi and want to use it "for real", then I would uninstall wubi and install ubuntu the normal way and setup a dual boot.

As far a messing up your win7 system, I haven't run across that problem yet. I have read about others having an issue but am not too familiar with what it was that was the problem.

As far as which to use, 32 or 64, if you really don't know, then go with 32. It will simplify things for you in the sense that now you don't have to choose.   :) 

Hopefully that helps and doesn't hinder.  :guitar:


-Spydey :KS

P.S. to quote from one of the best movies of all time:

"Baby steps Bob, it's all about baby steps...."   :D

---

### Post by spydeyrch on 2010-10-11
> **Quackers said:**
> Are you using XP, Vista or W7?
It is much safer (and quicker with Vista and W7) to shrink your Windows partition by using the Windows Disk Manager. Right-click on the drive and select shrink. It does have limits though, as it will only let you shrink it by about half.


Yes, if you are going to commit a partition to ubuntu on the same hdd, then:

-boot into windows (i believe it is win7, right?)

-defrag your hdd (we want to have as much continuous free space as possible)

-use the built-in win7 partition utility to shrink your hdd to the size you want.

-install ubuntu to the newly created partition.

viola!

-Spydey :KS

---

### Post by Bv202 on 2010-10-11
Hey,

Thank you for the reply. I know what wubi is, but would like to do a real install :)

If I just use the Ubuntu installation and let Ubuntu create the partitions, won't that be fine? So with this:
[img]http://wiki.ubuntu-nl.org/InstallatieDesktopLucid?action=AttachFile&do=get&target=schijfruimtevoorbereiden.png[/img]

You can specify how much space you want for Ubuntu/Windows. Will that work too?

---

### Post by Quackers on 2010-10-11
It might, but it might also wreck your Windows 7 installation. I wouldn't like to take the risk, personally, but the choice is yours.

---

### Post by Bv202 on 2010-10-11
Hey,

Hmmm, doesn't sound good.

This guide is Dutch and outdated, but you'll understand the partition part:
[http://wiki.ubuntu-nl.org/InstallatieDualBoot](http://wiki.ubuntu-nl.org/InstallatieDualBoot)

So, following this guide, you have to:
1) Make the windows partition smaller
2) With the new free space, create 3 partitions:
- Root, about 10gb, ext4, /
- Swap, about 4gb, swap
- Home, rest of the space, ext4, /home

But I can't do that as you can only have 4 primary partitions and I have recovery partitions which I don't want to remove:
(My computer)
[http://img241.imageshack.us/f/partities.png/](http://img241.imageshack.us/f/partities.png/)

According to this tutorial ([https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)), you can use a file as the swap. I was told you can use only 1 partition for home and root, so you only need one partition for the whole OS (which will work, as I can still have one more primary partition).

So this is what I should do:
- Make the Windows partition smaller
- With the new free space, create one new partition:
- Ext4, /, all space

Then select the new ext4 partition to install Ubuntu on. That way it won't reformat the windows partition and Ubuntu will install the GRUB, which will detect Windows.

Is this correct?

---

### Post by spydeyrch on 2010-10-11
@Bv202,

As has been mentioned a few times, use windows built in partition shrink program to shrink your windows partition.

Then with the ubuntu install cd, just select that new partition that you created as the install destination.

Ubuntu will then use just that 2nd partition's space to create the needed partitions (i.e. /, /home, swap, etc). 

This shouldn't ruin your win7 install.

But if you just boot into the live CD and let ubuntu shrink your win7 partition and create a new partition, it may ruin your win7 install.

does that make sense?

-Spydey :KS

---

### Post by Bv202 on 2010-10-11
Hey,

So I should use this tool:
[http://img241.imageshack.us/f/partities.png/](http://img241.imageshack.us/f/partities.png/)

Can I make the partition smaller while working on it?

Also, I already have 3 primary partitions. So what will ubuntu do with it? It can only create one more.

---

### Post by Quackers on 2010-10-11
You are correct about only being able to have 4 primary partitions, but what you can do (and the installer can do too) is create an extended partition which can then hold your necessary Ubuntu partitions within it.
Some would advise a seperate Home partition - some would advise not.

---

### Post by Bv202 on 2010-10-11
So what partitions will the Ubuntu installer create this way? Also a swap one?

---

### Post by Quackers on 2010-10-11
If you don't create a seperate Home partition and install Ubuntu to the largest contiguous space it will create all necessary partitions (including swap).
The image you enclosed is an image of the Windows Disk Management screen, I believe. That is what I would use to shrink your Windows partition.

---

### Post by BigRedButton on 2010-10-11
Actually, batteries and Ubuntu mix very nicely. I have an Acer D250 and my battery lasts about an hour longer on ubuntu than it does on 7.

I also dual boot 7 and 10.04. i chopped the 7 partition down considerably, since I really only use Ubuntu, and I've never run into any "getting along" troubles.

About the driver questions, if you had a positive experience with the VM, everything will work the same on an install. Generally, everything works out of the box, with the exception of the mic needing some tweaking, see [http://ubuntuforums.org/showthread.php?t=1572388](http://ubuntuforums.org/showthread.php?t=1572388) on that issue.  Also you may run into troubles with fingerprint readers and non usb-based multi card readers, but check the hardware compatibility lists on those.

Choosing partitions/size is easy, especially if you only have one OS installed currently. The defaults are to install side by side, and all of the partitions are created automatically. Obviously, there can only be 4 primary partitions, but only the root partition needs to be primary. the rest will just be made as extended partitions. Move the slider left or right until the numbers look how you want them. The default is half for each OS.

Also, Spydey has an excellent suggestion, using the utilities in 7 to shrink your partition first, though if you defrag it shouldn't be an issue.

Grub will detect windows automatically no matter how you cut the cake. It is seriously one of the oldest continuous parts of Ubuntu and its implementation is very refined.  I haven't ever had a problem with GRUB since Dapper.  It will pick up Windows 7 and another boot option it calls Windows Vista, which is the recovery partition (you can rename this if you wish, see the GRUB man pages or look around the forums)

---

### Post by Bv202 on 2010-10-11
Hey,

I did everything as explained here, but it only fails.

With the live CD, as soon as I connect to my wireless the first time, my mouse hangs for a minute or so. I can use keyboard etc., so it's only my mouse.

When I try to start the installation, I only get errors. I can get to the window which tells you need to have a internet connection, 2gb free space, etc., but as soon as I click next, two applications stops working and the installer stays loading.

These programs crash:
Ubiquity
Jockey-text

No extra error messages were given. I've downloaded and burned Ubuntu again, but still getting the same problems.

Is there any way to let the installer really install Ubuntu? I'm using the 64-bit version.

---

### Post by BigRedButton on 2010-10-11
Are you trying to install from the desktop session on the live cd? or directly from the initial menu? If you got the CD from [http://www.ubuntulinux.org/desktop/get-ubuntu/download](http://www.ubuntulinux.org/desktop/get-ubuntu/download) you don't need to connect to the internet in order to install Ubuntu.  If it's giving you too much trouble though, maybe try going the USB stick route (save you CD burning time, and another CD) and use one of the alternate install downloads. They don't have a live boot option, and the installer isn't quite as sexy, but it pretty much never fails.

---

### Post by Bv202 on 2010-10-12
I'm trying to install from the live cd (so with the "try Ubuntu" option). I'll try a few more things as soon as I'm back from school.

---

### Post by Bv202 on 2010-10-12
Hey,

If I just start the installation (without "trying" the OS) it doesn't give any error.

But now I'm at the partition part? How do I let Ubuntu install on the free space? I can select three options:
- Install next to another OS: When I select this, I can decide how much space I want for Windows/Linux. But it doesn't give me an option to use the free space:
- Use entire disk: I don't want to do this...
- Advanced: Brings me to the advanced partitioning system where I don't understand anything...

---

### Post by Mark Phelps on 2010-10-12
The screen shot gives the appearance that you're going to use the Ubuntu installer to shrink the current Win7 installation to make room for Ubuntu.

DO NOT DO THAT!!

You've been told at least 3 times NOT to use the Ubuntu installer to do that!  This is asking for trouble with Win7, and runs the risk of rendering it unbootable.

Also, stuff that does NOT work with the LiveCD can range from trivial to impossible to fix later, especially stuff that fails due to missing drivers.

So, if stuff is not working, your best bet is to then do searches in these forums using the hardware info to see if others have posted on the same problems and have solutions for them.

---

### Post by Bv202 on 2010-10-12
My partition is shrinked already with Windows 7. I now have 50gb free space to install Ubuntu on, but the installer doesn't give me that option.

I can only choose to install on the whole drive, on my recovery partition (with advanced, if I understand correctly, it will install on the orange part, which is my recovery partition) or make my Windows partition smaller while I already did that.

---

### Post by Quackers on 2010-10-12
I think there should be an option to "install on the largest free space" if I remember correctly.

---

### Post by Bv202 on 2010-10-12
The installation failed...

I've filled in everything correctly, but at the end of the installation my screen went black. I've waited like 5-10 minutes, but my computer wasn't reading the cd anymore, so I just resetted the system.

The grub was installed. I wanted to make sure Windows still worked, so I booted up Windows, which went fine. On the next reboot though, the grub didn't load anymore and my computer hung.

I've downloaded the Windows 7 Recovery Tool and fixed the MBR. My Windows installation works fine now, but I assume Ubuntu is corrupted.

Not sure what I'll do now. I don't want to try this again to be honest. Too bad Ubuntu doesn't work as stable as everyone tells me.

Maybe I'll try the next release. Is it possible to remove that Ubuntu partition and allocate the free space back to Windows?

---

### Post by Quackers on 2010-10-12
If you boot from the live cd try selecting "try ubuntu" rather than installing it. If that loads up and everything works then an install should work. I suspect it may not work, possibly due to a graphics problem. I'm not sure whether the ATI 5xxx cards are fully supported, but trying Ubuntu off the cd will give us a clue.

---

### Post by Bv202 on 2010-10-12
> **Quackers said:**
> If you boot from the live cd try selecting "try ubuntu" rather than installing it. If that loads up and everything works then an install should work. I suspect it may not work, possibly due to a graphics problem. I'm not sure whether the ATI 5xxx cards are fully supported, but trying Ubuntu off the cd will give us a clue.

The Live CD works fine... at least until I decide to install, which only gives some errors:(

---

### Post by Quackers on 2010-10-12
If you can get as far as the Ubuntu desktop by "trying Ubuntu" then an install should be ok. Have you tried that?
BTW, have you checked the MD5 checksum of the downloaded .iso for 10.10?
Version 10.04 could be another option.

---

### Post by brokenromeo on 2010-10-12
I installed by shrinking the windows 7 partition, then booting from a live usb drive...the default options do not allow for installing on free space, at least not from what I could see...I had to select the advanced disk options...select the unused space and create a / partition and then with the space left from that created a swap partition of appropriate size, then the installation worked. The default installation brings up a slider that allows you to adjust the Windows 7/Ubuntu disk sizes, it does not default to the size of the unused space on disk...this is a little confusing...

---


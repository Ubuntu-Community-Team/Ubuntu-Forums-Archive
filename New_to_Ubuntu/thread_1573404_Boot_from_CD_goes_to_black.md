---
title: "Boot from CD goes to black"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by MatrimFTW on 2010-09-12
As the title says, BIOS boots fine > Boot from CD > CD reads and something loads but the monitor turns off as if its not receiving input. 

Background, I'm trying to reformat from XP due to a corrupt winlogon (Lost the install/repair CD =|) I cannot load windows properly and my friend suggested Unbuntu as a better alternative than something heavy and bloated. 

Can someone suggest how to install Unbuntu to a working state? Many thanks.

Vid card is DVI-D input only. Monitor is old IBM flat unsure of make. Vid card is gforce series

---

### Post by MooPi on 2010-09-12
Can you give us your computer specs ? Another choice for install media is the alternate install CD. It uses less resources.
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download")

---

### Post by MatrimFTW on 2010-09-13
I've tried looking to turn to a regular VGA input from the MB but there isn't any 12 pin connectors.

Specs are Fatality FP-IN9 SLI MB, 2.4 Quad Intel. Not sure what else you need. Sadly can't access much to copy/paste so its off of the top of my head.

My other thought was to hook the HDD up to my "old" comp to format and install drivers/unbuntu but having never done that I'm not sure how successful I'd be.

Any help is greatly welcome as I'm lost atm.

---

### Post by mastablasta on 2010-09-13
there is an adapter (usually comes with the card) to transfer from DVI to VGA. if not you could buy one as they are very very cheap.
 
Though i don't think this is the issue. 
 
somehow someway you probably need to get to command line (which should be available on most if not all graphics cards). from there you can progress forward. Likely you need to somehow enable the propper graphics card.
 
Using alternate install CD you will progress through text mode install i believe. that way at least you could see what is happening.
 
As for the Windows i am not sure what is corrupt but if you can get to command line (press F8 during windows boot) and then type ```
fixmbr
``` that could fix the boot sector. then you could boot in and do a ```
chkdsk /r
```

---

### Post by MatrimFTW on 2010-09-14
Checking in, sadly haven't had a chance to try the alternate CD yet. I can also check to see if I can get to a C prompt since when it attempts to log into windows it restarts and I can get to a boot to safe mode menu even though it won't boot to safe mode.

Which alt-dl offers the text based install? 

By the way, I thank you both for your replies and greatly appreciate the help :)

---

### Post by mastablasta on 2010-09-14
text based install will help you install the system and then you can (hopefully) configure your graphics drivers from the command line to get into propper graphical interface.
 
it would help if you could find out exactly which card you are using i am sure someone here will know the solution for it.

---

### Post by MatrimFTW on 2010-09-15
> **mastablasta said:**
> text based install will help you install the system and then you can (hopefully) configure your graphics drivers from the command line to get into propper graphical interface.
 
it would help if you could find out exactly which card you are using i am sure someone here will know the solution for it.

The vid card is an Nvidia GeForce 8800 GT SE.

Can you also link the text based install guide/download please? I'm having trouble finding one specifically. Thank you you're truly a gentleman(lady) and a scholar.

---

### Post by wilee-nilee on 2010-09-16
The alternative cd is great. You might try the live cd again, as soon as you hit the boot for it hold down the shift key this will get you to a menu to try out Ubuntu or install and other options, instead hit f6 click on nomodeset then boot this may get you in to install. 

If this works, you will reboot to the installed system holding the shift down again when you see the grub menu then hit e for edit, then add nomodset (notice the different spelling) at the end of the kernel hit crtl-x to boot then if you get in you can get the graphics set up on the installed system, if the graphics driver is the problem. 

The advantage of getting the live cd to boot up is to check it out and see if the OS is going to work, before installing.

---

### Post by MatrimFTW on 2010-09-18
Still can't get any display after I tell it to boot to the CD :'(

Am burning the alt-install as we speak. Fingers crossed.

---

### Post by KirbySmith on 2010-09-18
The following works for my two computers (see below) using 9.10.   Because my two video cards' nomeclature "bracket" yours, it may help you.

When booting from the live CD, I accept (Enter) the English language option, and then at the next screen use the F4 key to get to the options.  The important option for nVidia cards is low resolution mode.  Hit enter and then Enter at the higher level menu and the live CD should load itself into RAM and start up correctly.

If I am doing an installation, I install from the loaded live CD with it in low resolution mode.  After I get a functioning installation, I upgrade the video driver using either ubuntu's reminder, or via System/Administration/Hardware Drivers.

kirby

---

### Post by MatrimFTW on 2010-09-19
Ok so, using the alternate CD to text install I installed the unbuntu OS. System restarted as normal, got the GRUB and then the monitor went to searching for input again. I assume that the video card drivers obviously need reinstalling but how do I install them blindly? Is there a way to boot to low resolution or VGA safe mode or something? I can't see one on my GRUB selection. Would it be a better idea to get to a C: prompt and put the current drivers on a cd and try to install them from DOS?

---

### Post by KirbySmith on 2010-09-21
Please reread my message (no. 10).   What I called low resolution mode is actually called "Safe Graphics."   This will install Ubuntu so that it doesn't need special video drivers (at least for nVidia cards in my experience).

After Ubuntu is installed, then the correct driver can be installed using the System/Administration/Hardware Drivers path from the top bar menus.

As far as I know, DOS drivers will not work and will not install.

There are answers on this forum for interrupting grub so that certain modes can be set at boot time that probably do what you want, but I'm not experienced with them.

kirby

---

### Post by MatrimFTW on 2010-09-26
Reinstalled, checked CD, used a lower res monitor and now I get an error in GRUB after using the Alt-install CD

Gave up Waiting for Root Device. COmmon Problems
-Boot args (cat /proc/cmdline_
    -Check rootdelay=
    -check root=
-Missing Modules (cat /proc/modules; ls /dev)

ALERT! /dev/disk/by-uuid/1b69f615-fd51-48f8-8b7f-5f1d93511478 does not exist. Dropping to a shell!

I'm not sure if its because I put it on/created another partition only for unbuntu to boot from or whats going on.

Sadly I only have about 3 hours a week to mess with this issue or I swear I'd be done by now

---

### Post by KirbySmith on 2010-09-27
Your boot process seems to be looking for a UUID that doesn't match the  partition you are trying to boot to.   If so, and if you look at the message link  below, and ignore that the topic of that thread is quasi-cloning a drive,  you will find two actions that you may need to take.  One is modifying  fstab, and the other is fixing grub.

[http://ubuntuforums.org/showpost.php?p=9866374&postcount=15](http://ubuntuforums.org/showpost.php?p=9866374&postcount=15)

fstab has to be modified so that the UUID is the correct one for the partition you want to boot to, and grub has to be re-installed so it points at that partition.  Note that these actions are performed from a functioning live CD instance of ubuntu, not the one that is on the hard drive and broken.  However, it is the fstab and grub of the latter that is to be modified.

Please note that this is about the limit of my knowledge of the subject, and that I have no experience with the alternative CD.

There is a command blkid-something that can provide actual UUIDs, but they could be determined with the live CD using system/administration/gparted by right clicking on a dispalyed partition and choosing information.  Be very careful when in gparted.   Gparted will also allow you to see what partitions of what type you now have on the drive.

It is unclear to me whether you are trying to save stuff already on the drive or have the freedom to reformat it and re-install cleanly.  Clean installs should be easier to work with.  In my initial learning several months ago, I worked with fresh drives and then added older drives with useful information later, or copied info from older drives using USB connections from USB drive caddies.

kirby

---

### Post by MatrimFTW on 2010-09-28
Well, the original issue has been solved. As far as the drive goes at this point I just want it fixed and am willing to reformat it to install whatever.

I'm not using the alternate CD at this point, I'm using the regular install. Thank you for linking the other topic, I'm hoping it works as I'm really tired of messing with it, haha. :)

---

### Post by MatrimFTW on 2010-10-02
> **MatrimFTW said:**
> Well, the original issue has been solved. As far as the drive goes at this point I just want it fixed and am willing to reformat it to install whatever.

I'm not using the alternate CD at this point, I'm using the regular install. Thank you for linking the other topic, I'm hoping it works as I'm really tired of messing with it, haha. :)


Solved, old monitor is old and wasn't reading the VGA output from the card.

---


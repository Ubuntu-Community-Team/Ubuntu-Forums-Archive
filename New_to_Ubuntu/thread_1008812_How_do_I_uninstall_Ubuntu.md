---
title: "How do I uninstall Ubuntu?"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by Ben321 on 2008-12-11
I've got copy of Ubuntu 8.10 installed on my computer and is being used as a dual boot (Windows XP is on the first partition, Ubuntu is on the second partition). I've decided to remove Ubuntu to give myself more space on the drive. However I can't figure out how to completely uninstall Ubuntu. I have managed to delete the partition that Ubuntu is on by using "Disk Management" from Windows XP. But then when I boot up it give me an an error about not finding GRUB (the menu used to select which OS I want to boot from), and refuses to boot, even to Windows XP. So to make my computer bootable I had to reinstall Ubuntu (and therefore GRUB).

So now I'm looking for the correct way to uninstall Ubuntu. I tried booting back from the Ubuntu install CD to see if it had an uninstall option, but it doesn't. So now I'm stuck. I'm afraid that to get Ubuntu off, I might have to boot from my Windows XP CD and delete ALL the partitions on my drive, and then start fresh by making a new one, and reinstalling Windows XP, which would be a ROYAL PAIN! Does anybody know how to JUST uninstall Ubuntu (and the associated boot loader GRUB)? Or can I put GRUB on the same partition as Windows XP, so that it will only list Windows XP to boot from, and therefore allow me to delete the Ubuntu partition?

Whatever I have to do, PLEASE someone tell me how to uninstall Ubuntu. I don't want my WHOLE computer, including Windows XP, being "held hostage" by some COMPLETELY UNRELATED operating system which I don't even want anymore.

---

### Post by aheckler on 2008-12-11
You will need to delete the Ubuntu partition, reinstall the Windows bootloader (this is why you couldn't boot to Windows), and then expand the Windows partition to take up the entirety of the drive if you want.

Googling around will tell you how to reinstall the Windows bootloader.

---

### Post by jay576 on 2008-12-11
if you know which partitions are which you can format your ubuntu partition and resize the windows partition using gparted on an ubuntu livecd

---

### Post by Nodnelg on 2008-12-11
> **jay576 said:**
> if you know which partitions are which you can format your ubuntu partition and resize the windows partition using gparted on an ubuntu livecd
Additionally you may also need to completely remove GRUB which can be done using the Super GRUB disk found here ( [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) ).

---

### Post by jay576 on 2008-12-11
> **Nodnelg said:**
> Additionally you may also need to completely remove GRUB which can be done using the Super GRUB disk found here ( [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) ).

thanks for completing that.  I haven't just removed all my linux partitions ever unless i completely reformatted the drive.

---

### Post by Ben321 on 2008-12-11
> **jay576 said:**
> if you know which partitions are which you can format your ubuntu partition and resize the windows partition using gparted on an ubuntu livecd

By "live" CD do you mean one that can boot the OS from the CD disk without installing it to the harddrive? If so, that's the kind of disk I have. But what directory do I find "gparted" on, and how do I run it, and run it correctly?

And does anybody know of just some "Ubuntu uninstall" CD that I can just run and will AUTOMATICALLY remove Ubuntu (and optionally GRUB)?

And is GRUB only capable of working with Linux installations? Or is it also capable of working with NON-Linux OS's such as Beos, MSDos, old Windows (such as Win 3.1), or IBM OS/2?

And is it possible that my computer's default boot loader (access by pressing F8 durring boot up) could be used instead of GRUB when booting a Linux OS? Because a computer should ONLY need one boot loader (not both the default one and also GRUB).

---

### Post by Ong on 2008-12-11
This might give you some help [http://users.bigpond.net.au/hermanzone/p18.htm]("http://users.bigpond.net.au/hermanzone/p18.htm"):popcorn:

---

### Post by Ong on 2008-12-11
gparted is at System>administration>partition editor

---

### Post by caljohnsmith on 2008-12-12
To get rid of Grub as your boot loader, you can install a Windows MBR (Master Boot Record) by booting your Windows Install CD, go to the "recovery console" and run:
```
fixmbr
```
Or if you don't have a Windows Install CD, if you boot your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo lilo -M  /dev/sda mbr
```
That will install a Windows equivalent MBR to drive sda. You can check which is your Windows drive by doing:
```
sudo fdisk -lu
```
And that will list your drive/partitions. Let me know how it goes.

---

### Post by TMOL on 2008-12-12
Hi, I was until recently an Ubuntu user (of sorts), and after attempting to remove Ubuntu from my computer through my Windows partition due to the excessive amount of space it takes up and the error with the loading screen, I got this same problem with the Grub.

My Ubuntu was installed by my stepdad, who I no longer live with, so I cannot reinstall Ubuntu on my computer. This leaves me with the problem of not being able to access my Windows partition either! Is there any way of removing the faulty Grub bootloader without having to access either Ubuntu or Windows?

---

### Post by Duck2006 on 2008-12-12
or

[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

---

### Post by pedro_orange on 2008-12-12
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Ong on 2008-12-12
u could use the super grub disk to restore windows MBR []("http://www.supergrubdisk.org/")

---

### Post by jezebel on 2008-12-13
Hi.

I, just today, uninstalled Ubuntu (getting ready for a computer overhaul and will definitely re-install!).

I followed the instructions from [this archived post  http://ubuntuforums.org/showthread.php?t=113630  ]("http://ubuntuforums.org/showthread.php?t=113630"), and it worked great and was easy for a non-tech person like me. 

Doing this, I didn't have to worry about the windows master boot record or any other crap that's way above my head.
And I did have a complicated set-up - three hard-drives, about ten partitions, and three OS. Yet it was really easy. 

In case you don't want to click, here are the original instructions, posted back in 2006 by Scole:

--------
 How To: Uninstall Ubuntu
Well, not many of you would want to do this but about a week ago I was reading a forum post that had someone ask how do you uninstall Ubuntu? I was left wondering because so few people would want to do it. But, I found an easier way than deleting partitions blindly and rewriting a windows mbr which is no fun at all. To do this you need to be in windows (its an exe) download this file [http://www.terabyteunlimited.com/bootitng.html](http://www.terabyteunlimited.com/bootitng.html) You do not need to buy it. Just scroll to the bottom to download from their link. When downloaded run the exe in there. You then may make a bootable floppy or cd your choice. This puts the program on you choice of media so your ready to go. (the cd option makes a cd .iso so you will need a program to burn it.) Both the floppy and cd contain the same program. Next you will restart your computer with the cd or floppy in the drive. Once you boot into the program do not install it to your HDD. Just click cancel to just run it off the cd or floppy. Then go to partion work. Click the oval on the left side of the window (yes you can use your mouse!) to go to your primary hdd. Select and delete every partition except for your standard windows partition. Now you should have a formatless partion that says free space after it. Then select your windows partion and click resize. It will run an error check which may take a while depending on your partion size. Once that finishes type in the largest size in the prompt unless you have other plans for some of that space . Once you do that it will allocate all that space back to your primary partion. Next, if you installed grub the bootloader you will need to reset you mbr or else you can't boot up because grub will crash. To do this select you windows partion go to view mbr on the left. When in there select your windows partion and click std mbr. This will take grub off and set your mbr back to the way it was before. Click apply and the changes will be made. Then eject your media and use the file option at the top left to reboot. Your computer should restart normally into windows . You just uninstalled Ubuntu. This saved you so much pain. You would have had to rewrite the mbr by hand to do this the other way and then have had to figure out a way to delete the linux partions. It is not a bad idea to back your stuff up before doing this because stuff happens and you don;t wanna lose everything. Hope this helps you.
__________________

---

### Post by TMOL on 2008-12-13
I don't have Live CD's or Windows XP Cd's or anything like that, I can't even access OS selecting because the Grub attempts to boot up first, no matter what I change in the BIOS boot order.

I really need some way of doing this manually with no CD, purely through the BIOS. Someone help?

---

### Post by chavy85 on 2008-12-14
all changing the bios setting will boot from different drives. such as sda sdb. if you don't have a cd you need one. fallow those links and fallow those instructions. or reinstall ubuntu and forget the spyware they call windows. that gives them windows into your computer. LOl

[http://flagstaff.craigslist.org/forums/?act=Q&ID=91638010](http://flagstaff.craigslist.org/forums/?act=Q&ID=91638010)  (1)
[http://flagstaff.craigslist.org/forums/?act=Q&ID=91638019](http://flagstaff.craigslist.org/forums/?act=Q&ID=91638019)  (2)
[http://flagstaff.craigslist.org/forums/?act=Q&ID=91638034](http://flagstaff.craigslist.org/forums/?act=Q&ID=91638034)  (3)
[http://flagstaff.craigslist.org/forums/?act=Q&ID=91638041](http://flagstaff.craigslist.org/forums/?act=Q&ID=91638041)  (4)
[http://flagstaff.craigslist.org/forums/?act=Q&ID=91638044](http://flagstaff.craigslist.org/forums/?act=Q&ID=91638044)  (5)
[http://flagstaff.craigslist.org/forums/?act=Q&ID=91638048](http://flagstaff.craigslist.org/forums/?act=Q&ID=91638048)  (6)

well worth reading.

or go here.
[http://flagstaff.craigslist.org/forums/?forumID=1991&all=N](http://flagstaff.craigslist.org/forums/?forumID=1991&all=N)

good luck.

---

### Post by uwave on 2008-12-16
Bootitng worked for me just as you described....Thanks jezebel
I had to start over to get rid of 8.10 the easy way
and start again with 8.04.

uwave

---

### Post by JoshuaRL on 2008-12-16
> **Ben321 said:**
> And does anybody know of just some "Ubuntu uninstall" CD that I can just run and will AUTOMATICALLY remove Ubuntu (and optionally GRUB)?

And is GRUB only capable of working with Linux installations? Or is it also capable of working with NON-Linux OS's such as Beos, MSDos, old Windows (such as Win 3.1), or IBM OS/2?

And is it possible that my computer's default boot loader (access by pressing F8 durring boot up) could be used instead of GRUB when booting a Linux OS? Because a computer should ONLY need one boot loader (not both the default one and also GRUB).

No Uninstall Ubuntu CD that I know of.  And yes, GRUB will work on non-Linux OS's.  GRUB stands for GRand Unified Bootloader after all.  What you're talking about is the BIOS screen that lets you choose which HARDWARE you want to boot from.  Then that hardware is expected to have it's own SOFTWARE bootloader.  For Windows it's MBR, and there's others including lilo, GRUB, and DASBoot.

> **TMOL said:**
> I don't have Live CD's or Windows XP Cd's or anything like that, I can't even access OS selecting because the Grub attempts to boot up first, no matter what I change in the BIOS boot order.

I really need some way of doing this manually with no CD, purely through the BIOS. Someone help?

USB drive with SuperGRUB or a Linux distro on it mayhaps?  Sorry dude, no way to alter MBR from BIOS.

---


---
title: "Grub Loading Stage 1.5 = error 1.5"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by damien_flanders on 2009-11-12
I am trying to install Ubuntu 8.10 on my destop computer. It already has Windows
XP on it. I installed it on my HP Laptop and had NO PROBLEMS whatsoever.

The error I get after installation is and the boot screen is:

[B]GRUB loading stage 1.5

GRUB loading please wait

ERROR 21[/B]

then the computer stops and it just sits there. I can hit CTRL ALT DEL or something
and it will reboot and then do the same thing all over again.

I cannot even get to the point where I can do a dual boot and choose XP, so I am 
stuck with this error screen.

---

### Post by philinux on 2009-11-12
Try this from the live cd.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by damien_flanders on 2009-11-13
I tried using the Ubuntu Live CD. 

this does me no good, as I can not get to the DESKTOP. I am still
getting the same error.

I tried the option "try ubuntu without any change to your computer" and that failed 
as well. I tried Boot from hard disk and that gave me the same "error 1.5"

---

### Post by egalvan on 2009-11-13
> **damien_flanders said:**
> I tried** using the Ubuntu Live CD**. 

this does me no good, as I can not get to the DESKTOP. I am [B]still
getting the same error.[/B]

I tried the option "try ubuntu without any change to your computer" and that failed 
as well. I tried Boot from hard disk and that gave me the same "error 1.5"

You cannot get a grub hard drive error from a LiveCD because the LiveCd does NOT touch the hard drive, except to attempt reading/mounting partitions, and this happens AFTER grub.
And errors found at this stage on the LiveCD are not reported, the partitions are simply not mounted.

---

### Post by damien_flanders on 2009-11-13
Ok. i'm not sure what you mean by, "LIVE CD." I put in the Ubuntu CD that I got free via mail.
What do I do after I turn the computer on and boot from the CDROM drive? Is there an option that I need 
to choose from on the main menu?

Do I choose something from the options for the Function keys on the bottom of the screen?

I am completely new a this LINUX stuff, don't know what a "GRUB" is other than something 
found in good topsoil, etc.

All I know is that now I can't use my desktop computer!

---

### Post by damien_flanders on 2009-11-13
> **philinux said:**
> Try this from the live cd.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

The first line from this thread say to:

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

**When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)**

How do I get to the DESKTOP?? I just have a black screen that says:
[B]
GRUB Loading Stage 1.5 = error 1.5[/B]

---

### Post by ranch hand on 2009-11-13
When you boot from the cdrom and the menu for the Live CD comes up, the first option is "try Ubuntu with no changes to your computer".  This is what you want.  This will take you to a fully functional Desktop environment, albiet a bit slow, that you can do all kinds of neat things from.

Slow down and remember to breath.  Your panicie posts do not indicate that you are in the right frame of mind to correct a problem.  Calm down and think slowly.  Follow directions carefully.

---

### Post by kansasnoob on 2009-11-13
This may actually be one of the reasons grub2 was released when it was.

What they're saying about booting the Live CD is, just when you're stalled at the boot error or just before, try opening the CD tray so you can put the Live CD back in.

Then hit Ctrl > Alt > Del again. When you boot back up you should be able to try reinstalling grub as explained above.

If that fails I think you'll need to mount, chroot and then install grub-pc (aka: grub2). I checked and it is in the Intrepid repos.

More about mount & chroot here:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

About changing to grub2 in Appendix #2 here:

[http://ubuntuforums.org/showthread.php?p=8312563#post8312563](http://ubuntuforums.org/showthread.php?p=8312563#post8312563)

---

### Post by oldfred on 2009-11-14
To boot from the CD you need to select that as the BIOS is configuring the system. On my portable it is f2 and on my desktop  it is f12 to choose drive to boot from. You should see the choice of what key to push as it starts to boot. 
Some older computers do not have a choice as you boot and you have to go into the BIOS and change the boot order from HD first to CD first. The key to get into the BIOS is also a choice that should be shown as it starts to boot, often it is the delete key, but may be something else.

---

### Post by damien_flanders on 2009-12-01
I haven't tried fooling with correcting this for a while. Today I decided to follow the instructions and see if I could get this thing up and running.

I booted the computer from the Ubuntu Live CD and then chose the option to 
run "try Ubuntu with no changes to your computer". I was able to do so this
time, but after some wait I just go an error screen full of messages:

[IMG]http://i167.photobucket.com/albums/u122/heavyjavadrinker/internet/ubuntuerror005.jpg[/IMG]
[IMG]http://i167.photobucket.com/albums/u122/heavyjavadrinker/internet/ubuntuerror006.jpg[/IMG]

I'm not sure what any of this means. Does this have to do with bad sectors on the HDD?
I'm pretty certain that it defaulted to installing Ubuntu onto my slave Hard Drive. I have taken the slave hard drive out so that i can see if i can delete the partition with Ubuntu off the drive.

There is still a problem however and that is that I can no longer boot into Windows XP from the Master Drive. It goes only as far as the ASUS Bios Screen. I was able to get into the Bios and change the boot order to floppy>HDD>CDRom, but that was about it. It will not boot into XP and this is probably due to the failed Ubuntu installation.

Unsure of what to do next.

---

### Post by Miljet on 2009-12-01
The reason that you can no longer boot into XP is that when you installed Ubuntu it over wrote the MBR (Master Boot Record) on your hard drive. That is just a fancy name for the first sector of the hard drive. It is a very small sector and basically all it does it point to the real boot loader program. It is now pointing to your Ubuntu install, but can not find it. That is the reason for the error message.

> I was able to get into the Bios and change the boot order to floppy>HDD>CDRom
You need to change this back so that CDRom is before HDD so you can boot the live CD. BTW, the live CD is the same disk you used to install from. You just select "Try Ubuntu without changing your computer." If you cannot boot into the live CD, it is because of one of three problems.
1- You don't have the BIOS set to boot the CDRom before the HDD.
2- You have a bad CD. Check by trying it in a different computer.
3- You CD drive is bad and introducing errors while reading the disk.

See if you can get to the point of running the live CD and post back and we will go from there.

---

### Post by oldfred on 2009-12-02
Error messages on sr1 are reading errors on the CD. You do not have a good CD is what it is saying. 

Try burning it at the slowest speed you can and then run the check CD on the CD.

---

### Post by presence1960 on 2009-12-02
> **oldfred said:**
> Error messages on sr1 are reading errors on the CD. You do not have a good CD is what it is saying. 

Try burning it at the slowest speed you can and then run the check CD on the CD.

+1

here is some info for you: [https://help.ubuntu.com/9.10/switching/installing.html](https://help.ubuntu.com/9.10/switching/installing.html)

---

### Post by damien_flanders on 2009-12-02
> You need to change this back so that CDRom is before HDD so you can boot the live CD. BTW, the live CD is the same disk you used to install from. You just select "Try Ubuntu without changing your computer." If you cannot boot into the live CD, it is because of one of three problems.
1- You don't have the BIOS set to boot the CDRom before the HDD.
2- You have a bad CD. Check by trying it in a different computer.
3- You CD drive is bad and introducing errors while reading the disk.

1. - I can change the boot order back to CDRom>HDD>Floppy
2. The CD is fine, I used it to install on my new HP Pavilion dv5 and Ubuntu works normally. I used the Ubuntu 8.10 desktop edition that I ordered from Ubuntu.
3. This could be the problem. I may have had problems with this drive in the past. I first tried installing with my DVD and that failed. Then I tried installing with the CDROM drive in this is the problem I am having.

I will have to put the Slave HDD back in the computer and try using another CDROM.

btw, i get the error message before removing the slave HDD.

---

### Post by damien_flanders on 2009-12-02
Okay, I managed to get a little further with this:

I put in another CDRom Drive and booted the computer. I was able to boot
into the Ubuntu Live Disc successfully with no problems. 

From there I chose, **"try Ubuntu with no changes to your computer" **and 
when that was clicked on, I got the following:

a pop up square with a title of "BOOT LOADER," and beneath that it reads,

**/caspop/vmlinux**

and then nothing happens. then suddenly it went to a black
screen that just said:

**/BOOT**

like it was in a DOS type mode. I tried tying in some of the lines to fix the 
Error 21 message and nothing worked.

---

### Post by Miljet on 2009-12-02
> btw, i get the error message before removing the slave HDD.
That's because during your install the part of GRUB that was installed to the MBR of your hard drive is pointing to the wrong place. It is easy to fix, but you need to be able to boot the live CD in order to fix it. One of the earlier replies gave a link to an excellent tutorial on how to fix this.

You can try cleaning the lens on the CD drive, but I have found that it is better to just replace them. They are pretty much dirt cheap now-a-days.

Just for information, GRUB stands for GRand Unified Boot loader. It is installed in the /boot/grub subdirectory. And as mention before, a pointer is installed in the MBR of the drive that points to that subdirectory.

---

### Post by Miljet on 2009-12-02
You have NOT successfully booted into the live CD until you have selected "Try Ubuntu without changing your computer, the operating system fully loads, and you get to a desktop. However, the fact that you are getting the menu indicates that you have the boot selection set correctly.

The errors that you are getting still indicate a bad CD (which I doubt) or a bad drive. Since you have changed the CD drive, it is remotely possible that you have a bad connection or bad cable that connects the drive. If you can try the disk in another computer and boot the live CD completely to the desktop, that would verify that the disk is good.

---

### Post by damien_flanders on 2009-12-02
> You have NOT successfully booted into the live CD until you have selected "Try Ubuntu without changing your computer, the operating system fully loads, and you get to a desktop. However, the fact that you are getting the menu indicates that you have the boot selection set correctly.Okay. So I have tried several things mentioned above.

The first thing I did was boot up the computer with Ubuntu CD in and with the CDROM first in the boot order. I then tried all the main options.

I clicked on "check for defects" on got this result:

[IMG]http://i167.photobucket.com/albums/u122/heavyjavadrinker/internet/ubuntuerror008.jpg[/IMG]

nothing happened other than that pop-up.

The I tried "test memory" and got this:

[IMG]http://i167.photobucket.com/albums/u122/heavyjavadrinker/internet/ubuntuerror007.jpg[/IMG]

All errors. It looked like it was going to go on forever, so I stopped it and rebooted and tried again with the same results. 

I then tried putting the UBUNTU LIVE CD into my laptop and do the  "try Ubuntu with no changes to your computer" and after all grinding away on the hard-drive or cd-rom i finally got to the desktop:

[IMG]http://i167.photobucket.com/albums/u122/heavyjavadrinker/internet/ubuntuerror011.jpg[/IMG]

As you can see, at the same time I booted my desktop PC with no Ubuntu disc in the drive and naturally I go the ... you guessed it... ERROR 21!

Finally for good measure, here is the screen I get if I try and
do the "try Ubuntu with no changes to your computer" on my desktop I get the old

[IMG]http://i167.photobucket.com/albums/u122/heavyjavadrinker/internet/ubuntuerror013.jpg[/IMG]

/caspep/vmlinux


what on earth do i try now!???

---

### Post by IsolatedSheep on 2009-12-02
Weird, in my LiveCD for both 9.04 and 9.10, its /casper/ not /caspep/. Maybe you should check whether the directory do exist in the installation cd.

And if your computer could boot from flash drive, maybe you should try USB installation instead.

---

### Post by damien_flanders on 2009-12-02
I have used the disk to install to my laptop which has Vista. It works fine.

It's only my desktop which runs XP that I am having all the problems with.

---

### Post by theozzlives on 2009-12-02
I'm thinkin bad RAM, because of your errors during memtest. You could just have a stick of RAM not seated properly, try taking it out and putting it back in.

---

### Post by damien_flanders on 2009-12-05
> I'm thinkin bad RAM, because of your errors during memtest.Okay, this morning I took your advice and looked around inside my computer case (which is a chore because it's a mess of IDE cables and Power cables etc...) and I believe the Ram in slot one was not seated correctly. 

I restarted the computer with the Ubuntu CD-rom inside and was able to boot to the desktop using **"try Ubuntu with no changes to your computer" **which is a HUGE step forward for me! But, after hitting restart and Ubuntu asking to eject the disc, I took the disc out and got the following error when I restarted:

ERROR 18.

One other thing, and I don't know if it's a problem or not... the BIOS isn't automatically detecting the SLAVE drive and so I had to go in an manually find it. 

It's an ASUS A7N8X-E deluxe motherboard.

---

### Post by damien_flanders on 2009-12-05
[B]Okay So Now I am able to get to the Desktop Environment in Ubuntu and open a terminal.

I did the following tutorial step by step and here are my results:
[/B]
When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

 	Code:
 	sudo grub 
This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

 	Code:
 	find /boot/grub/stage1 
This will return a location.

[U][B]I did this and was returned the results of hd1,4
[/B][/U]
 If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

 	Code:
 	root (hd?,?) 
[B]Okay so here I tried:

root (hd1,4)
root (hd1)

I mean, I don't know what to choose![/B]


Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

 	Code:
 	setup (hd0) 
[B]so here I entered as it says above:

setup (hd0)[/B]

Finally exit the grub shell
 	Code:
 	quit 
That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.

**I am still now getting ERROR 18**

---

### Post by oldfred on 2009-12-05
For old grub error's I like Herman's pages for explanations and solutions.
Error 18 is related to old BIOS that could not boot larger hard drives, but Herman has several other things to try.

[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

---

### Post by damien_flanders on 2009-12-05
OKAY OKAY GOOD DAY!!!

I am actually using the computer now. I changed in the BIOS how the computer was
seeing the slave drive from "manual" to "auto" and that made all the difference.

I saw some reference in the article on ERROR 18 that OLD FRED left a a link to and that had me go in the BIOS to change it and that takes care of that!

Thanks for all the help in here! I was getting to the point that i just wanted to either to smash the computer into pieces or take the hdd out.

Last somewhat related question, i was going to try and use EasyBCD 1.7.2 and it looks like you have to have VISTA in order to do this for the fact that it is looking for the VISTA bootloader. Is there a similar program for xp or is this just an unnecessary program in the 1st place?

---

### Post by oldfred on 2009-12-05
Grub can boot you into WinXP. Some want to keep the windows boot loader and use that to boot. Windows will not boot Ubuntu but I believe some of the other windows boot loader can be configured to do that, but to me grub just works.

Grub should find your windows and add an entry to the menu to boot from. If not we can help sort it out.

---


---
title: "4 serious problems"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by BobWest on 2011-01-16
1.  When I first tried to install Ubuntu 10.10 on my new HP dv7-4197cl, selected "Install alongside other operating system."  I followed the instructions.  When it said to restart, I clicked restart; the computer never shut down. "Control alt delete" did nothing.  I powered down the computer by holding down the power button.  After that , it started once in windows without the desktop icons.  I restored to a prior time to fix that.  When I attempted to reboot, the computer never would boot again.  I reformated using the recovery DVDs.
 
2.  I then ibstalled Ubuntu 10.10 by carefully following the instructions in     [http://www.linuxbsdos.com/2010/12/01/how-to-dual-boot-linux-mint-10-or-ubuntu-10-10-and-windows-7-on-a-computer-with-two-hard-drives/](http://www.linuxbsdos.com/2010/12/01/how-to-dual-boot-linux-mint-10-or-ubuntu-10-10-and-windows-7-on-a-computer-with-two-hard-drives/)      Everything seemed to be okay except, again the computer did not shut down at the end when it said to restart.   I waited 3 hours and again held down the power button.  It seemed to start and run okay after that.
 
3.  Now when I tried to register for help in windows live, the computer would not accept several key strokes for passwords, and the site kept timing out.  I had the same problems trying to register for launch pad and Ubuntu forums.  I had to use another computer to make this post. 
 
4.  I feel I was mis-informed where the Ununtu web site said Ubuntu was perfectly safe.  
 
My one question is what can be done about all this?

---

### Post by kittkatt on 2011-01-16
If you have important data on your laptop, you can get access to it [by running Ubuntu in "Live" mode ]("https://help.ubuntu.com/community/BootFromCD") and then transferring it off using a USB stick.  You should do this first.  

In theory, setting up a dual boot using Ubuntu should have no problems, but in practice, often Murphy's Law strikes.  

Your problems registering in the Ubuntu forums wouldn't have anything to do with your installation though since your forum account is not tied to your computer in any way.  I hope that you can find the solutions in the forums for figuring this out (I don't have Win7 or your laptop model, sorry!).

---

### Post by Paqman on 2011-01-16
> **BobWest said:**
> 
3.  Now when I tried to register for help in windows live, the computer would not accept several key strokes for passwords, and the site kept timing out.  I had the same problems trying to register for launch pad and Ubuntu forums.  I had to use another computer to make this post. 


That's very odd. What browser are you using? Firefox? Have you tried it in another browser?

---

### Post by lbarnes on 2011-01-16
I would download another copy of Ubuntu and run it as a live cd to make sure everything runs properly and see what proprietary drivers are available.

---

### Post by Jetro on 2011-01-16
1. I've had a bunch of problems through the years trying to install Ubuntu. It is certainly not every time it works flawlessly.

Some installations have just halted like yours without no real reason for it. Also, you should be sure  to shut down Windows properly etc. before you try installing Ubuntu, but I expect you have done that.

2. I would have tried (unless you want to butch Ubuntu entirely) 10.04 in stead, or 10.10 from another source. (I once had to use an unofficial Ubuntu boot USB, the official one hanged during the installation).

4. I truly get that. There are tons of bugs connected with Ubuntu, so you will most likely have lots of tweaking to do, even if you get it installed properly.

Bottom line, take backup of all your important files before you do anything, and try another boot-CD/USB, and/or another version. It's not often very logical why these things happen.

Hope this helps, if not, sorry.

---

### Post by The Cog on 2011-01-16
1/2:
I have seen a bug in a recent version of the installer where it doesn't shut down or restart at the end of the install, several times. Just powering off or pressing a reset button doesn't seem to hurt, but doesn't inspire confidence either. Actually, I think it outputs a "Press enter to reboot" message that gets lost somewhere, either scrolled off the top by other messages, or perhaps on a different tty console.

3:
Were you trying to register for windows live in Linux or windows?
If Linux: Maybe MS doesn't like accepting logins from Linux boxes?
If Windows: Try completely powering off when changing between OS's. Sometimes an OS can leave hardware in a state that the other OS doesn't expect and can't correct.

---

### Post by nick_goodfate on 2011-01-16
if you try again to install ubuntu, after you press restart at the end of installation try to remove the cd and then press enter.

---

### Post by nick_goodfate on 2011-01-16
if you try again to install ubuntu, after you press restart at the end of installation try to remove the cd and then press enter.

---

### Post by BobWest on 2011-01-17
[FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]1.  When I first tried to install Ubuntu 10.10 on my new HP dv7-4197cl, selected "Install alongside other operating system."  I followed the instructions.  When it said to restart, I clicked restart; the computer never shut down. "Control alt delete" did nothing.  I powered down the computer by holding down the power button.  After that , it started once in windows without the desktop icons.  I restored to a prior time to fix that.  When I attempted to reboot, the computer never would boot again.  I reformated using the recovery DVDs.[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana] [/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]2.  I then ibstalled Ubuntu 10.10 by carefully following the instructions in     [http://www.linuxbsdos.com/2010/12/01/how-to-dual-boot-linux-mint-10-or-ubuntu-10-10-and-windows-7-on-a-computer-with-two-hard-drives/](http://www.linuxbsdos.com/2010/12/01/how-to-dual-boot-linux-mint-10-or-ubuntu-10-10-and-windows-7-on-a-computer-with-two-hard-drives/)      Everything seemed to be okay except, again the computer did not shut down at the end when it said to restart.   I waited 3 hours and again held down the power button.  It seemed to start and run okay after that.[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana] [/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]3.  Now when I tried to register for help in windows live, the computer would not accept several key strokes for passwords, and the site kept timing out.  I had the same problems trying to register for launch pad and Ubuntu forums.  I had to use another computer to make this post. [/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana] [/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]4.  When I tried to connect wirelessly, I carefully followed the instructions in the [/FONT][/COLOR][/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]Ubuntu[/FONT][/COLOR][/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana] [/FONT][/COLOR][/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]Help[/FONT][/COLOR][/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana] [/FONT][/COLOR][/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]Center[/FONT][/COLOR][/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana].  I went to step 3, but there was nothing to click.  I went to troubloe shooting, which said to click Network Manager in notification area.  There was no notification manager in the notification area.  5.2.3 said to install Windows Wireless Drivers.  I installed the ndisgtk package; the site said installed.  System-[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]administration-Windows Wireless Drivers did not have any drivers to select.  The computer became very slow and stopped responding.  After several tries, I was finally able to power down with the power icon in the notifification area.[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana] [/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]5.  I feel I was mis-informed where the Ununtu web site said Ubuntu was perfectly safe.  [/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana] [/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]My one question is what can be done about all this? [/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Comic Sans MS][SIZE=2][COLOR=blue][COLOR=blue][FONT=Comic Sans MS] [/FONT][/COLOR][/COLOR][/SIZE][/FONT]

---

### Post by Bucky Ball on 2011-01-17
If you still have Windows on the system, reinstall Ubuntu 10.04 LTS. That is perfectly safe. Also, no operating system is 'perfectly safe' when it comes to installing. Mistakes are easily made.

10.10 has known issues at the moment. The LTS releases are always safest for newcomers. When you get to partitioning section when installing 10.04 go for manual partitioning and leave the Windows (NTFS) partitions alone and install over the 10.10 install. Three partitions are best:

/ = the OS, 20Gb plenty
/home = your data and settings (big as you like)
/swap = 2Gb, 4Gb if you intend to hibernate

You will probably need to make an extended partition to put these in as four *primary* partitions are the maximum for a single physical disk but if one of these is an extended partition, the sky's the limit as to how many *logical* partitions you can put inside it. 

;)

---

### Post by LewRockwellFAN on 2011-01-17
If it were me, if you have Windows installation disk, I'd do the following:

Back up any important unbacked data. Then repartition with the Windows installation disk making a partition to install Windows on first. Depending on which Windows it is I think it will actually make 2 partitions, one of which will be very small (I'm not sure it is strictly called a partition, but that is essentially correct). How big to make it depends on a lot of things you haven't mentioned. Then make a second partition for Ubuntu. 15 giB should be sufficient. You can always resize these later if you have to. Presumably you'll want to use the rest of the drive for common data partition(s) and for swap partitions if you don't have much memory. Be sure to ***_format_*** these partitions. Then finish installing Windows. Then install Ubuntu on it's own partition(s), _***not***_ "alongside" Windows. Putting multiple OSs on one partition is asking for trouble. There are lots of threads here on multibooting where you will find discussions of the merits of separate home partitions, whether to use a swap partition, how big to make it and whether to try to share it with Windows. Use the search function to find them. Even if you do nothing fancy they will give you a clearer understanding. I'd just put put all of Ubuntu, including home, on one partition. If you have 2 giB or more of memory I wouldn't use a swap at all.

If you _***don't***_ have an installation disk, that's harder. Think about it and hope someone else brighter than I will comment before you do anything. But HP probably shipped the darn thing (ok, I'm officially an HP hater) with a hidden partition containing a backup of the original installation and some sort of utility to restore this backup, putting you back to square one, maybe. If you can do that, and Windows works like it should at that point, I'd back it up with Clonezilla and then resize the Windows partition with a Ubuntu live disk, then make a partition for Ubuntu. Then install Ubuntu on that partition like in the first paragraph.

Installing Ubuntu in its own partition is reasonably safe. I don't think anybody recommends installing a second OS "alongside" the first one on the same partition unless you just like to tinker with weird configurations.

Good luck. And always back up data.

P.S.: I see Bucky was typing at the same time I was and typing faster, no doubt. He probably qualifies as "someone else brighter than I".

---

### Post by Bucky Ball on 2011-01-17
You don't need to make a partition(s) for Ubuntu during Windows install as it will be over-written to EXT when you install Ubuntu anyhow (Windows won't make this file type). Install Windows and leave the rest as free space and create the partitions when you are installing Ubuntu.

---

### Post by Old_Grey_Wolf on 2011-01-17
> **BobWest said:**
> 1.  When I first tried to install Ubuntu 10.10 on my new HP dv7-4197cl, selected "Install alongside other operating system."  I followed the instructions.  When it said to restart, I clicked restart; the computer never shut down. "Control alt delete" did nothing.  I powered down the computer by holding down the power button.  After that , it started once in windows without the desktop icons.  I restored to a prior time to fix that.  When I attempted to reboot, the computer never would boot again.  I reformated using the recovery DVDs.
Did you check the MD5 sum of the iso you downloaded? Did you burn the CD at the lowest speed your CD burner supports? Did you check the integrity of the CD after you burned it? Have you considered using a USD instead of a CD?

> 2.  I then ibstalled Ubuntu 10.10 by carefully following the instructions in     [http://www.linuxbsdos.com/2010/12/01/how-to-dual-boot-linux-mint-10-or-ubuntu-10-10-and-windows-7-on-a-computer-with-two-hard-drives/](http://www.linuxbsdos.com/2010/12/01/how-to-dual-boot-linux-mint-10-or-ubuntu-10-10-and-windows-7-on-a-computer-with-two-hard-drives/)      Everything seemed to be okay except, again the computer did not shut down at the end when it said to restart.   I waited 3 hours and again held down the power button.  It seemed to start and run okay after that.

See response to #1 above. Also, I'm not familiar with the site linuxbsdos.com you got the instructions from. I would stay with Ubuntu websites; such as, ubuntu.com, ubuntuforums.org.

> 3.  Now when I tried to register for help in windows live, the computer would not accept several key strokes for passwords, and the site kept timing out.  I had the same problems trying to register for launch pad and Ubuntu forums.  I had to use another computer to make this post.

Were you trying to register from the MS Windows or Ubuntu OS? If it was MS Windows, you may have something wrong from when you "I reformated [sic] using the recovery DVDs." in #1 above. If it is from the Ubuntu OS, you may have a bad install so who knows what is working.

> 4.  When I tried to connect wirelessly, I carefully followed the instructions in the UbuntuHelpCenter. I went to step 3, but there was nothing to click. I went to troubloe shooting, which said to click Network Manager in notification area. There was no notification manager in the notification area. 5.2.3 said to install Windows Wireless Drivers. I installed the ndisgtk package; the site said installed. System-
administration-Windows Wireless Drivers did not have any drivers to select. The computer became very slow and stopped responding. After several tries, I was finally able to power down with the power icon in the notifification area.

You may not have a Network Manager icon; because, you have a bad ISO or CD. See response to #1 above.

The ndisgtk is used to install a wireless driver you have downloaded or a driver on the device's installation CD that came with the device. It does not automatically find one for you. You have to add the driver to Windows Wireless Drivers before you can use them.

Also, read my sig.

---

### Post by overdrank on 2011-01-17
Hi and welcome, threads merged. :)

---


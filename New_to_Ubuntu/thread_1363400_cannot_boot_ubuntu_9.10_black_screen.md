---
title: "cannot boot ubuntu 9.10 black screen"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by xiaohunying on 2009-12-24
I installed ubuntu 9.10 on a Dell dimension 2400 computer. After installing, I restarted my computer and it goes well. But After I shut down my computer and boot it again, it won't boot up and give me a black screen. The last word on the screen is "Grub loading" before black screen. :confused:Does anyone know what's wrong and give me a help? Thanks!

---

### Post by fslezak on 2009-12-24
See this thread...

[http://ubuntuforums.org/showthread.php?t=1363341](http://ubuntuforums.org/showthread.php?t=1363341)

---

### Post by admiralspark on 2009-12-24
sounds like the system is hanging. A few options:
1) did the LiveCD function work okay? Boot again from the LiveCD to make sure it's not a hardware problem.
2) Reinstall Ubuntu, using the LiveCD beforehand to save any valuable data you might have. 

It sounds like a problem with the bootloader GRUB....do you also have another operating system?

---

### Post by xiaohunying on 2009-12-24
> **admiralspark said:**
> sounds like the system is hanging. A few options:
1) did the LiveCD function work okay? Boot again from the LiveCD to make sure it's not a hardware problem.
2) Reinstall Ubuntu, using the LiveCD beforehand to save any valuable data you might have. 

It sounds like a problem with the bootloader GRUB....do you also have another operating system?

I don't think it's a hardware problem. Because if I press ESC while my computer start booting and exit the setup menu without changing anything, it boots very well. 

There is a Ubuntu logo, and "Grub loading" and black screen.

I only have one os on my computer, which is this Ubuntu 9.10.

---

### Post by hotcarl on 2009-12-25
I have the same problem with my parents computer when I installed 9.10.  I would get to the screen where the Ubuntu logo shows up, then everything goes black.  Sometimes I could get to the login screen when I press escape.  But when the computer goes idle and the screen would fade out, it would often not return.  At first I upgraded 9.04 to 9.10, then I tried a fresh 9.10 with the same results.  My solution has been to keep them on 9.04, so any suggestions for a real fix would be great.

---

### Post by xiaohunying on 2009-12-28
Anyone knows?:(

---

### Post by xiaohunying on 2009-12-28
Every time I reboot my computer, it shows on my monitor 
"Input Signal Out of Range
Change setting to 1440X900 - 60Hz"
or sometimes
"Auto adjust in progress
Recommended setting: 1440x900 60Hz"
and then I get to see the login of ubuntu.

but if i shut down my computer and start it by push the power button, there'll be no signal and a black screen. I am frustrated. Anyone can help me?

---

### Post by Astronomer on 2009-12-28
I upgraded from 8.10, and I get a fade-to-black-screen after logging in as a user.  The screen isn't disabled, and the computer isn't locked.  If I press Ctrl-Alt-Del, I get the logout dialog on the black screen, and I can log out normally.

If your symptoms are different, if you did a clean install, of if you're not using KDE, your symptoms may be different and not fixed by what I found.

I discovered the problem to be in the following file:

/home/USERX/.kde/share/config/kdeglobals

In particular, the "widgets" configuration under the "[General]" category was the problem.  Once I deleted that line, the black screen never returned.

There may be more configuration lines in the "[General]" section causing problems, depending on how much you've configured the screen settings before upgrade.  If in doubt, eliminating the entire "[General]" won't hurt.

Hope this helps.

---

### Post by shadetree1 on 2009-12-28
> **xiaohunying said:**
> Every time I reboot my computer, it shows on my monitor 
"Input Signal Out of Range
Change setting to 1440X900 - 60Hz"
or sometimes
"Auto adjust in progress
Recommended setting: 1440x900 60Hz"
and then I get to see the login of ubuntu.

but if i shut down my computer and start it by push the power button, there'll be no signal and a black screen. I am frustrated. Anyone can help me?

There is issues with the Intel chip-set drivers in Karmic with the Dell 2400 MOBO.

I installed a Radeon 5250 card I had and that fixed the video booting issues bypassing Intel video.  But Karmic would freeze minutes to a hour later requiring a hard boot each time.  I couldn't keep It up long enough to update the kernel.  So I went back to 9.04 ext4, and it's stable as a rock.  

There are other threads referring to the 2400 and Karmic.  Perhaps the admins can merge these threads to something like "** Dell Dimension 2400 with Karmic issues **".

I am guessing but there may be other systems with the same chip-set issues with Karmic.

my2$

shadetree

---

### Post by baddad on 2009-12-29
I have downloaded version 9.10 and burnt it to a cd, when i try to run the cd or to set it up as an OS on my computer it gets to a certain point and my screen just goes blank and nothing happens, i can not even access anything on my PC and have to reboot to get anywhere

---

### Post by margazhang on 2009-12-29
> **xiaohunying said:**
> Every time I reboot my computer, it shows on my monitor 
"Input Signal Out of Range
Change setting to 1440X900 - 60Hz"
or sometimes
"Auto adjust in progress
Recommended setting: 1440x900 60Hz"
and then I get to see the login of ubuntu.

but if i shut down my computer and start it by push the power button, there'll be no signal and a black screen. I am frustrated. Anyone can help me?

It more sounds like a display problem, check my post here and find the way to install the proper NVIDIA driver at the command line:

[http://ubuntuforums.org/showthread.php?p=8575698#post8575698](http://ubuntuforums.org/showthread.php?p=8575698#post8575698)

---

### Post by shadetree1 on 2009-12-29
> **margazhang said:**
> It more sounds like a display problem, check my post here and find the way to install the proper NVIDIA driver at the command line:
 
[http://ubuntuforums.org/showthread.php?p=8575698#post8575698](http://ubuntuforums.org/showthread.php?p=8575698#post8575698)
 
These 2400's use Intel chip-sets native, not NDVIDA.
 
Install start-up-manager and change the beta grub loader to 16 bit and the next highest boot menu resolution and restart.  
 
Your monitor may be able to go even higher, just go at steps.  
 
Your monitor "out of range" protection can't use the low default settings of the default Karmic grub loader.
 
shadetree

---

### Post by xiaohunying on 2010-01-05
> **shadetree1 said:**
> These 2400's use Intel chip-sets native, not NDVIDA.
 
Install start-up-manager and change the beta grub loader to 16 bit and the next highest boot menu resolution and restart.  
 
Your monitor may be able to go even higher, just go at steps.  
 
Your monitor "out of range" protection can't use the low default settings of the default Karmic grub loader.
 
shadetree

problem solved.
I installed SUM and changed color depth to 24 bit, then problem solved. Thank you so much.

---

### Post by shadetree1 on 2010-01-05
> **xiaohunying said:**
> problem solved.
I installed SUM and changed color depth to 24 bit, then problem solved. Thank you so much.
 
Good to here you got it going :P

---

### Post by Coltomis on 2010-02-06
I have slightly the same problem. I use ubuntu 9.10 netbook remix and I can load it up. after it loads grub and shows all the OS's on it, I push enter on Ubuntu. it then proceeds to the white Ubuntu logo and after several seconds, it disappears. 

I have tried pressing esc and then this shows up:
Gave up waiting for root device. Common problems
-Boot args (cat /proc/cmdline)
  - check rootdelay= (did the system wait long enough?)
  - check root= (did the system wait for the right device?) 
-Missing Modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/32228esd-73c6-4051-aa11-b65cc2cdbff6 does not exist. dropping to shell!


Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)

then with a blinking line after it: (initramfs)

I have the worst luck when it comes to computers! please help!

---

### Post by gqqser on 2010-03-15
Has there been any update to this problem. I am running Ubuntu 9.10 Remix on an aspire one net book and I get the same thing. It boots the grub, when I select one of the option (any of the options) I get the ubuntu logo and then a blank screen. 

Very Frustrating to say the least...I am trying the live cd on USB now to see if I can get around this or install 9.04

I just wish someone knew what was going on with this

---

### Post by fslezak on 2010-06-07
Try this solution.

( Workaround A, for Lucid. Will probably work on yours, though)

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---


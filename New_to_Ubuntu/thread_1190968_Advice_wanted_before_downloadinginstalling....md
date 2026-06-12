---
title: "Advice wanted before downloading/installing..."
date: 2009-06-18
forum: New to Ubuntu
---

### Post by Jamdog on 2009-06-18
As a person who has always reluctantly used Windows 'because it's there', I have chosen to dip my toe in the warm waters of Linux, and am hoping my toes will not be bitten off by underwater nasties.

My first step was to choose a distro, and upon the recommendation of many, I have decided upon Ubuntu.  Unfortunately, I am unsure of my second step, and already require a little hand-holding.

My first question is that I would like to have the ability to run a webserver with PHP and MySQL.  It would also be nice to add remote shell login accounts, as I often work on code that requires collaboration.  Do I need the Server edition, or will the Desktop edition do this?

I would like to dual-boot, keeping my current Win XP installation (at least until I am more comfortable with Ubuntu).

My second query is that I also need to know if I meet minimum requirements, which I was unable to find a list of.  My PC is a 4-year old Packard Bell x86 AMD 1.8GHz single-core processor with 768Mb RAM and NVidia GeForce4 MX 440 Graphics card.  I have 2 physical hard drives, split into 3 partitions.  The drive letters in Windows are:
C: Disk0 Part0  22Gb (11Gb Free) - Windows XP installed here
D: Disk0 Part1  45Gb (15Gb Free) - Most windows programs installed here
E: Disk1 Part0  76Gb (65Gb Free)

Can anyone advise me on whether I can fit Ubuntu onto the first partition with space to spare, or how to get it onto E: (1st partition of the 2nd drive) which would be my preferred option.

---

### Post by jimmy the saint on 2009-06-18
The server addition and the Desktop addition are mostly the same, just with different programs installed.  You can easily install the Desktop version then add the packages you need for the server.  If you are looking to run a full-time server, I would recommend using a dedicated machine if you can (you don't need much for that, I picked mine up free when someone was tossing it) simply because you will probably need to shut down the desktop from time to time for vairous reasons.  But that is not entirely neccessary.

As for the requirements, you should be more than fine.  Your partitions are all big enough. Back up your files first and (I recommend) create a disk image of your windows partition so that you can start over if you need to.  To be safest, I would probably install Ubuntu to your second disk first, then make sure everything works.  That way you still have your Windows present in case you need to jump online to get help. 

Ubuntu is great.  You may also look into Xubuntu (slightly lighter) which may run a little faster for you, but I have found that the performance increase is nominal for most applications.  Firefox definitely worked faster for me in Xubuntu and I run a dual core processor with 4 gigs of RAM.  Go figure!

---

### Post by Idefix82 on 2009-06-18
Hello and welcome! I hope I don't forget any of your questions but here goes:

> Do I need the Server edition, or will the Desktop edition do this?


It's your choice but I would recommend to install the desktop edition and then install all the server software you need. The server edition does not install a desktop environment so is not necessarily the easiest way to begin working with Linux.

> My second query is that I also need to know if I meet minimum requirements

You should be ok. I am running Ubuntu on a laptop with much lower specs. You might have to fiddle to get your wireless card working but everything else **should** work out of the box (fingers crossed).

> Can anyone advise me on whether I can fit Ubuntu onto the first partition with space to spare, or how to get it onto E: (1st partition of the 2nd drive) which would be my preferred option.

You will have no problems installing Ubuntu on the E: partition. In the installer, choose the manual installation and then tell Ubuntu to create a partition wherever you want it to go, to format it as ext3 and to mount it as / (i.e. root folder). You should also create a SWAP partition, somewhere between 500MB and 1GB in size. It might be easier if you free up E: completely before you start installing and give it all to Ubuntu.

Edit: if your logged in users are to have their own home folders, it might make sense to also create a separate partition and to mount it as /home. This way you will have a natural limit on the space your clients can use up, namely the size of the dedicated partition.

---

### Post by Ms_Angel_D on 2009-06-18
Hello, the others have already nicely addressed your questions, I would like to follow up what they have said with some helpful links. These are definite recommended reading, and will make your transition to Ubuntu/Linux much smoother.

(listed in no particular order)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)


This guide references Ubuntu 8.04 but the same steps apply to Ubuntu 8.10 & 9.04 as well.
[How to dual boot Windows XP and Linux (XP installed first) -- the step-by-step guide with screenshots]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm")


All of these will answer many(not all but most) of the questions you might have as a linux/Ubuntu beginner.

Good Luck!

[edit]I also found this page for you ;) [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)[/edit]

---

### Post by Jamdog on 2009-06-20
Thanks to everyone for the helpful advice.  I am now talking to you from within Ubuntu.

I split my drive E: into 3 partitions, 30Gb for root and 20Gb for /home, and I also made an 8Gb partition on the other hard-drive for 'swap space' (wasn't sure how much was needed, but better safe than sorry).

The problem I now have is I seem to be stuck in 640x480 resolution (my only other choice is 320x240 which is just silly!).  I used to use 1024x768 on Windows (my graphics card/monitor will do 1600x1200 but my monitor squeals).  When I choose System->Preferences->Display, I get the message "It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?".  Clicking 'Yes' shows me the "NVidia X Server Settings" screen, but it jumps around the screen due to the low res, and says I can only choose 640x480, 320x240 or Auto as the Resolution...

I'm hoping someone here can help me resolve this, as it's very difficult to work like this...

---

### Post by Bucky Ball on 2009-06-20
Go to Synaptic Package Manager (System->Administration) and do a search for:

ubuntu-restricted-extras

Install.

When you open System->Admin->Hardware Drivers, what have you got in there? Is there an Nvidia driver in there enabled? 

When Nvidia Settings is jumping around the screen, can you set 'Auto'?

---

### Post by Jamdog on 2009-06-20
> **Bucky Ball said:**
> Go to Synaptic Package Manager (System->Administration) and do a search for:

ubuntu-restricted-extras

Install.Thanks for the helpful advice - I'd have never found that...  Not sure what it does, but I installed it.  Hasn't had any effect on the display though...
> **Bucky Ball said:**
> When you open System->Admin->Hardware Drivers, what have you got in there? Is there an Nvidia driver in there enabled? 
Yes, it says "NVIDIA Accelerated Graphics Driver (version 96) [Recommended]" and has a green 'light' next to it, and at the bottom, says: "This driver is activated and currently in use."
> **Bucky Ball said:**
> When Nvidia Settings is jumping around the screen, can you set 'Auto'?It's difficult to set anything due to the 'jumping', but 'Auto' was already set, and I can only change it to 240x320 or 640x480.

---

### Post by Jamdog on 2009-06-20
A little more info on this problem...
When selecting System->Settings->Display, and then clicking 'Yes' on the aforementioned message box, it takes me to the same place as System->Administration->NVIDIA X Server Settings.  This reports as version 96.43.10
I have downloaded the latest drivers from the NVIDIA website (96.43.11), but when I type "sudo sh NVIDIA-Linux-x86-96.43.11-pkg1.run" to install it, I get the message: "ERROR: You appear to be running an X server; please exit X before installing."  I can remove the driver in System->Admin->Hardware Drivers, but still get the same message when installing the new one.  Any ideas how I can stop the X Server? (it doesn't show on 'ps' as far as I can see, so I can't 'kill' it)

---

### Post by Bucky Ball on 2009-06-20
Yup, xserver needs to be stopped to change vid drivers. And here's how to do it:

[http://www.cyberciti.biz/faq/how-to-stop-xorg-server/](http://www.cyberciti.biz/faq/how-to-stop-xorg-server/)

Because you have an older card, from memory, the newest drivers may not be appropriate.

You could also try Envy-ng from Synaptics also, if all else fails. That will try and select the appropriate driver for your card, remove and old artifacts of previous drivers and install the correct one. Works for some.

---

### Post by Jamdog on 2009-06-20
Sorry, but even with the excellent advice given here, I'm still feeling hopelessly lost.   I have never used linux before, apart from using a few basic commands in a bash shell.

Everything I've tried so far has not resolved my 640x480 screen resolution problem, and I really don't want to have to go back to Windows XP, but Ubuntu is rendered almost unusable at this resolution.

I tried following your link to stop the X Server, Bucky Ball, and my screen went black with a flashing cursor in the top-left, but nothing more happened.  I'm guessing I did something wrong, but I don't know enough about Ubuntu to know what it was...  You mentioned using Envy-NG, but I have no idea what that is, or how to use it.  I've used Windows since v3.1, and used MS-DOS and GEM Desktop before that, and I feel like a total noob all over again... :confused:

I'm glad I anticipated that all may not go smoothly, and had the foresight to dual-boot, keeping my Win XP 'just in case'.  I spent the majority of my time online doing web-design, programming and general socialising (Messenger, forums, MUDs), so can't afford to be without a fully-operational OS for long.  I am very willing to give Ubuntu another go, I really want to get this working, but I really need help with it, in the form of step-by-step, detailed instructions, or something like that.

---

### Post by Jamdog on 2009-06-20
I found [this post]("http://ubuntuforums.org/showpost.php?p=3783384&postcount=2") which may be of help - going to boot back into Ubuntu now to try it - will let you know how it goes...

---

### Post by Bucky Ball on 2009-06-21
Using this method, you don't have to use a terminal at all and Envy will hopefully install the correct driver for you (I have my doubts about the newest):

* Go to:

System->Administration->Synaptic Package Manager

* Click the 'Search' icon and do a search for:

envyng-gtk
envyng-core

* Click the boxes to the left and 'mark for installation'. Click 'Apply' in the upper left toolbar.

You should now find Envy-ng in one of your drop down menus. Open it up and let it attempt to install the appropriate driver. Make sure you get it to investigate for an Nvidia driver, not ATI (there are two options).

Hope that helps. :)

---

### Post by 3rdalbum on 2009-06-21
You should send a bug report to Nvidia; being stuck at a low resolution is definitely not what I'd expect.

I know that basically their driver for the old cards is pretty old (your card requires the version 9x.xx driver, and the latest cards use the version 180.xx driver) so maybe you have to use some old-fashioned hackery to enable a better resolution.

Press Alt-F2 and **copy and paste** in the following:

```
gksudo gedit /etc/X11/xorg.conf
```

A text file will open with settings for the X server; it will have sections like this:

Section "ServerLayout"
  - some settings
EndSection

Section "InputDevice"
...
Section "Monitor"
...

etc.

Your Section "Screen" should read something like this:

```

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    SubSection     "Display"
        Modes      "1024x768"
    EndSubSection
EndSection

```

There might be some other settings in there, or maybe some other 'modes'. Those can stay, but the important part is that there is a SubSection "Display", and that your preferred resolution is one of the 'modes', and that you have EndSubSection after this.

Save your changes and reboot, and cross your fingers. If anything goes wrong Ubuntu should be able to recognise this and switch back to safe graphics mode so you can fix the problem, but with some luck you will be able to boot up properly and select the good resolution.

Make sure you answer "No" when asked if you want to use the graphics card vendor's tool; I believe you will need to set the good resolution using the actual System > Preferences > Display program and not with the Nvidia program.

---

### Post by hyperdude111 on 2009-06-21
I know why you have the resolution problem. 

Your graphics card has not been supported since 8.04, I had the same card a while ago and this was part of the reason I got a new pc. I would recommend ubuntu 8.04 for your hardware.

---

### Post by rjs1064 on 2009-06-21
i had the same problem.had to edit xorg conf and add horizsync and refresh rate values. it now works. interestingly i tryed mandriva which worked first time from live cd and on investigation used the more recent nvidia graphics driver (173.14.18 not 173.14.16) rather than the one in synaptic. i also couldn't install the driver from nvidia this terminal stuff takes some getting used to

---


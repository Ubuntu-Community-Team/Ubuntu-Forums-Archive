---
title: "Need help with xorg-intel upgrade"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by TheOctagon911 on 2010-08-06
Greetings to all who are Linux;

Now, -- heres my problem:

I am trying to run ubuntu 10.4 in virtual PC 2007, ON a Win7 AMDx64 box. Plenty of ram, plenty of disk space. My xorg only see's things as the very basic default stuff (mouse only points but won't scroll; video is stuck at 800x600 (and I'm on a 1920x1600 screen UGH and ARGH) and I have zero sound. The xorg has not and will not generate a xorg.conf file in my /etc/X11 folder. I have to go to recovery/root mode and do the xorg -configure to get the xorg.conf.new file, which does squat for me. It has all the defaults that don't work in it. I tried editing it under the screen section with the appropriate V & H sync settings and resolution, only to have it totally crap out on me and become unbootable. Obviously my novice self did something wrong. Reinstall!

The synaptic package manager (who's irony in its name is not lost on me) says I have the xserver-xorg-intel package on here, but not the most current version. It refuses to update that package, and (here is where I got really aggravated) I can only seem to find the drivers in a "not-ready-to-install" state and have to be "built" in order for the bloody manager to see it. What is wrong with pre-packaging folks, huh? Tell me.

I am running the following machine:

Asus CM5570  w/AMDx64 duel core -- i686 (see note below)
Intel X4500 integrated graphics  (G43/G45)
Realtek network card (which actually works! Wooohooo!)
Intel/Realtek integrated audio
6 GB of ram
750 Gb HD
Win 7 home premium edition
Virtual PC 2007

*(Note: Apparently I do not have a 'true' 64 bit machine, so says Linux, as when I tried installing the 64 bit version of Ubuntu it told me I was on an i686 and not an x64. Hmmmmm)

I want/need to run this in a virtual environment for multiple reasons, so the first person to tell me to make it a duel boot instead will find generations of their kin damaged beyond repair. *grin* 

I would paste in a copy of my xorg.conf file, but it doesn't exist and when I create the .conf.new file, it has the basic defaults you can find all over the Internet, including the bloody s3 video driver settings. 

My eyes hurt from this crappy resolution, my head is pounding from the endless research to nowhere, and I'm about ready to toss Linux to the curb. So, to all whom are Linux, here's your chance to convert a die-hard windows person over. I am yours to lead, if you are up for the challenge. 

With warmest animosity and regard,   *wicked grin*
TheOctagon911

---

### Post by dv3500ea on 2010-08-06
I've never heard of > Virtual PC 2007 but I've never had any problems running Ubuntu in a Virtual Machine. I would suggest using[ Virtual Box]("http://www.virtualbox.org/"), which is free.
Because it is a virtual machine, the specific model of your hardware shouldn't matter and your specs show that you have plenty of resources to run Ubuntu in virtualbox.

> in Windows I know I can get or download a 'package' and its ready to go - double click and it installs You can do this in Ubuntu by downloading .deb files (double-clickable), although it is recommended that you use the package manager. Ubuntu Software Centre makes installing software painless and Synaptic Package Manager is good for advanced users. The centralised repository system is much easier and more secure than downloading individual installers.

> We are expected to know how to "build" packages, make diffs, know what the heck diffs are and how they apply You are not expected to know this and compiling from source is not something you should try unless you are 100% certain of what you are doing. To install software, use the software centre; to install drivers, it is preferable to go to System -> Administration -> Hardware Drivers.



Sometimes a specific program or driver is not available from the repositories. However, this is rare and often there is a ppa available, which you can add and install packages normally from.

---

### Post by wilee-nilee on 2010-08-06
Have you looked in system-admin-hardware drivers to see if there is a driver for the graphic card there to be enabled?

Post this, if nothing is there.
```
lspci | grep VGA
```

---

### Post by TheOctagon911 on 2010-08-06
> **dv3500ea said:**
> 

 You can do this in Ubuntu by downloading .deb files (double-clickable), although it is recommended that you use the package manager. Ubuntu Software Centre makes installing software painless and Synaptic Package Manager is good for advanced users. The centralised repository system is much easier and more secure than downloading individual installers.

 You are not expected to know this and compiling from source is not something you should try unless you are 100% certain of what you are doing. To install software, use the software centre; to install drivers, it is preferable to go to System -> Administration -> Hardware Drivers.

Sometimes a specific program or driver is not available from the repositories. However, this is rare and often there is a ppa available, which you can add and install packages normally from.

Thank you for the kind reply. Regarding this quote; being a true windows-whiner, the GUI is the first place I went to try some of these corrections. I could not get the xorg-intel driver to update to the 2.12 version that has just come out. It just reinstalls the older version (as it shows in the version column of the S.P.M.) Additionally, I couldn't find any .deb files for download out there, they all have either the tarball extentions, the gz, or the pkg extention. What I could find was that I was expected to "make" those .deb files out of the files they provide for download. That is where my frustration with all of this came in at. If you know of a .deb package for the xserver-intel package is, please do share! *Smile*

Virtual PC is by Microsoft and it is the scaled down version of their Virtual server. Hyper-V followed by being built in to 2008 R2. I am unfamiliar with Virtual Box, but will check it out to see if it will run microsoft OS's as well. Thank you for that info.

---

### Post by TheOctagon911 on 2010-08-06
scott@scott-ubuntu:/etc$ lspci | grep VGA
00:08.0 VGA compatible controller: S3 Inc. 86c764/765 [Trio32/64/64V+]

---

### Post by dv3500ea on 2010-08-06
It appears there is a ppa repository you can add so that you can install this latest version from the package manager.

Go to System -> Administration -> Software Sources
and add this:
```
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu lucid main
``` (see screenshot)

Then run System -> Administration -> Synaptic Package Manager.
Click 'Reload'.
Click 'Mark all Upgrades'.
Click 'apply'.

---

### Post by davec64 on 2010-08-06
Just a heads up on Virtualbox, it will run MS OS'es (I use it!)

And if you want USB support download the closed source version (still free) rather than the OSE. You can then get USB support by installing Guest Additions.

---

### Post by aysiu on 2010-08-06
I don't have any experience with Virtual PC 2007, but I use VirtualBox on a regular basis, and I've virtualized Ubuntu on Windows, Windows on Windows, Ubuntu on Mac...

If you do decide to go the VirtualBox route, I believe you have to install Guest Additions in order to get the screen resolution beyond 800x600. There's a little guide to that here:
[http://ubuntu-tutorials.com/2010/06/26/install-virtualbox-guest-additions-on-virtualbox-guests/](http://ubuntu-tutorials.com/2010/06/26/install-virtualbox-guest-additions-on-virtualbox-guests/)

You may have to reboot the virtual machine to have the changes take effect, but then you should be able to go to System > Preferences > Display and pick the screen resolution you want.

The fact that your computer is coming up as i686 instead of AMD64 may also have to do with your running Ubuntu as a virtual OS instead of running it native (I'm not telling you to set up a dual-boot--I'm just explaining why the processor type may not be detected correctly). My understanding is that the virtual environment sets up some virtual hardware as well, which is why you sometimes can run desktop effects natively but not in a virtual environment.

---

### Post by CharlesA on 2010-08-06
It's the virtualization software you are using. You can use VirtualBox instead. I've only heard of VirtualPC 2007 talked about when refering to running "XP Mode" in Win7.

I'd not bother using it tbh, since VBox and VMware player work better.

Anyway, give virtualbox a shot and install the guest additions and you should be good to go.

---

### Post by yknivag on 2010-08-06
> **TheOctagon911 said:**
> Thank you! A voice of reason! I don't know why people think that just because I am frustrated with this and am a Windows admin that I am some moron that doesn't know how to do research. Again, if it was an easy fix, I wouldn't be here asking for help. Thank you [yknivag]("http://ubuntuforums.org/member.php?u=352142") for showing some compassion.

You're welcome.

I've been using Linux/HPUX/Solaris since the mid 1990s and Windows since 3.11 so I'm not really new to either.  Yet since Ubuntu 8.04 I've not been able to get my Intel graphics card to work properly with the official Ubuntu xorg-intel driver in the repositories.

To be honest, mine is just about usable so long as I don't want to use hardware acceleration but I'm resigned to the fact now (after over a year of frustration) that the only options are going back to 8.04 or buying a newer ATI/nVidia card.

Incidently while you're playing if you do end up with a blank screen pressing "F1" should drop you to a command prompt still.  Login again and run:

```
sudo dpkg-reconfigure xserver-xorg-video-intel
```

That should get you back to the previous version.  Press "F7" to get back to your graphical tty and then "Ctrl+Alt+Backspace" to restart X.

Hopefully that will save you from the endless cycle of re-installing.

---

### Post by snowpine on 2010-08-06
(edit) Attempt to offer support deleted. :)

---

### Post by rhigmus on 2010-08-06
> **TheOctagon911 said:**
> 
I am running the following machine:

Asus CM5570  w/AMDx64 duel core -- i686 (see note below)
Intel X4500 integrated graphics  (G43/G45)
Realtek network card (which actually works! Wooohooo!)
Intel/Realtek integrated audio
6 GB of ram
750 Gb HD
**Win 7 home premium edition**
Virtual PC 2007


I'd like to point out two things if I may. 

1. Your using Win7 Home Premium, right? Ok, Virtual PC 2007 isn't supported by Home Premium, I know this because it became necessary for me to install and use VirtualPC at work. This required me to upgrade to Win7 Professional or BETTER. I'll allow this is potentially a typo on your part. If you really are using HomePrem then its likely only the "XP-mode" that installed correctly.

2. Virtual PC 2007 is a right picky piece of I'd-rather-not-say. Does not like 64bit guest OSes. And I have had it flat out refuse every attempt at Linux (and I'm no green linuxer, despite my bean count :D).

Others have suggested VirtualBox (free) which is a great program. However, I got authorization to purchase VMWare Server, and that pretty much settled any issues I was having.

This also prompted me to install vmware on my laptop (ubuntu 10.04, beautiful!), and now I'm virtualizing Win7 on it.
Sorry to go on about MS so much, yikes I did not mean to do that.

---

### Post by aysiu on 2010-08-06
> **snowpine said:**
> With respect to aysiu's moderatorial decision :) splitting the posts separates this rant from an important detail of the OP's problem. That's actually because I wanted support in this thread and rant stuff in the other thread. [I don't know why people try to offer support in rant threads](http://ubuntuforums.org/showthread.php?t=634322), instead of offering support in a support thread.

---

### Post by TheOctagon911 on 2010-08-09
Thanks to all who provided excellent ideas and support. This issue has been resolved. My problem was indeed the Microsoft Virtual environment I was running. I believe, as one commenter pointed out, that Virtual PC 2007 has issues with what is called "XP Mode", and even though I wasn't trying to run anything specifically in that mode, it must have had something going on in the background. 

Someone had suggested that VirtualBox by Oracle would work, and it did. Not only did it work the first time, but my installation went so smoothly that I blew it away and reinstalled it again to make sure I didn't miss anything. Upon installing the Virtualbox additions into the ubuntu, my resolution issues went away, my mouse started scrolling, and a host of other unimportant but equally annoying issues as well. 

I am now running this (Ubuntu 10.4) in a virtual window FROM windows 7 on 1360x768 resolution with a gig of allocated RAM and 20 gig HD allocated space. It runs great! No runs, no drips no errors! Thanks to all who helped and inspired!

:D

---


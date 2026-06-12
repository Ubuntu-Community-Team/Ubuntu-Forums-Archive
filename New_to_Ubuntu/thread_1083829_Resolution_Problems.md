---
title: "Resolution Problems"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by jman5555 on 2009-03-01
Hello, 
I know this problem has already been posted in different ways, but personally I can't resolve the resolution problem in Ubuntu 8.10. I have just installed Ubuntu through windows(xp) and downloaded and installed all recommended updates. The problem though is that my resolution defaults to 800 by 600. When I go to the screen resolution menu it gives me only three screen size options (all for smaller screens.) I have tried many methods of of obtaining a better screen resolution, but all have failed.
Specs
Dell P991 Moniter
NVIDIA RIVA TNT2 Model 64 Graphics card
Dell Dimension 4100 actual comp.

I will post my config document next post.

---

### Post by residualbit on 2009-03-01
If you go to System>Preference>Hardware Drivers are there any restricted drivers available? If you find any, clicking on them will launch the install and all you will have to do is restart you machine. Let me know if this helps!

---

### Post by jman5555 on 2009-03-01
I have tried it with to no avail. All I achieve is a message stating that no proprietary drivers are in use on this system.

---

### Post by jman5555 on 2009-03-01
I re-installed a little while ago and there are many updates avaiable, could some be driver updates?

---

### Post by JohnLM_the_Ghost on 2009-03-01
> **jman5555 said:**
> I re-installed a little while ago and there are many updates avaiable, could some be driver updates?
It is possible... however I believe only updates for currently installed packages are shown.

Try ```
sudo apt-get install xserver-xorg-video-nv
```
to ensure the nvidia driver is installed (it is going to install it if it isn't)

---

### Post by jman5555 on 2009-03-01
I have tried but it doesn't look like we got any where.
here is what I got:
Reading package lists... Done
Building dependency tree        
Reading state information... Done
xserver-xorg-video-nv is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 255 not upgraded.

---

### Post by JohnLM_the_Ghost on 2009-03-01
Hmmm I guess that means it is installed after all... and updated as well.

That can only mean the driver is not compatible and/or is not used.
Of course the latter reason is preferred, cause that can be fixed.

Unfortunately I don't own Nvidia card... so I cannot be of any more help.

---

### Post by jman5555 on 2009-03-01
Um, any more suggestions? I am really stuck, I have been trying to convince a few in my house hold that we should switch to linux but...frankly they haven't been to impressed.:lolflag:

---

### Post by JoshuaRL on 2009-03-01
> **jman5555 said:**
> Um, any more suggestions? I am really stuck, I have been trying to convince a few in my house hold that we should switch to linux but...frankly they haven't been to impressed.:lolflag:

Alright, do the updates first.  Then when its done, we'll see about getting your drivers loaded correctly.  If you use the open-source "nv" driver, it will not let you have 3D direct GPU rendering.  That's only from the proprietary Nvidia drivers.  But don't worry about that right now, we'll get to that in a second.

---

### Post by jman5555 on 2009-03-01
Ugh, It will not boot. Must be me trying a few things out in the terminal...I'll reinstall then install the updates. BTW, I'm sorta a beginner at this so I might need some explanations.

---

### Post by JoshuaRL on 2009-03-01
> **jman5555 said:**
> Ugh, It will not boot. Must be me trying a few things out in the terminal...I'll reinstall then install the updates. BTW, I'm sorta a beginner at this so I might need some explanations.

No problem, I can do that too.  Why exactly wont it boot?  What are the errors?

---

### Post by jman5555 on 2009-03-04
Hey,
Sorry for the slow response. I will have time to work on this later, on the weekend, but right now I'm a bit bogged down with stuff. Thanks for your help so far though, and I hope we get this sorted out.

---

### Post by JoshuaRL on 2009-03-05
> **jman5555 said:**
> Hey,
Sorry for the slow response. I will have time to work on this later, on the weekend, but right now I'm a bit bogged down with stuff. Thanks for your help so far though, and I hope we get this sorted out.

That's fine, we'll work on it when you get time.  That'll be $19.99 and we accept all major credit cards.  Oh wait, that's that OTHER operating system ...

---

### Post by jman5555 on 2009-05-10
Wow, can't believe I've been so bogged down lately. So currently I am just running Ubuntu from the disk. It is installing the system. It still looks like the resolution is messed up. I was researching Ubuntu awhile back and I found that it only uses opensource drivers. Maybe that is where the problem is originating. Is it possible to download and install the "closed" drivers from the Nvidea website?

---

### Post by jman5555 on 2009-05-10
Great News!
I was able to force change my resolution in the xorg.conf. The only problem I am getting is that Ubuntu is forcing me to run in low graphics mode. The reason has something to do with a framebuffer device or whatnot. Anyway any help would be much appreciated.


P.S. I will attach my xorg.conf in my next reply.

---

### Post by jman5555 on 2009-05-10
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Generic Monitor"
	SubSection	"Display"
		Modes	"1280x1024"
	EndSubSection
EndSection

---

### Post by JoshuaRL on 2009-05-11
So after you reinstalled, did you update?  And did you see any drivers listed when you opened System->Administration->Hardware Drivers?

---

### Post by jman5555 on 2009-05-11
Ok, I have not yet installed updates, but I will soon. Right now though, there are no hardware drivers listed. Also do you know anything about this "Envy" program. It looks like it could help. Finally I was  wondering what you thoought about the force change in resolution. COuld the frame buffer problem be fixed?

---

### Post by JohnLM_the_Ghost on 2009-05-11
> **jman5555 said:**
> Ok, I have not yet installed updates, but I will soon. Right now though, there are no hardware drivers listed. Also do you know anything about this "Envy" program. It looks like it could help. Finally I was  wondering what you thoought about the force change in resolution. COuld the frame buffer problem be fixed?

Hmmm... form your xorg.conf it seems that X is configured to use generic fbdev (framebuffer device) driver. If for some reason it doesn't detect your video card correctly, you might need to manually edit xorg.conf to use a particular driver.
Yeah, but install those updates before you start to tinker with things.

Well about "Envy"...
It used to be main user-friendly (with GUI) way to install proprietary video drivers. However since Gutsy (or Feisty?) "Hardware Drivers" manager program was developed and shipped with Ubuntu, what made "Envy" somewhat obsolete.
Well, I wouldn't say "Envy" is the best option, but if nothing else works you and you're not comfortable to manually edit config files, you could give it a try.

---

### Post by jman5555 on 2009-05-11
Ok I have installed all of the updates and I am going to restore my xorg.conf file to the way it is when I first install.

---

### Post by jman5555 on 2009-05-11
Ok. So I have all of the updates now. I still don't have any drivers showing up. I reset my xorg.conf to the generic one (the one my computer has been using) and I am still getting the no valid frame buffer error. So how do you actually want me to tinker with the xorg.conf file?

---

### Post by JoshuaRL on 2009-05-12
So just to clarify, you have all the updates installed?  And you've gone to System->Administration->Hardware Drivers and no proprietary drivers are showing?

If so, could you post the output of the following?
```
lspci
```

As far as manually editing xorg.conf, I wouldn't suggest it unless absolutely necessary.  Since Hardy (Xorg 7.3+) autodetection has been favored over manual xorg.conf tweaks, and a lot of the syntax has been changed.  So if you find info from before that, it will either not work or break stuff.  But we're gonna try a couple other steps before parsing the net for the necessary info.

---

### Post by jman5555 on 2009-05-12
Ok here is the output. And yes your clarification was correct.

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
01:09.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
01:0a.0 SCSI storage controller: Advanced System Products, Inc ABP940-U / ABP960-U (rev 03)
01:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:0c.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
01:0c.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
01:0d.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

---

### Post by jman5555 on 2009-05-12
```
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
01:09.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
01:0a.0 SCSI storage controller: Advanced System Products, Inc ABP940-U / ABP960-U (rev 03)
01:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:0c.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
01:0c.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
01:0d.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
```

---

### Post by JoshuaRL on 2009-05-13
Looks like you have an Nvidia Riva TNT2 64 Pro GPU in there.  We have a couple options.  For any of the following, if you run into trouble and can't get the screen to show anything (misconfigured or wrong drivers), please reboot and choose the Recovery Mode from the Grub menu.  From there, scroll down to the "xfix" option and then resume normal boot.  That should get you to a workable graphical system to try again.

First let's go to System->Administration->Synaptic Package Manager.  From there, search for the following:
> nvidia-glx-71
Then mark it for installation by clicking and apply the changes.  That will attempt to install the proprietary driver from Nvidia that should work with your card.  Once you've installed it, you'll need to do Ctrl+Alt+Backspace to restart the X server.  That will allow the driver to be loaded, and you should be in 3D graphics at that point.

If that doesn't work, do the same thing but search for:
> xserver-xorg-video-nouveau
That is the open source experimental driver for Nvidia that can sometimes provide 3D acceleration.  If it works for you and you're fine running an experimental driver, that can be a good option.

If it doesn't work or you find it too unstable, you can install the stable 2D driver by searching for the following:
> xserver-xorg-video-nv  This option will NOT give you Compiz, compositing, or any cool 3D effects.  But it should run faster and more efficient than the one-size-fits-all "vesa" driver.

Another option you could try is to manually install the proprietary driver.  I didn't suggest this before because if it doesn't install from Synaptic, it may not work for you.  And it's usually a little more work.  Plus, you'll need to reinstall the driver this way for EVERY kernel update.

The best way to do this is to use the Envy application.  From Synaptic, search for:
> envyng
Go ahead and install both "envyng-core" and "envyng-qt".  Then run it from the terminal with:
```
envyng -q
```
It should tell you to install the -71 driver if I read the description correctly.

I hope that helps.  Unfortunately, Nvidia has been a little unhelpful with some older cards.  If you run into trouble here, please post.  But you also might think about upgrading to a newer card if that is possible.  Just a thought.

Hope that helps.

---

### Post by jman5555 on 2009-05-13
OK, I tried the first one and it installed correctly, but I am not getting any changes, and when I try to run open arena it just doesn't start. Without the driver open arena worked extremely slow but it still started. I then tried the envy thing, and all it did was told me that my driver was installed correctly. Then I searched for that expirimental driver you were talking about. My search yeilded no results for some reason. I aslo tried rebooting the entire system, but nothing happened. On the boot screen when all of the code is going by I saw that when it tried loading nvidia it got a fail. Right now I have no clue as to what is happeneing. I really don't want to have to go down to a 2d driver if it is possible. 

Thanks so far for your help

P.S. The computer I am running Ubuntu on is an old clunker that I am just wanting to breath new life into so I doubt I would upgradee my card.

---


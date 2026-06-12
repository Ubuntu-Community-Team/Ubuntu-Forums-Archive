---
title: "Lucid fglrx, no hardware drivers."
date: 2010-07-18
forum: New to Ubuntu
---

### Post by djk21108 on 2010-07-18
I have installed fglrx by ways of synaptic.

Unfortunately when I go to the Hardward Drivers screen I find  "no proprietary drivers are in use on this system"

I don't think fglrx is being utilized, what can I do about this?

---

### Post by djk21108 on 2010-07-18
Anyone have any advice for this?

---

### Post by ajgreeny on 2010-07-18
Firstly, what is your video card?

Secondly, look in System ->Administration ->Hardware Drivers.

If there is a driver available for your card you can get it that way.  If none are listed, there are no proprietary drivers available and you will have to make do with the open source driver.

---

### Post by djk21108 on 2010-07-18
I have an Ati Mobility Radeon x1400.

There is absolutely nothing listed under Hardware Drivers.

---

### Post by ell02 on 2010-07-18
Had that problem on Lubuntu and installing fglrx-dev made something show up in hardware drivers(probally not the right approach).Searching 
radeon in synaptic shows a few options.
Never had this happen on a gnome ubuntu though.Not a solution but a direction to look perhaps.

---

### Post by djk21108 on 2010-07-18
Well that can't hurt so I'm gonna give it a shot right now.

I'll post back the results.

---

### Post by djk21108 on 2010-07-18
Results, sadly negative. Still nothing on the Hardware Drivers menu :(

---

### Post by clhsharky on 2010-07-18
djk21108

Your Ati Mobility Radeon x1400 card is no longer supported with fglrx. Radeon is the correct driver you your card now.

Sharky

Radeon is the default Open Source driver.

---

### Post by djk21108 on 2010-07-18
Sharky that is great news. I'm glad you have some insight on whats going on. Unfortunately I tried to go the Radeon route and I've had just as much problem. The command aticonfig just plain old doesn't work. 

I'm REALLY hoping you have some insight as to how I can get some drivers on my machine.

Thank you for your reply though.

---

### Post by djk21108 on 2010-07-18
Sharky, I see your edit, but I don't quite comprehend what that means. Is Radeon the driver I have right now? How can I find out?

---

### Post by clhsharky on 2010-07-18
djk21108

aticonfig doesn't work on radeon only on fglrx.
All so the xorg.conf file is not installed in Lucid by default.
So what is the problems your having?

Sharky

---

### Post by djk21108 on 2010-07-18
The problems I'm having are those of stuttery performance, especially on Java and Flash sites on the internet. I have a feeling, a driver might be able to better utilize my graphics card. Maybe I'm incorrect in assuming this, but when I boot into Windows, I have no problems with flash games and the sort.

Should I just assume that graphics card support will never be what it is on Win7?

---

### Post by djk21108 on 2010-07-18
Also, I'm not sure if this is related, but my laptop's fans have nut spun up once since the install of Ubuntu.

I'm thinking this might be due to the fact that my graphics card isn't noticed by the system.

The computers no hotter than usual, but I feel like that may because it's not using anywhere near full power.

---

### Post by clhsharky on 2010-07-18
djk21108

> Should I just assume that graphics card support will never be what it is on Win7?
Yes and no. Adobe flash supports windows better and fglrx quit supporting your card in 03-08. Window fglrx are old drivers that may be installed on some win OS but I don't think 7 for your card. Its probably Adobe flash player is the difference.

I have ATI 1650 card and have no problems at all with flash. So I don't know why yours is stuttering.
Do you have 64bit OS?

Sharky

---

### Post by djk21108 on 2010-07-18
I do not, I have a 32 bit OS, 2.0 dual core processer, 2GB's of RAM.


I'm just curious to see if my graphics card is WORKING. It kind of seems like it isn't.

---

### Post by clhsharky on 2010-07-18
djk21108

You should have this in your Xorg.0.log
System> Administration>Log file viewer
```
[    11.407] (II) LoadModule: "radeon"
[    11.424] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    11.447] (II) Module radeon: vendor="X.Org Foundation"
```


Sharky

---

### Post by djk21108 on 2010-07-18
Sharky,

I see a lot about VESA but I don't believe there is anything about Radeon. 

Should I revert to the original configuration that came with Ubuntu? If so how do I go about that?

---

### Post by clhsharky on 2010-07-18
djk21108

In terminal
Applications> Accessories>Terminal

Copy/Paste one line at a time then enter
Type in password  when asked then enter
```
sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
```
restart

Sharky

---

### Post by djk21108 on 2010-07-18
Perfect, it seems as though the radeon drivers are in and the framerate seems better.

You are really a fantastic troubleshooter Sharky. I thank you very much.

Do you have any thoughts on my lack of fan noise?

---

### Post by clhsharky on 2010-07-18
djk21108

> Do you have any thoughts on my lack of fan noise?

Maybe , the newer .35 kernels have better power management for laptops with OSS drivers.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc5-maverick/linux-headers-2.6.35-020635rc5_2.6.35-020635rc5_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc5-maverick/linux-headers-2.6.35-020635rc5_2.6.35-020635rc5_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc5-maverick/linux-headers-2.6.35-020635rc5-generic_2.6.35-020635rc5_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc5-maverick/linux-headers-2.6.35-020635rc5-generic_2.6.35-020635rc5_i386.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc5-maverick/linux-image-2.6.35-020635rc5-generic_2.6.35-020635rc5_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc5-maverick/linux-image-2.6.35-020635rc5-generic_2.6.35-020635rc5_i386.deb)

Download them all
Install, double click each, one at a time
In the order there listed
If it asks about grub choose the one you already have from the drop down.
restart

Sharky

---

### Post by djk21108 on 2010-07-18
Thanks for the advice. Just did what you suggested...but what exactly did you just give me? Once again I'm very new to linux so I'm not quite sure what just happened when I installed these 3 packages.

---

### Post by clhsharky on 2010-07-18
djk21108

That was the latest 2.6.35.rc5 kernel from Ubuntu compiled kernels.
The first was linux-headers-all
second was linux-headers-32bit
third was linux-image-32bit
they can be found here
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
More info here
[http://www.h-online.com/open/features/Kernel-Log-Coming-in-2-6-35-Part-1-Graphics-1034168.html](http://www.h-online.com/open/features/Kernel-Log-Coming-in-2-6-35-Part-1-Graphics-1034168.html)

Kernels can be removed in synaptic package manager, search linux.
You should still be able to boot your old kernel from boot menu.

Sharky

---

### Post by a71680 on 2010-07-18
try this link if its supported by ati for linux it would b here if not youll have to use an open source driver
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
hope this helps

---

### Post by clhsharky on 2010-07-18
a71680

Ati Mobility Radeon x1400

ATI Catalyst 9.3 wont work on Lucid(10.04), but it will work on Hardy(8.04). If it worked on Lucid it would be in Hardware Drivers.

Sharky

---

### Post by ajgreeny on 2010-07-19
To the OP:

I run an even older ati 9200SE card than yours in my desktop, and have a problem with 10.04 and slow refresh rates.  I also had a problem with 9.10 and had to use 16 bit colour in that to be able to have compiz running at all, at 24 bit colour I had no visible desktop background, just black, no icons at all, but the panel still showed as did application windows, until you maximised them.

I found this /etc/X11/xorg.conf to be the best I could use successfully:-
```
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
    Option        "EnableDepthMoves"    "True"
    Option        "EnablePageFlip"    "True"
    Option        "DMAForXv"        "True"
    Option        "AccelDFS"        "True"
    Option        "ColorTiling"        "True"
    Option        "RenderAccel"        "True"
    Option        "VGAAccess"        "True"
    Option        "AccelMethod"        "EXA"
    Option        "DRI"            "True"
    Option        "MigrationHeuristics"    "greedy"
    Option        "TripleBuffer"        "True"
    Option        "EXAOptimizeMigration"  "true"
    Option        "EXANoComposite"    "No"
    Option        "BackingStore"        "true"
    Option        "AGPMode"        "8"
    Identifier    "Card0"
    Driver        "radeon"
    VendorName    "ATI Technologies Inc"
    BoardName     "RV280 AP [Radeon 9200 PRO]"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Module"
    Load  "dri2"
    Load  "dri"
    Load  "dbe"
    Load  "extmod"
    Load  "glx"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    16
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option "RENDER" "Enable"
    Option "Composite" "True"
    Option "XVideo" "Enable"
    Option "XINERAMA" "False"
EndSection

Section "DRI"
    Mode        0666
EndSection

```
Give it a try, using your own figures for resolution and refresh rates, and you may find things are even better than at the moment.

---

### Post by clhsharky on 2010-07-19
ajgreeny

Nice xorg.conf file for ati 9200SE card with r200 driver. I have that card in a old server box with Hardy. Maybe now I'll update to Lucid and give it a try.

djk21108

If you try the xorg.conf file you will need to remove
> Option        "AGPMode"        "8"
You have a PCIX IGP chip
> BoardName     "RV515 [Mobility Radeon X1400]"

Sharky

---

### Post by djk21108 on 2010-07-19
Well I'm gonna give this a shot sharky. I have no xorg.conf file in my x11 folder as of now, but I created one per your instructions and customizations.

How do I move it from the desktop to x11?

---

### Post by djk21108 on 2010-07-19
Any hints guys? I don't think I have xorg installed or something. It's just not in that folder, and I can't move it there.

---

### Post by djk21108 on 2010-07-20
Sorry guys, You've been really helpful thus far, I just need a little help with this last point.

---

### Post by clhsharky on 2010-07-20
djk21108

I don't use a xorg.conf file and you shouldn't need one ether in Lucid.

Flash Optimization
[http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

I'd be more interested in you posting back your Xorg.0.log please wrap with code tags,its a lone file,to see if drivers are set up correctly.

Sharky

---

### Post by ajgreeny on 2010-07-20
Sharky's comment should be correct and you may not need an xorg.conf file.

However in the interests of your attempt to get things running better and as an exercise in how to copy things from place to place, you need to run the command ```
sudo cp /path/to/source/file /path/to/destination/folder/
``` which in your specific case will be ```
sudo cp Desktop/xorg.conf /etc/X11/
```
Note the / at the end of the X11 folder as without that the cp (copy) will not work.
You also need **sudo** as you can not copy files to any file system folders such as X11 without root privileges.

I also recommend you follow sharky's request for the xorg.0.log, and also do not use my example xorg.conf file without making the changes sharky noted, or you may be in trouble.

If for any reason you can not login to a GUI with that xorg.conf, login to the cli, then run ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.confbackup 
``` and then try again.  That command will rename the file as a backup, and you will be back to where you were.

---

### Post by gardelvis on 2010-07-24
HI Sharkey !!!

I'm having the same problem ( no hardware drivers list ) on Ubuntu Lucid 10.04 AMD 64 bits - I' ve got an NVIDIA GeForce 8200 Video card and since kernel update 2.6.32-23 that I have missed the Video Card Graphics Acceleration support. I have tried several solutions , but no hardware drivers are listed anymore . 

Would you help me ? 

Thanks in advance.

Gardelvis

---

### Post by clhsharky on 2010-07-24
gardelvis

Check in Synaptic Package manager that
nvidia-173-modaliases
nvidia-185-modaliases
is in stalled.
How did you install your NV drivers before kernel upgrade?

Sharky

---

### Post by gardelvis on 2010-07-24
Hi Sharky !!!

Now I have nvidia-173-modaliases installed also ( the other was preinstalled ) , but still no hardware controllers list.

In the past , I installed Nvidia modules via Hardware controllers and it displayed two options , and I selected the second which was the recommended nvidia driver - Since the kernel update , the system boots in low resolution mode for graphics and I 've got to uninstall nvidia at the first time that happened this. 
One of the solutions I took was to purge all nvidia packages ( nvidia*.* ) so I think maybe when I 've done this , something disappeared and produced this mess. 

Thanks very much for your reply.

Waiting anxiously for your answers...

Gardelvis

---

### Post by clhsharky on 2010-07-24
gardelvis

This is a Lucid fglrx thread.

Start a new thread
> Lucid nvidia, no hardware drivers 
So others can find and be included also.

Sharky

---

### Post by gardelvis on 2010-07-24
OK Sharky - I ' ll do it.

Thanks very much

Gardelvis

P.S: : The link to my new thread is [http://ubuntuforums.org/showthread.php?p=9632964#post9632964](http://ubuntuforums.org/showthread.php?p=9632964#post9632964)

---


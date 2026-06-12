---
title: "Need help with video driver problem when upgrading to 9.10"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by Crimson_Tider on 2009-11-08
Hey, guys.  I am having a big problem with upgrading to 9.10 Karmic.  When I try to boot into it normally, I get to a black screen with a totally white Ubuntu logo in the center (I guess that's normal so far) but then I get a flickering black screen with a login prompt. I can't login because the flickering won't let me type normally. I have to hit each key several times or hold down a key for exactly the right amount of time to input each letter of my login name, and then when it prompts me to enter the password, it's impossible because I can't see what I'm typing, so I can't see if or how many times my keystrokes are being recognized. There's no way for me to get to the desktop.

I have seen several people on here with this problem, but not many of them have the integrated graphics driver that I have, which is an Intel 82845G. I have deduced that I just need to download and install the driver for the graphics hardware, but I am unsure how to do that. I downloaded the driver, which is a file named i915Graphics.tar.gz, from the Intel website, put it on my USB flash drive, booted up my computer in recovery mode, went to a root shell command prompt, and mounted the flash drive. So what do I do from here to install the driver from this point?

By the way, I do need to include the fact that the driver is from 2004, so I'm not even sure this will work. I'm just trying to exhaust all other options before going through the trouble of backing up my home directory (which I don't know how to do this from a command prompt) and doing a clean install from a live CD.

Thanks for any help. Remember to be very specific and use very simple terms and explain thoroughly; I am still very much a newbie.

---

### Post by jbrown96 on 2009-11-08
The intel drivers changed substantially since 8.10. They moved into the kernel (which is a huge benefit) and changed the acceleration method. The problem was that they were really buggy in 9.04. You may have followed a guide to change to uxa (or is exa the new one? can't remember), and that is likely causing the problem. You won't need to download a new driver, but we need to reconfigure your graphics hardware to use the driver and methods that 9.10 fixed. Boot into recovery mode; there should be an option related to fixing graphics (or Xorg), choose that. If you can't find it, you can drop to a root shell and run ```
sudo dpkg-reconfigure --xorg-xserver
``` Both of these will take you through several menus. You can choose the default (just press enter) on almost all of them. The only thing you might want to change is the keyboard options, but if you use a standard US keyboard, then defaults are fine. Reboot ```
sudo reboot
``` and see if it's working any better.

---

### Post by Crimson_Tider on 2009-11-08
> **jbrown96 said:**
> The intel drivers changed substantially since 8.10. They moved into the kernel (which is a huge benefit) and changed the acceleration method. The problem was that they were really buggy in 9.04. You may have followed a guide to change to uxa (or is exa the new one? can't remember), and that is likely causing the problem. You won't need to download a new driver, but we need to reconfigure your graphics hardware to use the driver and methods that 9.10 fixed. Boot into recovery mode; there should be an option related to fixing graphics (or Xorg), choose that. If you can't find it, you can drop to a root shell and run ```
sudo dpkg-reconfigure --xorg-xserver
``` Both of these will take you through several menus. You can choose the default (just press enter) on almost all of them. The only thing you might want to change is the keyboard options, but if you use a standard US keyboard, then defaults are fine. Reboot ```
sudo reboot
``` and see if it's working any better.

Here are the results it gave me:
```
sudo dpkg-reconfigure --xorg-xserver
Unknown option: xorg-xserver
```

It then went on to list the valid options.

I figured you may have just committed a typo, so I tried
```
sudo dpkg-reconfigure xorg-xserver
```

and it gave me
```
Package 'xorg-xserver' is not installed and no info is available
```

---

### Post by jbrown96 on 2009-11-09
Hmmm, maybe that command is changed now. When you get into recovery mode, there is a list of things that you can fix. Try the graphics option. It's just an automated way to run that command.

---

### Post by Crimson_Tider on 2009-11-09
> **jbrown96 said:**
> Hmmm, maybe that command is changed now. When you get into recovery mode, there is a list of things that you can fix. Try the graphics option. It's just an automated way to run that command.

There isn't a graphics option. The listed options are

resume (Resume normal boot)
clean
dpkg (Repair broken packages)
grub
netroot
root

I chose dpkg. Then it said

rm: cannot remove 'var/lib/apt/lists/partial (I think I forgot to write down the rest of this line)

Then it went through an updating process, in which it downloaded a bunch of files and then gave me a command prompt. I typed startx (I had read somewhere on here that that is how you can go to the desktop). It gave me some general information about the operating system and then said

(EE) Failed to load module "intel" (module does not exist, 0)
(EE) No drivers available

Fatal server error:
 no screens found

Then it told me to consult The X.org Foundation support and it told me to check the log file at "/var/log/Xorg.0.log"

Then it said

xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error.

And it gave me a command prompt.

---

### Post by anewguy on 2009-11-09
Boot back into the terminal/command line, then type cat /var/log/Xorg.0.log | more and press enter.  Scan that output, pressing the space bar as needed to scroll down a page, for the fatal errors (I think they usually have three stars - "***").  Note down what the fatal errors say and post back here.

Dave :)

---

### Post by anewguy on 2009-11-09
Although I don't think it's getting far enough for this to be the problem, there used to be a problem with compiz and the 845, and perhaps it has carried forward.  Boot into a terminal/command line and type metacity --replace and press enter, then try rebooting to normal mode.

Dave :)

---

### Post by Crimson_Tider on 2009-11-09
> **anewguy said:**
> Boot back into the terminal/command line, then type cat /var/log/Xorg.0.log | more and press enter.  Scan that output, pressing the space bar as needed to scroll down a page, for the fatal errors (I think they usually have three stars - "***").  Note down what the fatal errors say and post back here.

Dave :)

The log file basically has two categories that sound like they may pertain to fatal errors--(WW) for warnings and (EE) for errors--so I will post both here. (II) is for information; I will post the ones of these that pertain to the errors and warnings given.

```
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
Entry deleted from font path.
.
(A bunch of loading modules and the like)
.
.
.
(II) LoadModule: "intel"
(WW) Warning, couldn't open module intel
(II) UnloadModule: "intel"
(EE) Failed to load module "intel" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult . . . support at . . . for help.
Please also check the log file (this same log file!) . . . for additional information.

ddxSigGiveUp: Closing log

(Then command prompt)


```

---

### Post by Crimson_Tider on 2009-11-09
> **anewguy said:**
> Although I don't think it's getting far enough for this to be the problem, there used to be a problem with compiz and the 845, and perhaps it has carried forward.  Boot into a terminal/command line and type metacity --replace and press enter, then try rebooting to normal mode.

Dave :)

```
metacity --replace
Window manager error: Unable to open X display
```

---

### Post by Thirtysixway on 2009-11-09
I also have driver issues, and now compiz isn't working after upgrading to 9.10.  I'll try to see if I can find those options when I get home today.

---

### Post by jbrown96 on 2009-11-09
From what I can remember, the module should not be named intel. I would try deleting /etc/X11/xorg.conf

---

### Post by Crimson_Tider on 2009-11-09
> **jbrown96 said:**
> From what I can remember, the module should not be named intel. I would try deleting /etc/X11/xorg.conf

Success!

Thanks jbrown96; deleting that file was all it took!

Now, I can finally get to the desktop and everything looks okay, but now I have another, though much smaller and much less serious, problem. I would like to enable desktop effects, but it won't let me. I get the response below (after going to Appearance, Visual Effects, and then clicking beside Normal)

```
Desktop effects could not be enabled.
```

I think I've seen somewhere that the responsible package is called compiz?

---

### Post by jbrown96 on 2009-11-09
3d may not be enabled on your system. I'm not exactly sure how to do it with Intel cards; it usually just works. Try running ```
glxgears
``` you may need to install a package called mesa-utils first. It should pop up a window with three gears rotating. If it doesn't work, then post the errors here; probably glx errors.

---

### Post by Crimson_Tider on 2009-11-09
> **jbrown96 said:**
> 3d may not be enabled on your system. I'm not exactly sure how to do it with Intel cards; it usually just works. Try running ```
glxgears
``` you may need to install a package called mesa-utils first. It should pop up a window with three gears rotating. If it doesn't work, then post the errors here; probably glx errors.

Works fine. I saw the little animation, and the terminal displayed this:

```
473 frames in 5.0 seconds
486 frames in 5.0 seconds
481 frames in 5.0 seconds
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 3837 requests (38 known processed) with 0 events remaining.

```

The fatal error didn't occur until I closed the window with the animation.

---

### Post by Crimson_Tider on 2009-11-10
Does anyone know where I can find an up-to-date driver for my video card? I'm pretty sure that's all I need because I ran compiz-check (from [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)) and it told me this:

```
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) y

```

And then it popped up the "Hardware Drivers" window, which told me
"No proprietary drivers are in use on this system."

---

### Post by jbrown96 on 2009-11-11
You don't need to install anything. You need to switch to the mesa driver. Open /etc/X11/xorg.conf and look for the driver section. change vesa to mesa.

---

### Post by Voxan2004 on 2009-11-11
Hi, guys.

I'm glad to find someone with the same problem as me. But as I am very green behind the ears as Linux is concerned, how do you delete the file /etc/X11/xorg.conf correctly?? Can someone post the command line, please?

Thanks a million,

Steve

---

### Post by Crimson_Tider on 2009-11-11
> **jbrown96 said:**
> You don't need to install anything. You need to switch to the mesa driver. Open /etc/X11/xorg.conf and look for the driver section. change vesa to mesa.

You had me delete that file in Post #11. What I have now in /etc/X11 is these:

xorg.conf.20090514210537
xorg.conf.dist-upgrade-200911010531
xorg.conf.failsafe
xorg.conf-backup-090514210034

And there is one hidden file:

xorg.conf~

It shows a filetype of backup for that one

xorg.conf.failsafe is the only one that mentions a driver at all, so should I just edit that one? Sounds like a "duh" question, I know, but I want to make sure.

---

### Post by jbrown96 on 2009-11-11
Sorry I firgured a new xorg.conf would be generated. Boot into recovery mode and go to a root shell. ```
Xorg -configure
``` This should generate a /etc/X11/xorg.conf. Reboot and post that.

---

### Post by Crimson_Tider on 2009-11-11
> **jbrown96 said:**
> Sorry I firgured a new xorg.conf would be generated. Boot into recovery mode and go to a root shell. ```
Xorg -configure
``` This should generate a /etc/X11/xorg.conf. Reboot and post that.

No, it didn't generate another one in that location, but I noticed in the output that it said

```
Your xorg.conf file is /root/xorg.conf.new
```

The contents of that file are below:

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri2"
	Load  "glx"
	Load  "dri"
	Load  "dbe"
	Load  "extmod"
	Load  "record"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

I have also attached a somewhat blurry photo of my computer screen after I ran Xorg -configure from the root shell. It looked like I might need to know some of that information later, and I didn't know how to save it to my hard drive.

---

### Post by jbrown96 on 2009-11-11
That file looks pretty good. You might need to copy it to /etc/X11/xorg.conf, but I'd try rebooting and see if it's working properly now. I was wrong earlier: intel is the correct driver. I looked through the release notes, and there isn't anything about problems with your chipset. That doesn't mean that it isn't a problem, but I think that it is a problem with your installation. It would probably be quicker to reinstall (~20 minutes) than keep trying to fix it. Just backup your home folder.

Upgrades always have the potential to have problems, especially with the substantial changes that 9.10 made to the intel graphics stack.

---

### Post by JBAlaska on 2009-11-11
I believe the intel 845g is on the Compiz blacklist. un-blacklisting results in system freeze.

---

### Post by Crimson_Tider on 2009-11-11
> **JBAlaska said:**
> I believe the intel 845g is on the Compiz blacklist. un-blacklisting results in system freeze.

I've heard that from some other people, too. I think I'll just do without desktop effects for now. I've spent too much time on this already. Thanks!

---


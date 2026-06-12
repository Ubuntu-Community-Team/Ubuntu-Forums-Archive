---
title: "Low Screen Resolution"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by Inhopeless on 2011-03-29
I have just installed Ubuntu 10.10 on my laptop, and the screen resolution appears to be set to 800x600 (4:3), however in Windows, it has a maximum of 1280x800 (16:10).

I've tried the following:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom 
sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/x11/xorg.conf.md5sum'    
sudo dpkg-reconfigure xserver-xorg

The first way, I get an error saying that the file cannot be found.

The second way, it simply doesn't work.

The third way, it just skips to the user@computer command line again.

Is there an alternative way?

My computer is an Ei-System 4213 with an intergrated Intel chipset.

Thank you in advance.

---

### Post by sanguinoso on 2011-03-29
Under System -> Monitors are you unable to set a resolution higher than 800x600?

---

### Post by Bölvaður on 2011-03-29
Look at the top panel on your desktop

System &#8594; Administration &#8594; Additional Drivers (might also be named something similar, like restricted hardware or or something to do with hardware and drivers)

Have you installed/enabled all those drivers? Specially that graphical one.


Like the poster above said: Check
System &#8594; Preferences &#8594; Monitors

---

### Post by seawolf167 on 2011-03-29
If you have the additonal drivers installed and are unable to change the resolution via the GUI way posted above, try this command (a slight variation on yours above, but this one only prompts for the display resolution, everything else is set to default values)

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

You can also pass the resolution if you know it with

```
xrandr -s 1280x1024
```

where 1280x1024 is your monitor's target resolution

---

### Post by Inhopeless on 2011-03-30
Okay, I've checked System > Pref. > Monitors. The largest resolution possible is 800x600.

I've checked Systems > Admin. > Additional Drivers, and it says "No proprietary Drivers Installed"

The coding way came up with 'enter password', I did correctly, but then it just comes up with nothing. I can't go out and change monitor (that not is expensive but also impractical as I have a laptop). Is there another option?

---

### Post by realzippy on 2011-03-30
If you are willing to run a few terminal commands,there *might* be a way.
This needs a little attention and might be disturbing when coming from windows.
So if:

Need more infos,so post output from
```
xrandr
```
and
```
lspci |grep VGA
```

---

### Post by matt_symes on 2011-03-30
Hi

A small typo RealZippy. I make many of them myself :D

```
lspci |grep VGA
```

Sounds like X is using fail safe mode.

Kind regards

---

### Post by realzippy on 2011-03-30
@matt_symes

thanks,edited post.
Can system boot to failsafe (recovery?) mode by itself? Wouldn't it inform about?
Thought about typical KMS failure..

---

### Post by matt_symes on 2011-03-30
Hi

> **realzippy said:**
> @matt_symes

thanks,edited post.
Can system boot to failsafe (recovery?) mode by itself? Wouldn't it inform about?
Thought about typical KMS failure..

Yes that is what i mean. A failure causing X to start in fail safe with no user intervention. Either 640x480 or 800x600 resolution as these are considered safe defaults for most graphics cards.

I will find a link and post it, but first i have a birthday party to go to :D .

Kind regards

---

### Post by fabricator4 on 2011-03-30
If the output from xrandr only shows low resolution modes then it seems like the EDID screen information is not being passed along correctly.  You can get around this by specifying vertical refresh and horizontal sync parameters in xorg.conf

---

### Post by realzippy on 2011-03-30
@ fabricator4

xorg.conf will not exist and we are in absolute beginner talk,so....

---

### Post by Inhopeless on 2011-03-30
I ran both commands and got:

xrandr: Failed to get size of gamma for output default
Screen 0: Minimum 640x480, current 800x600, maximum 800x600
default connected 800x600+0+0 0mmx0mm
800x600 61.0*
640x480 60.0

From the second command:

VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE
VGA Display Adapter (rev 10)

That's all I've gotten.

Thanks in advance.

---

### Post by davidmohammed on 2011-03-30
here is a very long [thread]("http://ubuntuforums.org/showthread.php?t=958967") - work from the last thread backwards - some suggested answers there for your graphics chipset.

---

### Post by fabricator4 on 2011-03-30
> **realzippy said:**
> @ fabricator4

xorg.conf will not exist and we are in absolute beginner talk,so....

That's OK, you can make the xorg.conf file. unfortunately I'm at work at the moment and this machine doesn't have the xorg.conf I need to give you. I'll do it tonight when I get home.

Chris

---

### Post by realzippy on 2011-03-31
Here is a solution that should work for you:

[http://ubuntuforums.org/showpost.php?p=9920147&postcount=568](http://ubuntuforums.org/showpost.php?p=9920147&postcount=568)

Which monitor model do you run?
(need to get H/V sync/refresh values to edit vanilla xorg.conf)


Edit.
feel free to ask if you have problems with that link..

---

### Post by fabricator4 on 2011-03-31
> **realzippy said:**
> @ fabricator4

xorg.conf will not exist and we are in absolute beginner talk,so....

OK, here's how to edit xorg.conf.  Open a terminal window and:

```

sudo gedit /etc/X11/xorg.conf

```

Note that the 'X' in X11 is a capital.  Capitalisation is important when dealing with the Linux files system. To avoid any confusion you can cut and past the command into the terminal window (use <ctrl><shift>v, or just press the center mouse button to paste into the terminal, or use the edit menu.)

Now past the following (which is my xorg.conf) into the file.

```

Section "Monitor"
	Identifier	"Samsung 1100p"
	Horizsync 30-110
	Vertrefresh 50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Samsung 1100p"
	Device		"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection


```

You'll want to change it to reflect your own system.  Note that the Horizontal sync and Vertical refresh figures will probably work fine to give you the extra modes, but you really should find out what the correct figures for your monitor are and use those.  You can find this out by googling for the specs, hopefully, or if you have a manual perhaps it will list them under the technical section.

Once you've saved this file, log out and log back in again, and you should be able to select different modes in Preferences/Monitors.

Chris.

---

### Post by realzippy on 2011-03-31
@ fabricator

Problem is not to create a xorg.conf.
This is made by **sudo Xorg -configure** after stopping X server.
Note that your suggested file has no "driver" line in the device section,
so the VESA driver would still be used,which will not give desired resolution.Also the Monitor section's Hsync/Vrefresh values should be the correct one for the plugged monitor;if it was a TFT panel your values are to high,which might give resolution options/refresh rates which might be
problematic for the display.
Above given link (which is the same as davidmohammed gave),has a valid driver for SIS graphics and a valid xorg.conf.

---

### Post by fabricator4 on 2011-03-31
> **realzippy said:**
> @ fabricator

Problem is not to create a xorg.conf.
This is made by **sudo Xorg -configure** after stopping X server.


Since xorg configuration was taken out of the installer and made a dynamic part of the kernel I've found the -configure has been left behind, and is increasing becoming less useful, or even relevant to particular problems.

> 
Note that your suggested file has no "driver" line in the device section,

I stand corrected. I was under the impression that the Sis modules now shipped with the kernal, and that it was not necessary to install or reference them in xorg.conf. That's the way xorg has been going for a few years now, and my understanding that the opensource drivers have been around and have been undergoing improvements since 7.04.

> Also the Monitor section's Hsync/Vrefresh values should be the correct one for the plugged monitor;if it was a TFT panel your values are to high,which might give resolution options/refresh rates which might be problematic for the display.


Of course, which is why I suggested he change the xorg.conf to be correct for his equipment?
> 

Above given link (which is the same as davidmohammed gave),has a valid driver for SIS graphics and a valid xorg.conf.

With all the great work that's been done on xorg I'm rather surprised Sis has been left out of the loop.  This reminds me very much of my first experience with Ubuntu...  Unfortunately.

Chris.

---


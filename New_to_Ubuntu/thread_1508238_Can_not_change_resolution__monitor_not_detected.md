---
title: "Can not change resolution / monitor not detected"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by Max1 on 2010-06-12
Hi,

I'm running ubuntu 10.04; I'm still new to this OS.  I've been doing some extensive searches over the past few days trying to get ubuntu to recognize my monitor (compaq CV535) or grant me the ability to change my resolution.  See, the problem is that when I go to System > Preferences > Monitors, I get this message, "Monitor: Unknown" and am limited to 800 x 600 resolution or lower.  This makes working on this system very difficult.  I've tried quite a few methods to get this to work, including modifying my xorg.conf file which currently looks like this:

```

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
    Modeline    "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798
        HorizSync       31-65
        VertRefresh     50-120
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
             SubSection      "Display"
                Depth           24
                Modes           "1024x768"
             EndSubSection
EndSection
```I correctly received a proper modeline using the vidtune command.  The following is in my xorg.0.log file:

```

(II) VESA(0): Supported established timings:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 1024x768@60Hz

(II) VESA(0): Configured Monitor: Using hsync range of 31.00-65.00 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-120.00 Hz
(II) VESA(0): Configured Monitor: Using maximum pixel clock of 60.00 MHz
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0):  Built-in mode "800x600"
(**) VESA(0):  Built-in mode "640x480"
(**) VESA(0): Display dimensions: (280, 210) mm
(**) VESA(0): DPI set to (72, 72)
(**) VESA(0): Using "Shadow Framebuffer"
```All searches are pointing to the same direction, which is a method that does not work for me.  Does anyone know how to solve this issue?  Thanks

---

### Post by halitech on 2010-06-12
what kind of video card are you using?

---

### Post by Max1 on 2010-06-12
Hi halitech,

I'm using XGI Volari Z9S 32MB on board Graphics.

---

### Post by halitech on 2010-06-12
only found 1 post (in Danish, thakn goodness for google translate) and it seems to indocate that you need to use the sis driver. SiS are very poor at providing support so don't expect miracles with this card. 

Try changing this:
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

```
to this
```
 Section "Device" 
	Identifier "Configured Video Device"
	Driver  "sis"
EndSection
 
```
Reboot and see what happens

---

### Post by Max1 on 2010-06-12
Hi halitech,

Thank you for your response.  There is some progress with that, but the problem persists.  Now when I boot up I get the following error message:

```

Ubuntu is running in low-graphics mode

The following error was encountered.  You may need to update your configuration to solve this.

(EE) No devices detected

```

the Xorg.0.log file reads as follows:

```

(II) LoadModule: "sis"
(II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
(II) Module sis: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.10.2
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
    SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
    SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
    SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
    SIS340
(II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
    Volari V3XT/V5/V8/Duo (XG40)
(II) Primary Device is: PCI 11@00:04:0
(WW) Falling back to old probe method for sis
(--) Assigning device section with no busID to primary device
(EE) No devices detected.

Fatal server error:
no screens found

```

---

### Post by halitech on 2010-06-12
ok, guess we might as well remove the driver line as it doesn't seem to be doing any good. Not sure what else to suggest from here as far as what to add to the xorg.conf file.

Is it possible to add an Nvidia video card? would be alot less work for you if possible. Not to mention would give you better graphics as you probably won't find one under 64meg nowadays.

---

### Post by Max1 on 2010-06-12
Before we call it quits; could it be the drivers themselves?  Maybe they are outdated.  The log file indicates that the drivers are for V3XT, V5, V8 and DUO.  Where as mine is of the Z7 Z9 Z9S series.  I did a few searches on sis drivers (thanks for pointing me in the right direction) and found a website which claims to have the sis drivers for my series (Italian website).  However, the file has a .rar extension and it seems I can't do anything with it.  How do I install these drivers?

---

### Post by halitech on 2010-06-12
you need to unrar the files and then see what is inside. Can you right click and extract here? then hopefully there will be a readme file with instructions.

---

### Post by Max1 on 2010-06-12
I can not.  I receive a notice that the archive type is not supported.  How do we use rar archives on ubuntu?  Upon further reading, it would seem that I need the sisfb drivers.  I tried simply changing sis to sisfb but I did not have the drivers installed on my ubuntu 10.04 distribution.

Also, I'm not sure if these drivers will work as they are intended for the windows platform and I can't seem to find a linux set of the sisfb drivers.

---

### Post by Max1 on 2010-06-12
I was able to unrar the package after installing unrar with the following command line:

sudo apt-get install unrar

However, my worries were confirmed as the files within the rar archive are of the Microsoft cabinet variety and do not work with Linux as far as I know.  The issue now is locating a version of sisfb that works on Ubuntu; but this is still not guaranteed to work, however it is a step further.  Do you, or anyone else, know where I can get a hold of these drivers?

Thanks

---

### Post by Max1 on 2010-06-12
Okay, I found a Linux version of the drivers I need (straight from the XGI website).  There are two issues that I have now.  One, I don't know if I'm running in 32 bit or 64 bit, how do I determine this?  Also, when I attempt to install the .run files I get the following:

ubuntu
cp: cannot create regular file '/etc/X11/.xorg.conf.xgi': Permission denied
Cannot open X11 installation path /user/X11R6/lib/modules/drivers.  Exit.
exit: 112: Illegal number: -1

How do I resolve this issue?

Any help would be greatly appreciated!

---

### Post by halitech on 2010-06-12
I think under System - Admin there should be something regarding about Ubuntu, it should tell you there what version you installed.

When you run the script you probably need to add sudo or gksudo if it starts a graphical app to give it root permission

---

### Post by Max1 on 2010-06-12
I was able to install the drivers using sudo however the new drivers did not solve my problem.  The sis drivers still do not recognize my Z9 on board chip and the system defaults to vesa.  As this is a webserver, we did not feel it necessary to purchase a video card.  It seems however that this is a problem that probably can not be solved save writing a new driver set that recognizes Z9.  How frustrating this situation is.

Regardless of the fact this issue was not solved; I greatly appreciate your time and help in this matter, halitech.  Based on the information you supplied I was able to conduct searches, gathering information that greatly expanded my knowledge of Ubuntu.

---

### Post by halitech on 2010-06-13
since you are using it for a webserver, why not install the ssh server and ebox and use that to configure and manage the box instead of a gui on the box itself?

---


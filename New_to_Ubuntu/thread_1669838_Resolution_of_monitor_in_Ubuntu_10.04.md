---
title: "Resolution of monitor in Ubuntu 10.04"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by chowdhury.indranil on 2011-01-18
Recently I had to reinstall ubuntu 10.04 again. After reinstalling, the resolution of the monitor has changed. My  monitor is DELL E178WFP, the optimal resolution is 1440x900, 60 hz, but currently the resolution is 1024x768 60 hz. This was not the case before re-installation. I had to reinstall because I had to replace the mother board of the computer. Please help.
Indranil.

---

### Post by chowdhury.indranil on 2011-03-25
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html/comment-page-2#comment-96479](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html/comment-page-2#comment-96479)
This helps me to solve the problem temporarily. Once I shut down the computer the resolution is again back to sub-optimal level. please help me to change the resolution of my monitor permanently. 
Indranil.

---

### Post by realzippy on 2011-03-25
Open system/settings/startup applications,hit "add":

Name :resolution (or whatever you want)
Command:

xrandr -s 1440x900

---

### Post by chowdhury.indranil on 2011-03-25
> **realzippy said:**
> Open system/settings/startup applications,hit "add":

Name :resolution (or whatever you want)
Command:

xrandr -s 1440x900
I just tried it. But the problem is still persisting, once i restart the computer, i am back to square one. Anyways, thank you.
Indranil.

---

### Post by realzippy on 2011-03-25
post output from

```
xrandr
```

and

```
lspci | grep  VGA
```

---

### Post by chowdhury.indranil on 2011-03-25
> **realzippy said:**
> post output from

```
xrandr
```

and

```
lspci | grep  VGA
```
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 2048 x 2048
VGA connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
  1440x900_60.00 (0xfb)  106.0MHz
        h: width  1440 start 1528 end 1672 total 1904 skew    0 clock   55.7KHz
        v: height  900 start  903 end  909 total  934           clock   59.6Hz

---

### Post by chowdhury.indranil on 2011-03-25
> **chowdhury.indranil said:**
> Screen 0: minimum 320 x 200, current 1360 x 768, maximum 2048 x 2048
VGA connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
  1440x900_60.00 (0xfb)  106.0MHz
        h: width  1440 start 1528 end 1672 total 1904 skew    0 clock   55.7KHz
        v: height  900 start  903 end  909 total  934           clock   59.6Hz
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

---

### Post by realzippy on 2011-03-25
run

```
gksudo gedit /etc/X11/xorg.conf

```
empty file opens (if not,stop here and post the output !)

paste in:


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
    Load  "extmod"
    Load  "record"
    Load  "dbe"
    Load  "dri"
    Load  "dri2"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "intel"
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

close file saving changes.
Reboot.
..if problems boot in recovery mode,log in at shell,run


```
sudo rm /etc/X11/xorg.conf
```


```
sudo reboot
```

or start low graphics session or kind of (have not been there for a while..)
and delete the file with file browser (nautilus):
/etc/X11/xorg.conf
and restart.

---

### Post by chowdhury.indranil on 2011-03-25
okay, i will do this now.

---

### Post by chowdhury.indranil on 2011-03-25
Followed the steps, faced problem in rebooting. booted in the recovery mode and did
sudo rm /etc/X11/xorg.conf
sudo reboot

---

### Post by realzippy on 2011-03-25
ok,used the xorg.conf from a formerly solved intel-resolution-problem.
So we need to create one on your machine:

1.**Write this down** since you won't be able to paste (mind capital "X"):
sudo service gdm stop
sudo Xorg -configure
sudo service gdm start

2.Press Alt+Ctrl+F2
A shell opens,log in with username&password
Type:

```
sudo service gdm stop
```

```
sudo Xorg -configure
```

a file xorg.conf.new should get created in your user's home folder.


```
sudo service gdm start
```

should bring you back.Post the content of created file,can use gedit:

```

gedit ~/xorg.conf.new
```

---

### Post by chowdhury.indranil on 2011-03-25
Okay, i will try this now.

---

### Post by chowdhury.indranil on 2011-03-25
okay I'm back.

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
	Load  "extmod"
	Load  "dbe"
	Load  "record"
	Load  "glx"
	Load  "dri"
	Load  "dri2"
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

---

### Post by realzippy on 2011-03-25
try this version now

```
gksudo gedit /etc/X11/xorg.conf
```

delete old content,paste in:

```
Section "ServerLayout"
Identifier "X.org Configured"
Screen 0 "Screen0" 0 0
InputDevice "Mouse0" "CorePointer"
InputDevice "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
ModulePath "/usr/lib/xorg/modules"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "built-ins"
EndSection

Section "Module"
Load "extmod"
Load "dbe"
Load "record"
Load "glx"
Load "dri"
Load "dri2"
EndSection

Section "InputDevice"
Identifier "Keyboard0"
Driver "kbd"
EndSection

Section "InputDevice"
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/input/mice"
Option "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
HorizSync       30.0 - 83.0
VertRefresh     56.0 - 75.0
EndSection

Section "Device"
Identifier "Card0"
Driver "intel"
VendorName "Intel Corporation"
BoardName "82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
BusID "PCI:0:2:0"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Card0"
Monitor "Monitor0"
SubSection "Display"
Viewport 0 0
Depth 1
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 4
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 8
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 15
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 16
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection
```

---

### Post by chowdhury.indranil on 2011-03-25
but there is no old content to delete
xorg.conf it is showing empty

---

### Post by realzippy on 2011-03-25
> **chowdhury.indranil said:**
> but there is no old content to delete
xorg.conf it is showing empty

sorry my mistake,off course empty since you deleted file formerly.Sorry.
Just paste in new content;
if it again does not boot,please check if you can remember the error message...

---

### Post by Grenage on 2011-03-25
Does this work, if used as your xorg.conf?  (Assuming you have no joy with realzippy's)

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Dell"
	ModelName "E178WFP"
	HorizSync 30 - 83
	VertRefresh 56 - 75
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "intel"
	VendorName "Intel 82845G"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1440x900"
	EndSubSection
EndSection
```

---

### Post by chowdhury.indranil on 2011-03-25
okay

---

### Post by chowdhury.indranil on 2011-03-25
> **Grenage said:**
> Does this work, if used as your xorg.conf?  (Assuming you have no joy with realzippy's)

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Dell"
	ModelName "E178WFP"
	HorizSync 30 - 83
	VertRefresh 56 - 75
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "intel"
	VendorName "Intel 82845G"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1440x900"
	EndSubSection
EndSection
```
Thank you very much. the resolution is perfect now.
Ubuntu and its are BEST.
I am very happy.
Indranil.

---

### Post by chowdhury.indranil on 2011-03-25
> **realzippy said:**
> sorry my mistake,off course empty since you deleted file formerly.Sorry.
Just paste in new content;
if it again does not boot,please check if you can remember the error message...
Thank you very much for helping me with this for so long. The resolution after rebooting is perfect. I am very happy. You people are great. Thank you.
Indranil.

---

### Post by Grenage on 2011-03-25
Adding the modeline 'usually' helps with a lot of these Intel issues; unfortunately it pretty much hard-sets your resolution and refresh rate.  It's not normally a problem (people rarely use anything but the native res), but it's worth bearing in mind.

---

### Post by realzippy on 2011-03-25
@ grenage

 still wondering why 1rst/2nd version refuses to boot.Caused by the
 "modules" section ?
AFAIK it should at least boot without the modeline..

---

### Post by Grenage on 2011-03-25
> **realzippy said:**
> @ grenage

 still wondering why 1rst/2nd version refuses to boot.Caused by the
 "modules" section ?
AFAIK it should at least boot without the modeline..

I agree, and I'm not sure why it doesn't; I'm guessing the xorg logs might give an indication - the modules shouldn't be a problem.  I'm not that knowledgeable when it comes to the settings, but find that a config with the bare essentials often works with a modeline; the system picks up the rest on its own.

I've never used the *viewport* settings before, do you prefer them over the *modes* option?

---

### Post by realzippy on 2011-03-25
@ indranil

If you have some time,can you please test if grenage's xorg.conf
file works without that modeline?
It might be interesting for the future when helping others...

First backup the file

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.grenage


```

then open it:

```
gksudo gedit /etc/X11/xorg.conf
```

and put a "#" in front of the modeline,so it looks like


```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Dell"
	ModelName "E178WFP"
	HorizSync 30 - 83
	VertRefresh 56 - 75
#Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
EndSection
```

close file saving changes.
reboot...
If it does not work,you'll get your old version back by:

```
sudo cp /etc/X11/xorg.conf.grenage /etc/X11/xorg.conf
```

---

### Post by chowdhury.indranil on 2011-03-25
> **realzippy said:**
> @ indranil

If you have some time,can you please test if grenage's xorg.conf
file works without that modeline?
It might be interesting for the future when helping others...

First backup the file

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.grenage


```

then open it:

```
gksudo gedit /etc/X11/xorg.conf
```

and put a "#" in front of the modeline,so it looks like


```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Dell"
	ModelName "E178WFP"
	HorizSync 30 - 83
	VertRefresh 56 - 75
#Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
EndSection
```

close file saving changes.
reboot...
If it does not work,you'll get your old version back by:

```
sudo cp /etc/X11/xorg.conf.grenage /etc/X11/xorg.conf
```
Okay, I will try this.
Indranil.

---

### Post by realzippy on 2011-03-25
@ grenage

*I've never used the viewport settings before, do you prefer them over the modes option?*

Think (do not know exactly)the viewport settings are obsolete here,since it is only relevant when using a virtual screen resolution.
Also think the "modes option" might be important here,since if there are no modes specified,system uses VESA standard modes,and think 1440x900 is no VESA standart mode,but may be wrong.

---

### Post by Grenage on 2011-03-25
> **realzippy said:**
> @ grenage

*I've never used the viewport settings before, do you prefer them over the modes option?*

Think (do not know exactly)the viewport settings are obsolete here,since it is only relevant when using a virtual screen resolution.
Also think the "modes option" might be important here,since if there are no modes specified,system uses VESA standard modes,and think 1440x900 is no VESA standart mode,but may be wrong.

I think you may well be onto something there:

[QUOTE=xorg man]This is an optional multi-line entry that can be used to provide definitions for video modes for the monitor. In most cases this isn't necessary because the built-in set of VESA standard modes will be sufficient[/QUOTE]

The VESA standard modes end with:

320x200, 640x400, 640x480, 800x600, 1024x768, 1280x1024

---

### Post by chowdhury.indranil on 2011-03-25
Now a new problem. The resolution is perfect. But after booting the icon or Arrow sign of the mouse is not showing. I had to hard shut down the PC many times. Then I booted from one of the previous kernel from the grub and thus I am writing this. Without the mouse icon the computer is useless to me. I have lots of work to do tomorrow. By now it must be obvious to you that I am only an ordinary user who knows almost nothing about the workings of the system. Please help me to solve this problem.
Indranil.

---

### Post by realzippy on 2011-03-25
...since you tested the modeline thing ("#") I have asked for?

If so,post your xorg.conf please.Or hasn't the mouse ever be working since resolution was ok?

---


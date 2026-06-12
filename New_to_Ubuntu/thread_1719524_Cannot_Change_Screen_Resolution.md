---
title: "Cannot Change Screen Resolution"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by unknowngal on 2011-04-01
Hello! I'm pretty much a total newbie and newcomer to Ubuntu. I'm willing to learn about it though. :) Like the title says, I can't seem to change the screen resolution, it's stuck to 1600 x 1200, which makes things so incredibly small that I have to squint and lean into the screen to read what I'm typing here. :P I tried doing something I found online dealing with the Terminal, but I got a blank window, no information in it. Umm. Hopefully I didn't ruin anything. *sheepish* I appreciate any help sent my way, and thank you!! :D

---

### Post by Phil D. on 2011-04-01
So do you have a Desktop or a Terminal now?

If desktop screen resolution, can normally be changed under "Monitors".
If terminal run 'sudo dpgk-reconfigure xserver-xorg -phigh' to restore defaults.

---

### Post by unknowngal on 2011-04-02
> **Phil D. said:**
> So do you have a Desktop or a Terminal now?

If desktop screen resolution, can normally be changed under "Monitors".
If terminal run 'sudo dpgk-reconfigure xserver-xorg -phigh' to restore defaults.

I tried entering that command in the Terminal and it said "command not found". As I said, I'm really a newbie, so any step by step info would be much appreciated! :)

---

### Post by unknowngal on 2011-04-02
Sorry if this problem has been brought up before, but I've been looking around on the forums and I haven't found a clear response to this issue yet. Maybe I'm looking in the wrong areas, I don't know. ^^;; But thanks for any help sent my way!

---

### Post by matt_symes on 2011-04-02
Hi

Open a terminal and type

```
sudo dpkg-reconfigure xserver-xorg -phigh
```

Enter your password. It will not be echoed to the screen.

There was a small typo in it. That will reconfigure your X server. 

If that does not fix it type...

```
xrandr
```

Copy and paste the results back here.

Kind regards

---

### Post by unknowngal on 2011-04-02
> **matt_symes said:**
> Hi

Open a terminal and type

```
sudo dpkg-reconfigure xserver-xorg -phigh
```Enter your password. It will not be echoed to the screen.

There was a small typo in it. That will reconfigure your X server. 

If that does not fix it type...

```
xrandr
```Copy and paste the results back here.

Kind regards

I didn't get anything by typing the first line into Terminal, but I did get this when I typed in that second line, xrandr:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1600 x 1200, current 1600 x 1200, maximum 1600 x 1200
default connected 1600x1200+0+0 0mm x 0mm
   1600x1200       0.0*

---

### Post by xXNI4NI on 2011-04-02
What distro are you using (10.04, 10.10)?
I believe the process is the same but I'll try and break it down really easy like. But first things first, welcome to Ubuntu!
Navigate your way to System->Preferences->Monitors.
You can try various resolutions from here that fit your liking. 
If you know the resolution you're looking for and it is not listed try following this guide for adding undetected resolutions.
[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions")
Not sure if that's useful but to save time I'll give you some tips that helped me.
You'll need to know the name of your output, found typing ```
xrandr
``` in the terminal. Assuming you have only one monitor connected it should show up here. Something along the lines of VGA1.
Knowing your output you should be able to follow the guide I linked.
Sorry if this doesn't help but please let me know.

---

### Post by xXNI4NI on 2011-04-02
> **unknowngal said:**
> I didn't get anything by typing the first line into Terminal, but I did get this when I typed in that second line, xrandr:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1600 x 1200, current 1600 x 1200, maximum 1600 x 1200
default connected 1600x1200+0+0 0mm x 0mm
   1600x1200       0.0*

Sounds to me like driver issues? Have you installed proper drivers? Matt may be able to provide insight but have one resolution with the output named "default" doesn't seem right.

---

### Post by matt_symes on 2011-04-02
Hi

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1600 x 1200, current 1600 x 1200, maximum 1600 x 1200
default connected 1600x1200+0+0 0mm x 0mm
1600x1200 0.0*
```

It looks like it's not reading your monitors EDID info correctly so Ubunutu does not know the resolutions it supports.

The link by xXNI4NI above me is a good introduction to changing screen resolutions by hand using the terminal.

If you need a hand post back.

Kind regards

---

### Post by unknowngal on 2011-04-02
> **xXNI4NI said:**
> Sounds to me like driver issues? Have you installed proper drivers? Matt may be able to provide insight but have one resolution with the output named "default" doesn't seem right.

I'm not 100% sure, regarding the drivers, the monitor's always worked well, at least on Windows XP. If it helps any, it's a Futura monitor, probably purchased in 1999, so it's pretty old. ^^;; But I do remember updating the drivers sometime ago.

---

### Post by unknowngal on 2011-04-02
> **xXNI4NI said:**
> What distro are you using (10.04, 10.10)?
I believe the process is the same but I'll try and break it down really easy like. But first things first, welcome to Ubuntu!
Navigate your way to System->Preferences->Monitors.
You can try various resolutions from here that fit your liking. 
If you know the resolution you're looking for and it is not listed try following this guide for adding undetected resolutions.
[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions)
Not sure if that's useful but to save time I'll give you some tips that helped me.
You'll need to know the name of your output, found typing ```
xrandr
``` in the terminal. Assuming you have only one monitor connected it should show up here. Something along the lines of VGA1.
Knowing your output you should be able to follow the guide I linked.
Sorry if this doesn't help but please let me know.

I'm using 10.10 by the way. :) And thanks for the welcome! :D I just wanted to try it on a whim and I really like it so far. :) *likes variety* And I'll try that link you gave me!

---

### Post by unknowngal on 2011-04-02
Okay, I tried this link: [https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions)

I tried the first line, but this is what I got:

$ xrandr --addmode $-video 1024x768
xrandr: Failed to get size of gamma for output default
xrandr: cannot find output "himBHvideo"

And the second line gave me this:

$ xrandr --newmode <Mode''Line>
bash: syntax error near unexpected token `newline'

---

### Post by matt_symes on 2011-04-02
Hi

Open a terminal and type

```
cvt 1024 768
```

That will produce an output like this.

```
matthew@matthew-laptop:~$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline **"1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync**
matthew@matthew-laptop:~$ 
```

Take the bold line above and enter the command below changing the bold line to match the one found above if required. Not sure if i explained that very well.

```
xrandr --newmode **"1024x768_60.00" 63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync**
```

That should create the new mode. Next we need to change to that new mode.

```
xrandr --addmode VGA1 1024x768
```

You may have to change VGA1 if it is not correct on your system. If that works we need to make it persistent.

Kind regards

---

### Post by unknowngal on 2011-04-02
> **matt_symes said:**
> Hi

Open a terminal and type

```
cvt 1024 768
```That will produce an output like this.

```
matthew@matthew-laptop:~$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline **"1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync**
matthew@matthew-laptop:~$ 
```Take the bold line above and enter the command below changing the bold line to match the one found above if required. Not sure if i explained that very well.

```
xrandr --newmode **"1024x768_60.00" 63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync**
```That should create the new mode. Next we need to change to that new mode.

```
xrandr --addmode VGA1 1024x768
```You may have to change VGA1 if it is not correct on your system. If that works we need to make it persistent.

Kind regards

Okies, I tried those steps, and I got this:

xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr: Failed to get size of gamma for output default
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  19
  Current serial number in output stream:  19

I hope I'm not doing anything wrong. x__x;

---

### Post by realzippy on 2011-04-02
Think we solved the same problem here:

[http://ubuntuforums.org/showthread.php?t=1713043](http://ubuntuforums.org/showthread.php?t=1713043)

Feel free to ask for help concerning this..
...............................................
**Edit**:

You can test the xrandr thing before (which matt_symes suggested)
which would be :
```
xrandr --newmode "1024x768_60.00" 63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
```

```
xrandr --addmode default 1024x768
```

```
xrandr -s 1024x768
```

..but as he claimed you had to make it permanent (if it works),and creating a xorg.conf was a permanent solution.

---

### Post by unknowngal on 2011-04-02
> **realzippy said:**
> Think we solved the same problem here:

[http://ubuntuforums.org/showthread.php?t=1713043](http://ubuntuforums.org/showthread.php?t=1713043)

Feel free to ask for help concerning this..
...............................................
**Edit**:

You can test the xrandr thing before (which matt_symes suggested)
which would be :
```
xrandr --newmode "1024x768_60.00" 63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
``````
xrandr --addmode default 1024x768
``````
xrandr -s 1024x768
```..but as he claimed you had to make it permanent (if it works),and creating a xorg.conf was a permanent solution.

I tried it, and I got this after typing in 
[FONT=monospace]
[/FONT]gedit ~/xorg.conf.new[FONT=monospace]

[/FONT]Section "ServerLayout"
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
    Load  "dri"
    Load  "dri2"
    Load  "extmod"
    Load  "record"
    Load  "glx"
    Load  "dbe"
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
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
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

---

### Post by unknowngal on 2011-04-02
> **realzippy said:**
> Think we solved the same problem here:

[http://ubuntuforums.org/showthread.php?t=1713043](http://ubuntuforums.org/showthread.php?t=1713043)

Feel free to ask for help concerning this..
...............................................
**Edit**:

You can test the xrandr thing before (which matt_symes suggested)
which would be :
```
xrandr --newmode "1024x768_60.00" 63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
``````
xrandr --addmode default 1024x768
``````
xrandr -s 1024x768
```..but as he claimed you had to make it permanent (if it works),and creating a xorg.conf was a permanent solution.

Hmm, I got this after typing the above lines:

xrandr --newmode "1024x768_60.00" 63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr: Failed to get size of gamma for output default

xrandr --addmode default 1024x768
xrandr: Failed to get size of gamma for output default
xrandr: cannot find mode "1024x768"

---

### Post by realzippy on 2011-04-02
Ok,now we need to know your monitor model.
(for the correct H/V Sync/refresh values)
..and make sure you know how to start recovery mode if anything goes wrong..

---

### Post by unknowngal on 2011-04-02
> **realzippy said:**
> Ok,now we need to know your monitor model.
(for the correct H/V Sync/refresh values)
..and make sure you know how to start recovery mode if anything goes wrong..

How do I check for my model number? *apologizes for the newbieness* x__x

---

### Post by realzippy on 2011-04-02
Just tell me the "name" (model) of the monitor...
should be printed somewhere on it's case..will find the values for you.

---

### Post by unknowngal on 2011-04-02
> **realzippy said:**
> Just tell me the "name" (model) of the monitor...
should be printed somewhere on it's case..will find the values for you.

It's a Futura monitor, model K7034LD

---

### Post by realzippy on 2011-04-02
run

```
gksudo gedit /etc/X11/xorg.conf
```

empty file opens (if not,stop here and post the output !)

paste in:

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
Load "dri"
Load "dri2"
Load "extmod"
Load "record"
Load "glx"
Load "dbe"
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
HorizSync       30.0 - 95.0
VertRefresh     50.0 - 160.0
EndSection

Section "Device"
Identifier "Card0"
Driver "intel"
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

close file saving changes.
Reboot.
Hopefully you now have a bunch of resolutions to choose from in System/settings/Monitors..........

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

### Post by unknowngal on 2011-04-02
> **realzippy said:**
> run

```
gksudo gedit /etc/X11/xorg.conf
```empty file opens (if not,stop here and post the output !)

paste in:

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
Load "dri"
Load "dri2"
Load "extmod"
Load "record"
Load "glx"
Load "dbe"
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
HorizSync       30.0 - 95.0
VertRefresh     50.0 - 160.0
EndSection

Section "Device"
Identifier "Card0"
Driver "intel"
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
```close file saving changes.
..if problems boot in recovery mode,log in at shell,run

```
sudo rm /etc/X11/xorg.conf
``````
sudo reboot
```or start low graphics session or kind of (have not been there for a while..)
and delete the file with file browser (nautilus):
/etc/X11/xorg.conf
and restart.

It gave me this instead of a blank file:

Section "Screen"
    Identifier    "Configured Screen Device"
    Device    "Configured Video Device"
    SubSection "Display"
        Virtual    2048 2048
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

---

### Post by realzippy on 2011-04-02
never mind,**delete the existing content** so file is blank before pasting in suggested.

---

### Post by unknowngal on 2011-04-02
> **realzippy said:**
> never mind,**delete the existing content** so file is blank before pasting in suggested.

Holy moly. o__o I don't know HOW it worked, but it did. THANK YOU!!! I am SO bookmarking this and keeping it for future reference. THANK YOU AGAIN!!! :D

---

### Post by realzippy on 2011-04-02
*I don't know HOW it worked, but it did.*

...because we feed the video driver with correct monitor data in the created file.

Please set thread as solved (threadtools)
Have fun


edit:
If you now would connect a different monitor,especially a TFT panel,
this will work,but you would get resolutions/refresh rates available the different panel could not handle or even damage it.So if you ever change the monitor,disable
(rename) the file or edit the proper H/Vsync values for the new monitor.

---


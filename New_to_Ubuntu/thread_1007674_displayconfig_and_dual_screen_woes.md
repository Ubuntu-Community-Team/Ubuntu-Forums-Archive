---
title: "displayconfig and dual screen woes"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by Darth_Maga on 2008-12-10
Hello!!
ubuntu 8.04
Can anyone give me a hand? I trying to get a dual screen setup with a laptop and a screen through displayconfig. When executing
sudo displayconfig-gtk    I get this
Error: "/var/tmp/kdecache-diego" is owned by uid 1000 instead of uid 0. 
Reusing existing ksycoca 
DCOP Cleaning up dead connections. 
Error: "/var/tmp/kdecache-diego" is owned by uid 1000 instead of uid 0. 
Error: "/var/tmp/kdecache-diego" is owned by uid 1000 instead of uid 0. 
after that
the laptop screen stays in 1200x800 and gets skinny fonts and the 2nd screen gets 640x480.
displayconfig will not let you change these resolutions

wont work without the sudo either

It would be nice to get displayconfig to work b4 trying to edit xorg.conf
(I have tried but.....)

Am i going to mess up something if I change the directory ownership?

---

### Post by roger_1960 on 2008-12-10
Hi

Try

gksu displayconfig-gtk

instead of sudo ...

---

### Post by Darth_Maga on 2008-12-12
In the meantime if it can help anyone, I have edited xorg.conf and it works, but its not perfect

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
        Identifier      "0 Intel 945GM"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Screen      0
        Option          "MonitorLayout" "CRT,LFP"
        Option          "DRI" "false"
    # I don't think these next lines are actually required.
    #Option          "BackingStore" "true"
    #Option          "DevicePresence" "on"
    #Option          "DisplayInfo" "FALSE"
    #Option          "DRI" "true"
    #Option                       "CacheLines" "1024"
EndSection

Section "Device"
        Identifier      "1 Intel 945GM"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Screen      1
        Option          "MonitorLayout" "CRT,LFP"
        Option          "DRI" "true"
    # I don't think these next lines are actually required.
    #Option          "BackingStore" "true"
    #Option          "DevicePresence" "on"
    #Option          "DisplayInfo" "FALSE"
    #Option          "DRI" "true"
    #Option                       "CacheLines" "1024"
EndSection

Section "Monitor"
        Identifier      "0 nc2400 Monitor"
        Option          "DPMS"
        Option          "DPMS"
#       HorizSync       31.47 - 128.52
#       VertRefresh     59.9 - 128.52
EndSection

Section "Monitor"
        Identifier         "1 nc2400 Monitor"
    HorizSync      30 - 83
    VertRefresh    56 - 75
    Option         "DPMS"
        Modeline       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection


Section "Screen"
        Identifier          "0 Screen"
        Device              "0 Intel 945GM"
        Monitor             "0 nc2400 Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "Screen"
        Identifier          "1 Screen"
        Device              "1 Intel 945GM"
        Monitor             "1 nc2400 Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024@60"
        EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen      0 "0 Screen"
    	Screen      1 "1 Screen" LeftOf "0 Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

I got the info from here

[http://blog.dotkam.com/2007/05/18/dual-monitor-on-ubuntu-704-feisty-fawn-nc2400-with-intel-945gm/](http://blog.dotkam.com/2007/05/18/dual-monitor-on-ubuntu-704-feisty-fawn-nc2400-with-intel-945gm/)

You do not get an extended desktop, but 2 desktops
Visual effects dont work

If you want to work just with the laptop monitor you keep losing the mouse pointer to the left, where the other screen should be, and you can cant go back to 1 monitor without editing xorg.conf (or connecting a projector or anything)

btw gksudo doesnt work with displayconfig either

any suggestions anyone?

---


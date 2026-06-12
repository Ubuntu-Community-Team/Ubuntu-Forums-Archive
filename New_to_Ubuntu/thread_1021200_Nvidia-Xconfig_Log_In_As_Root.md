---
title: "Nvidia-Xconfig Log In As Root"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by tkelito on 2008-12-25
I have a 7200GS Nvidia Graphics card and I am running Ubuntu 8.04.  I cannot get it to work with VGA + S-Video for my TV to hookup.  I can get both monitors running, but only with a max resolution of 800x600.  I can get my single 22" LCD running at 1680x1050, but only if the TV is not working properly.

If I attempt to use Nvidia-Settings I get the Nvidia-Xconfig needs to be run as root and then Ctrl-Alt-Backspace to restart the xServer. I follow the steps, login as root, run it, no avail.

I have spent the better part of the last 6 hours attempting multiple combinations and reading poor/outdated documentation.  Previously my xorg.conf did have all the resolutions/refresh rates listed, now after installing the "Proprietary Hardware" they have disappeared.


This is my current xorg.conf:

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"False"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

---

### Post by tkelito on 2008-12-25
So if I enter the synaptic package manager and install nvidia-xconfig I can get my xorg.conf to look like this:

```


Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    Screen      1  "screen1" LeftOf "Default Screen"
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "true"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1680x1050"
    HorizSync       31.5 - 65.5
    VertRefresh     56.0 - 65.0
    Gamma           1
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    ModeLine       "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
    ModeLine       "1600x1024@60" 136.4 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
    ModeLine       "1680x1050@60" 147.1 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
EndSection

Section "Monitor"

 # 
    Identifier     "monitor1"
    VendorName     "Generic CRT Display"
    ModelName      "Monitor 800x600"
    HorizSync       31.5 - 35.1
    VertRefresh     50.0 - 61.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 7 Series"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Device"

 # 
    Identifier     "device1"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 7 Series"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050@60" "1600x1024@60" "1440x900@60" "1280x800@60" "1280x720@60" "1280x768@60" "800x600@60" "800x600@56"
    EndSubSection
EndSection

Section "Screen"

 # 
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "800x600@56" "640x480@60"
    EndSubSection
EndSection


```

I still cannot access the nvidia-settings, it still says I am not running the nvidia-xconfig when it is installed.

Still unsure where to go. Any help is greatly appreciated.

---

### Post by Amazona aestiva on 2008-12-25
Greetings,

I don't know xorg.conf so well, but here's mine, and I can enter nvidia-settings with it. (also got S-Video work) It may help.
By th way I have a GeForce 7300GS

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"hu"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

Regards

---

### Post by tkelito on 2008-12-25
Thanks for the quick response, I still have yet to get nvidia-settings to work.. I have also yet to go to sleep... lucky for me I have Christmas to myself with no one around to disturb.

Anyways, even if I use your config I am still not using the nvidia-xconfig and hence it renders me unable to use nvidia-settings.

Anyone who can give me a specific 1 - 2 - 3 order of operations for post OS install loading of the graphics drivers so that I can configure nvidia-settings to work appropriately would be very helpful.  I have swapped settings around so much and installed/uninstalled so many drivers I am contemplating doing another reload of the OS.

Once again I greatly appreciate any help anyone can offer to me.

::EDIT::

```

tkelito@MBOX:~$ lshw -C display
WARNING: you should run this program as super-user.
PCI (sysfs)
 *-display UNCLAIMED
      description: VGA compatible controller
      product: G72 [GeForce 7300 SE]
      vendor: nVidia Corporation
      physical id: 0
      bus info: pci@0000:02:00.0
      version: a1
      width: 64 bits
      clock: 33MHz
      capabilities: vga_controller bus_master cap_list
      configuration: latency=0

```

Thought I would add in that output from terminal if it can help yield me a response.

Thanks!

---


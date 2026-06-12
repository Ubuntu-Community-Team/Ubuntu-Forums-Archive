---
title: "New monitor, graphics driver does not supprt?"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by themis on 2009-05-04
Hello,

I need some guidance to use my new monitor,
instead of the laptop's monitor.
I've connected it, searched at this forum and at the help center,
but nothing answered my question.

When I go to System-> Preferences-> Display, I get a message
"It appears that your graphics diver does not support the necessary extensions to use this tool.
Do you want to use your graphics driver vendor's tool instead?"

and then I have "Monitor:unknown"

What can I do?
I don't want dual use, just want to use the new one.

 Thank you.

---

### Post by LowSky on 2009-05-04
on the keyboard there are some keys (usually in Blue) the need the Function key to work (Fn on the keyborad, next to CTRL and ALT)

SO hold FN and press the key with the label that looks like a square box or monitor, it should switch to your other monitor

---

### Post by jbrown96 on 2009-05-04
It depends on your graphics card. Intel and some AMD cards can use the native display manager. Nvidia and most AMD cards need their own graphics manager. I think for the AMD cards you will have to manually install their driver (could someone else verify?). It's fairly easy. Go to their website, and download the driver. You can install it with ```
sudo sh ./Desktop/ati...
``` If that doesn't work, try it without sh. For an Nvidia card, install nvidia-settings. ```
sudo apt-get install nvidia-settings
``` You will be able to find the applications in your Applications menu: Catalyst (AMD) is located right on this menu, Nvidia-settings is in System tools.

---

### Post by themis on 2009-05-04
1) The Fn key method doesn't work

2)I have N-vidia Ge Force FX,

and when I tried on a previous distribution to install them,
the result was a grey screen.
Other people had this problem too, so I can't install these.

Is there a possibility for the drivers to be working well at this distribution?

What else c****an I do?

---

### Post by razy60 on 2009-05-04
what laptop and what Graphics card is it (geforce fx ???)
are you dual booting with windows or do you only have 9.04 loaded? If you are dual booting does it work in windows? or can you try with another earlier version, 8.10 maybe!
Some laptops need the external monitor activated in bios first.

Raz

---

### Post by themis on 2009-05-04
I am on Toshiba m200, and
 the graphics card is nVidia geForce FX Go 5200.

Yes I am dual booting with Windows and it worked ok with WIndows.
But I don't se often Windows, cause I don't want to except some cases
when I need  special programs.

---

### Post by themis on 2009-05-04
nvidia-setings is installed, just found out!

but I still when I go to System-> Preferences-> Display, I get a message
"It appears that your graphics diver does not support the necessary extensions to use this tool.
Do you want to use your graphics driver vendor's tool instead?"

what does this mean, and what is the vendor's tool?

Does it help a bit now?
How can I switch to the external monitor? Or enable it through the bios forst?

AT BIOS-> Display there are 2 options
1. Power On : a. Auto Selected (on now), b. LCD+Analog RGB, c. System LCD only
2. LCD Display Stretch: a. Enabled(on now) b. Disabled

I don't think I should change something here.Tell me if I am wrong please!

---

### Post by NESFreak on 2009-05-04
> **themis said:**
> nvidia-setings is installed, just found out!

but I still when I go to System-> Preferences-> Display, I get a message
"It appears that your graphics diver does not support the necessary extensions to use this tool.
Do you want to use your graphics driver vendor's tool instead?"

what does this mean, and what is the vendor's tool?

Does it help a bit now?
How can I switch to the external monitor?

your vendors own tool is the program called "nvidia x server settings" which allows you to add monitors, change resolution and stuff. Which is good, since for nvidia cards it does the trick way better than ubuntus own manager, which is why it asks you "hey youve got a way better tool for this, dont you wanna use that one?"

---

### Post by themis on 2009-05-04
Ok!
 so how this display device be configured?
1. Disabled (present state)
2. Separate X screen (requires X restart)
3, Twin View

When I choose "separate X screen" it shows up a message 'cannot apply'.
I have a screenshot attached. Also I can't find how to disable the laptops screen.
MAybe the screenshot can help

---

### Post by jbrown96 on 2009-05-04
If you launch the program normally, then any changes will be forgotten after a reboot. It also has a timeout (~15 seconds) that it will revert back if you choose something that doesn't work. 

Once you get your settings right. Close nvidia-settings and reopen by presing Alt+F2 then ```
gksu nvidia-settings
``` Make your changes then choose to save configuration to your xorg.conf. From now on, if the monitor is connected before the system boots, it will automatically use your external monitor, otherwise the laptop lcd will be active.

---

### Post by themis on 2009-05-04
I get this error when I try to apply changes 
'Failed to set MetaMode (1) 'CRT-0: 1920x1080 @1920x1080 +0+0' (Mode 1920x1080, id: 0) on X screen 0'

???

---

### Post by themis on 2009-05-05
So after some experiments, 
I attach 3 xorg.conf files I've tried

**xorg.conf_backup**  this is my present state, working with the laptops monitor
```
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"us"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"	"/dev/psaux"
#	Option		"Protocol"	"auto-dev"
#	Option		"HorizEdgeScroll"	"0"
#EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
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
# commented out by update-manager, HAL is now used
#	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

**without_present**     this is how the pc works with its monitor switched off (I hear the login screen)
```
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"us"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"	"/dev/psaux"
#	Option		"Protocol"	"auto-dev"
#	Option		"HorizEdgeScroll"	"0"
#EndSection

Section "ServerLayout"
# commented out by update-manager, HAL is now used
#	Inputdevice	"Synaptics Touchpad"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "EIZO S1901"
    HorizSync       24.0 - 80.0
    VertRefresh     50.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX Go5200 32M/64M"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```


**eizos**    this is how theoretically the new screen should work. It is created automatically by the NVidia settings configuration. When I booted with this I have an Nvidia logo shown at startup, whereas in the others boots it didn't. In this state the laptops screen works. 
```
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"us"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"	"/dev/psaux"
#	Option		"Protocol"	"auto-dev"
#	Option		"HorizEdgeScroll"	"0"
#EndSection

Section "ServerLayout"

# commented out by update-manager, HAL is now used
#	Inputdevice	"Synaptics Touchpad"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "TOSHIBA Internal Panel"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "EIZO S1901"
    HorizSync       24.0 - 80.0
    VertRefresh     50.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX Go5200 32M/64M"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX Go5200 32M/64M"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```          

man xorg.conf is really big, can not just experiment..
Any ideas please?

---

### Post by 130s on 2011-02-25
(Ignore this. I posted by mistake)

---


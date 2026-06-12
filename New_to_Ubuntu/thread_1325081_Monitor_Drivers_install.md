---
title: "Monitor Drivers install"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by Psyper76 on 2009-11-13
I've plucked up the courage and just installed Ubuntu 9.10!

I have a Matrox video card which dual monitor outputs. At the moment both monitors are displaying the same screen.  In Display Preferences the monitor is showing as unknown and is only showing a single screen.  I've done a full update and there is nothing showing in the Hardware drivers in admin.

I've downloaded the Linux drivers for the specific card (I hope) but have no idea how to install it - it has terminal commands but I have no idea how to use them!!

Any help would be great :D

---

### Post by 3rdalbum on 2009-11-13
What are the instructions it gives? Usually you just install the "build-essential" and "linux-headers-generic" packages, open up a terminal in the directory that the driver code is in, and then copy and paste the commands into the terminal.

---

### Post by Psyper76 on 2009-11-13
Instructions say:

> Binary install
==============

A working installation of XFree86 4.3.0, and X.org versions 6.7.0, 
6.8.0, 6.8.1, 6.8.2, 6.9.0, 7.0.0 is required before the binaries 
can be installed.

To extract the driver files, enter the following command where 
<mga_filename> is the name of the driver file you want to extract:

  tar xvzf <mga_filename>.tgz

  cd mgadrivers

To install the drivers, run the script as "root" with no option:

  sh install.sh

The install script prompts you to install both the XFree86 2D 
driver ("mga_drv.o") and the HAL library ("mga_hal_drv.o"). Unless 
otherwise specified, these files are placed in 
"/usr/X11R6/lib/modules/drivers".

The installation script makes a back-up copy of "mga_drv.o" and, 
if it exists, of "mga_hal_drv.o". Being a windows user this doesnt make much sense to me!!  I've managed to find install.sh and I've opened a terminal session and managed to work out how to get to the correct folder - I've run sh install.sh and get the following error:

> [: 43: i686: unexpected operator
install.sh: 57: function: not found
---------------------------------------------------------
-e \E[31mERROR: You must be logged in as Root to run this program.
---------------------------------------------------------


How do I login as root??

---

### Post by Psyper76 on 2009-11-13
I've run the command:
> gksudo sh install.sh
and now I'm getting the error:

> Please enter the full path to your current X11R6 directory: 
Example: /usr/X11R6
-e \E[31mERROR: The X11R6 path could not be found. Please make
-e        sure that an X server is installed.

install.sh: 57: function: not found
install.sh: 69: function: not found
install.sh: 78: function: not found
install.sh: 95: function: not found
Not having much luck here :(

---

### Post by Psyper76 on 2009-11-14
Okay I have a matrox millennium g450 dual-head video card - basically this: [link]("http://www.techexcess.net/matrox-millennium-g450-dualhead-32mb-agp-video-graphics-card-g45fmdha32db.aspx")

I have two separate monitors connected to the two separate video outputs which I managed to get working in windows ages ago (can't remember how) so that when I move my mouse or window to the edge of one it appears on the other one (side by side).  In the vanilla install of Ubuntu I've got the display showing but it is mirrored on the 2nd monitor.

I've done a full update of the system - basically the first section in [this article]("http://blog.thesilentnumber.me/2009/09/top-things-to-do-after-installing.html").  But I get nothing.  When I go in to the synaptic package manager I get a lot of matrox stuff but I'm unsure what I should be installing here and I don't want to select everything incase it screws up my system unless someone here says its okay to give it a go!

In Display Prefrences the monitor is a single pink square with the error - Monitor: Unknown underneath and detect monitors doesn't change anything. Hardware Drivers in admin says that there are no proprietary drivers are in use on this system.

I think I found the correct Linux drivers for it but I couldn't install them correctly (see posts above) - there are various folders in a folder called 'xserver' in the driver download but I'm unable to work out what they are and how to use them.

I did a search and found that others that had problems with video cards are directed to manually create or modify the configuration files (I can't find the topic now to link it!)

Any help or suggestions will be great  - even if its just links to other threads saying try this but put this in instead etc etc.  The sooner I turn my back on windows the better :D

---

### Post by Psyper76 on 2009-11-17
Okay so I managed to find [this]("https://answers.launchpad.net/ubuntu/+source/yelp/+question/5121") at launchpad and applied it to my system and modified the code slightly.  I didn't have an xorg.conf file to work with so had to create the one below:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg
#
# Modified for Multihead operation
# 20 Oct 2007 by John Goodman
##

Section "Files"
 FontPath "/usr/share/X11/fonts/misc"
 FontPath "/usr/share/X11/fonts/cyrillic"
 FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
 FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
 FontPath "/usr/share/X11/fonts/Type1"
 FontPath "/usr/share/X11/fonts/100dpi"
 FontPath "/usr/share/X11/fonts/75dpi"
 FontPath "/usr/share/fonts/X11/misc"
 # path to defoma fonts
 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
 Load "i2c"
 Load "bitmap"
 Load "ddc"
 Load "dri"
 Load "extmod"
 Load "freetype"
 Load "glx"
 Load "int10"
 Load "type1"
 Load "vbe"
EndSection

Section "InputDevice"
 Identifier "Generic Keyboard"
 Driver "kbd"
 Option "CoreKeyboard"
 Option "XkbRules" "xorg"
 Option "XkbModel" "pc105"
 Option "XkbLayout" "us"
 Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
 Identifier "Configured Mouse"
 Driver "mouse"
 Option "CorePointer"
 Option "Device" "/dev/input/mice"
 Option "Protocol" "ExplorerPS/2"
 Option "ZAxisMapping" "4 5"
 Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  Option "Device" "/dev/wacom" # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option "Type" "stylus"
  Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  Option "Device" "/dev/wacom" # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option "Type" "eraser"
  Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "cursor"
  Option "Device" "/dev/wacom" # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option "Type" "cursor"
  Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
 Identifier "Matrox Graphics, Inc. MGA G400 AGP"
 Driver "mga"
 BusID "PCI:01:00.0"
 Option "OldDmaInit" "True"
EndSection

Section "Monitor"
        Identifier "Monitor0"
        ModelName "HANON"
        Option "DPMS"
        HorizSync 28-80
        VertRefresh 48-75
EndSection

Section "Monitor"
        Identifier "Monitor1"
        ModelName "HANON"
        Option "DPMS"
        HorizSync 28-80
        VertRefresh 48-75
EndSection

Section "Screen"
 Identifier "ScreenLeft"
 Device "Matrox Graphics, Inc. MGA G400 AGP"
 Monitor "HANON"
 DefaultDepth 24
 SubSection "Display"
  Depth 1
  Modes "1440x900" "720x450"
 EndSubSection
 SubSection "Display"
  Depth 4
  Modes "1440x900" "720x450"
 EndSubSection
 SubSection "Display"
  Depth 8
  Modes "1440x900" "720x450"
 EndSubSection
 SubSection "Display"
  Depth 15
  Modes "1440x900" "720x450"
 EndSubSection
 SubSection "Display"
  Depth 16
  Modes "1440x900" "720x450"
 EndSubSection
 SubSection "Display"
  Depth 24
  Modes "1440x900" "720x450"
 EndSubSection
EndSection

Section "Screen"
 Identifier "ScreenRight"
 Device "Matrox Graphics, Inc. MGA G400 AGP"
 Monitor "HANON"
 DefaultDepth 24
 SubSection "Display"
  Depth 1
  Modes "1440x900" "720x450"
  EndSubSection
 SubSection "Display"
  Depth 4
  Modes "1440x900" "720x450"
  EndSubSection
 SubSection "Display"
  Depth 8
  Modes "1440x900" "720x450"
 EndSubSection
 SubSection "Display"
  Depth 15
  Modes "1440x900" "720x450"
 EndSubSection
 SubSection "Display"
  Depth 16
  Modes "1440x900" "720x450"
 EndSubSection
 SubSection "Display"
  Depth 24
  Modes "1440x900" "720x450"
 EndSubSection
EndSection

Section "ServerLayout"
 Identifier "Multihead"
 Screen "ScreenLeft"
 Screen "ScreenRight" RightOf "ScreenLeft"
 InputDevice "Generic Keyboard"
 InputDevice "Configured Mouse"
 InputDevice "stylus" "SendCoreEvents"
 InputDevice "cursor" "SendCoreEvents"
 InputDevice "eraser" "SendCoreEvents"
EndSection

Section "ServerFlags"
 Option "xinerama" "true"
 Option "DefaultServerLayout" "Multihead"
EndSection

Section "DRI"
 Mode 0666
EndSection
```Now the - BusID "PCI:01:00.0" - part in the Device section was taken from lspci - in the instructions it should be xx: xx: xx not xx: xx.xx but when I change this nothing happens to my display but when I put in the config that I posted above I get an error when logging in - the monitors start flickering madly with errors and then asks me for my username and password in a bios/dos looking page (black background white foreground text) and its also hard to type as i have to type each letter 3 times before it gets accepted.  I have to reboot as safe mode and remove the config file and reboot to get back in.  I'm assuming that this means I've got the right busid but the config isn't set up correctly.  Has anyone had any luck with this at all??

---


---
title: "Nvidia Video Card that works with release 8.10"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by Dragonflyoh on 2009-01-23
I would like to know if anyone has updated to 8.1, without a clean install, and has a working video card?

I have a Nvidia GeForce 7100 GS and have tried every solution suggested by many people and always get a low graphics mode message and the driver is activated but not currently in use messages.

The video card is installed on a ASUS P5N32-SLI SE Deluxe Motherboard with a Pentium D 2.8 GHz processor and 1 GB memory.

The machine is both a workstation and a backend for Mythtv. I cannot set up the back end because of the low graphics mode. I will replace the video card if I could find someone that has one that works.

---

### Post by bailbath on 2009-01-23
[http://ubuntuforums.org/showthread.php?t=1043813](http://ubuntuforums.org/showthread.php?t=1043813)

Have you tried this read to the end of this thread.
Ian

---

### Post by northern lights on 2009-01-23
The latest official release of the NVIDIA Linux driver is 180.22 - it supports [these GPUs]("http://us.download.nvidia.com/XFree86/Linux-x86/180.22/README/appendix-a.html").

---

### Post by dawynn on 2009-01-23
I beat my head against the wall when I got to Intrepid, and yes, I think I even had to do a clean boot.

But after several failed attempts, I finally took a look at my /etc/X11/xorg.conf.

For whatever reason, the powers that had set up all the fun automatic tools for configuring xorg.conf were putting information in different places.  In the end, xorg.conf was set up with two monitors, two screens -- duplicates of many things.

I had to hand-edit the beast.  Once I trimmed everything down to a single screen, single monitor, etc, it was all fine and good.

Does your computer have the same issue? If you want some help deciphering your /etc/X11/xorg.conf, please post it and we'll take a look!

---

### Post by Dragonflyoh on 2009-01-23
This is what I have done based upon the inputs received.

Unloaded all Nvidia drivers with:

```
sudo apt-get remove nvidia*
```

Restarted computer.

Used the following from a post from Kosimo, thank you!!!!
Latest nVidia 180.xx drivers are: 180.22 (STABLE) You can download them here:
[http://www.nvidia.com/object/linux_display_ia32_180.22.html](http://www.nvidia.com/object/linux_display_ia32_180.22.html)


1) Downloaded the driver to my desktop

2) Entered a terminal mode: CONTROL + ALT + F1

3) Turned off x.org:

```
sudo /etc/init.d/gdm stop
```

4) Changed to my desktop:

```
cd Desktop
```

5) Ran the installer:

```
sudo sh ./NVIDIA-Linux-x86-180.22-pkg1.run
```

(If you hit TAB after you enter the first N the rest of the filename will automatically appear)

Answered Yes or OK to all questions and for the last step choose x.org automatic configuration as the last step inside the installation program.

6) Turned on x.org again

```
sudo /etc/init.d/gdm start
```

7. Edited xorg.conf:

```
sudo gedit
```

Added a line to the device section.
Did
```
lspci
```
to find the line with my video card and entered
Busid "PCI:01:00.0"
Restarted the computer and get the same message about no Nvidia kernel loaded and back to low graphics mode.

Here is my current xorg.conf

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
# This was generating an error at start up
#   Load           "type1"
    Load           "freetype"
    Load           "glx"
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

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Busid          "PCI:01:00:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Any ideas would be greatly appreciated.

---

### Post by Technoviking on 2009-01-23
Check out these instructions.
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by anewguy on 2009-01-23
Currently had to remove (for work purposes) Ubuntu from my system, but I have an nVidia 8400 GS that worked great using envyng to install the driver.  Compiz, etc., all worked flawlessly.  I have dual monitors and that even worked.

Dave :)

EDIT: re-install 8.10 desktop today.  I just used the restricted driver included with 8.10 and then nvidia-settings and everything works great.

---

### Post by Dragonflyoh on 2009-01-26
Thanks for all of the ideas. After all the time trying the various cures, and nothing correcting the problem, I have ordered a new video card and will provide an update after the card is installed. Again, thanks to everyone for the assistance.

---

### Post by Dragonflyoh on 2009-02-01
I installed my new card, a 8400GS, and the results are the same. I went through all of the drivers etc. and nothing works.
I am now working on backing up my Mythtv data base and email and am going to return to 8.04. Thanks to everyone for their ideas.

---


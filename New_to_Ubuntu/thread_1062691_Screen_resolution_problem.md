---
title: "Screen resolution problem"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by edno99 on 2009-02-07
Hello,

My windows died and I'm newly converted. About time too!! 

Got Ubuntu installed and seems to be working ok, but I'm having a desktop issue... 

My screen resolution seems to not be able to get higher than 800x600, whereas on xp I could get 1240x768. I've gone into the screen resolution settings and the option for 1240x768 isn't there. My desktop seems to be rather large and I have to alt drag any menus around to be able to see them. Does anyone have a solution please?

I'm running the latest version of ubuntu, fully updated and my monitor is a Sony SDM-S75A.

Thanks

---

### Post by 73ckn797 on 2009-02-07
Have you checked for the proper driver?

Go to System/Administration/Hardware Drivers. Any that are "recommended" should be used.

Do that first. You will probably have to reboot once the driver is installed.

---

### Post by edno99 on 2009-02-07
I've just been there and I don't have anything in that menu... everything's blank and there's just a message saying "no proprietary drivers are in use on this system". Also found out that I can't get sound either - video works though - are these problems related?

---

### Post by Sidewinder1 on 2009-02-07
The following link may be of help:
[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

---

### Post by edno99 on 2009-02-10
In my monitor resolution settings, the display is set to unknown, but I'm using a Sony SDM-S75A TFT with a maximum resolution of 1280x1024.
I have a feeling that the driver for the video card may not be right - SiS recommend going to this place to download something... [http://www.winischhofer.eu/linuxsispart4.shtml#download](http://www.winischhofer.eu/linuxsispart4.shtml#download)
but I'm unsure what to download! Hopefully these terminal command outputs will help:

Video card:

> lspci | grep -i vga
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

output of "X -version"
> 
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux ed-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686
Build Date: 24 October 2008 08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd)
 Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
 to make sure that you have the latest version.
Module Loader present

output of "sudo nano /etc/X11/xorg.conf"

> Section "Device"
        Identifier "Configured Video Device"
EndSection

Section "Monitor"
        Identifier "Configured Monitor"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Monitor "Configured Monitor"
        Device "Configured Video Device"
EndSection

---

### Post by SteveNorman on 2009-02-10
youll need to add the options for your monitor to your /etc/X11/xorg.conf file.

I found this from another forum. You can modify your xorg.conf to add these settings and reboot, seeing what happens. Before you do this however, you need to be able to edit a file from the command line incase your display gets hosed.

```

Section "Monitor"
DisplaySize 340 270
HorizSync 28-60
Identifier "Monitor[0]"
ModelName "SONY SDM-S75A/E"
Option "DPMS"
VendorName "SNY"
VertRefresh 50-60
UseModes "Modes[0]"
EndSection

Section "Modes"
Identifier "Modes[0]"
Modeline "1280x960" 97.68 1280 1352 1488 1696 960 961 964 993
Modeline "1280x800" 80.58 1280 1344 1480 1680 800 801 804 827
Modeline "1152x864" 78.82 1152 1216 1336 1520 864 865 868 894
Modeline "1280x768" 77.37 1280 1344 1480 1680 768 769 772 794
Modeline "1024x768" 61.89 1024 1080 1184 1344 768 769 772 794
Modeline "1280x600" 58.78 1280 1328 1456 1632 600 601 604 621
Modeline "1024x600" 47.26 1024 1064 1168 1312 600 601 604 621
Modeline "800x600" 36.88 800 832 912 1024 600 601 604 621
Modeline "768x576" 33.74 768 792 872 976 576 577 580 596
Modeline "640x480" 23.06 640 656 720 800 480 481 484 497
EndSection

Section "Screen"
DefaultDepth 24
SubSection "Display"
Depth 15
Modes "1280x1024" "1280x960" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1280x960" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1280x960" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1280x960" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
EndSubSection
Device "Device[0]"
Identifier "Screen[0]"
Monitor "Monitor[0]"
EndSection
```

step one: backup your xorg incase you screw it up
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Now add the info from above in your xorg.conf. (cut and paste to avoid typos)

```
sudo gedit /etc/X11/xorg.conf
```

save it, then resart x by using cntrl/alt/backspace

if it works you will see the new options in the screen resolution options. If it gives you a text login and no desktop (black screen) then login and at the prompt do

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

then```
startx
```

good luck!

---

### Post by edno99 on 2009-02-10
Steve Norman. You're a genius. Problem solved! Hurrah!

---

### Post by SteveNorman on 2009-02-10
sweet,,hows your sound?

---


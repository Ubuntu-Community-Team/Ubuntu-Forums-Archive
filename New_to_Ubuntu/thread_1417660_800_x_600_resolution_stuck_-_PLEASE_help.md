---
title: "800 x 600 resolution stuck - PLEASE help"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by pjb8033 on 2010-02-27
Hello, please help me, I have recently installed ubuntu 9.1 on a packard bell easynote laptop due to being frustrated with windoze. the problem i have is that i can not increase my screen resolution above 800 x 600. I have tried creating xorg.conf but to no avail i have also tried adding lines to etc/gdm/init

xrandr --newmode "1024x768 6oHz" 60 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
xrandr --addmode VGA1 "1024x768 6oHz"
xrandr --mode "1024x768 6oHz"

this did not work either.
I believe the graphics are SIS on this machine and that this may be the problem. it also happens on fedora linux.

---

### Post by coolbrook on 2010-02-27
Did you run a Live CD session prior to installation?

What is the terminal output of 

```
lspci
```

---

### Post by pjb8033 on 2010-02-27
> **coolbrook said:**
> Did you run a Live CD session prior to installation?

What is the terminal output of 

```
lspci
```

Thank you for rapid reply,

no i never ran live cd session, ubuntu 9.1 was fresh install on entire drive, installed twice just in case.

output of lspci is

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

---

### Post by coolbrook on 2010-02-27
I noticed your lines above show 6oHz instead of 60Hz. (sixty)  Try a re-edit.  If that doesn't work try

```
sudo apt-get install xserver-xorg-video-sis
sudo reboot
``` and see if you can change your resolution.

---

### Post by paydaydaddy on 2010-02-27
run the following command in terminal:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then restart X or restart your computer. You should then have additional resolutions listed for monitor settings. If not, post back for more input.

---

### Post by pjb8033 on 2010-02-27
> **coolbrook said:**
> I noticed your lines above show 6oHz instead of 60Hz. (sixty)  Try a re-edit.  If that doesn't work try

```
sudo apt-get install xserver-xorg-video-sis
sudo reboot
``` and see if you can change your resolution.

Tried these but still no joy, i suspect screen in display settings says unknown monitor and xrand output is

Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  
  1024x768 6oHz (0x104)   60.0MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   45.2KHz
        v: height  768 start  771 end  775 total  798           clock   56.6Hz

---

### Post by pjb8033 on 2010-02-27
> **paydaydaddy said:**
> run the following command in terminal:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```Then restart X or restart your computer. You should then have additional resolutions listed for monitor settings. If not, post back for more input.

Tried this, but still no extra resolutions, suspect screen, maybe xrandr output is
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  
  1024x768 6oHz (0x104)   60.0MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   45.2KHz
        v: height  768 start  771 end  775 total  798           clock   56.6Hz

---

### Post by pjb8033 on 2010-02-27
after weeks of trying i think its time to call it a day, nice while it lasted, its either laptop in bin or off to pc world for a copy of windoze 7. Thanks for the help anyway:mad:

---

### Post by mapman88 on 2010-02-27
Hi, I have the same issue - have a 20 inch Princeton monitor. I should be t 1024 x 768, but all I can select under Preferences>Display is 800 x 600 or smaller. And it says Monitor unknown.
thanks in advance
MM

---

### Post by DrWer2 on 2010-02-28
I've had the same problem on a HD LCD Polaroid TV/monitor. Never could solve it.

---

### Post by mapman88 on 2010-02-28
I just tried System>Administration>Hardware Drivers and downloaded a driver from nVidia(version 173) and now I have a ton of choices, appears to be solved for me....
Good Luck

---

### Post by ccroy on 2010-02-28
I had similar problems, I am running SiS Video chips on the motherboard of my PC and I am using an HDTV as a monitor since it came with a standard VGA monitor input.

Ubuntu 8.10 did not find either my video drivers nor the monitor type so it defaulted to "Unknown Monitor" and gave me 800x600 as the highest resolution.

This is what ended up fixing it for me:

type "lspci" to identify which video chips/card your system has

> chris@chris-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 740 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
chris@chris-desktop:~$ 


Then I got totally lucky and found an xorg.conf somebody had written for my SiS chipset. I pasted it into my original xorg.conf and commented out the original lines, which is everything below "+++++++++old+++++++". Note that #comments out lines so they won't run.

From terminal type: gksudo gedit /etc/X11/xorg.conf

Enter your passwaord and you should see your xorg.conf, here is mine.

> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Device"
Identifier "Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter"
Driver "sis"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection 
#+++++old++++++++
#Section "Device"
#    Identifier    "Configured Video Device"
#    Driver        "vesa"
#EndSection
#
#Section "Monitor"
#    Identifier    "Configured Monitor"
#EndSection
#
#Section "Screen"
#    Identifier    "Default Screen"
#    Monitor        "Configured Monitor"
#    Device        "Configured Video Device"
#EndSection

I also notice in the original post the user was typing "VGA1" in xrandr. If your system is in the state my was the name of the monitor is actually "default".

Good Luck!

Chris

---

### Post by pjb8033 on 2010-03-01
Thanks chris, tried that and ended up with a flickering screen and had to reinstall, really liked the idea of ubuntu and linux, but i guess its true what they say. You get what you pay for!!!

---

### Post by zezerbing on 2010-03-01
Same here guys.

---

### Post by halitech on 2010-03-01
apparently there is a bug with the SIS drivers in Ubuntu. Check here

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/301958/comments/38](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/301958/comments/38)

---


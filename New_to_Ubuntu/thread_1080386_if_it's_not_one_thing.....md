---
title: "if it's not one thing...."
date: 2009-02-25
forum: New to Ubuntu
---

### Post by pperez2084 on 2009-02-25
I am having tons of trouble with my first few days of Linux and Ubuntu. Where to begin...

One of the first things I had to do when I installed linux is install the latest ATI Radeon driver and Catalyst Control Center. I downloaded Catalyst 9.2* direct from ATI, and installed it. After some tinkering, I had usable desktop display.

I also used the Synaptic Package Manager to install Kubuntu and Xubuntu Desktops, so I could try them out. The install didn't go quite the way [it was supposed]("/http://www.psychocats.net/ubuntu/kde") to, though. I was never given an option to choose the display manager. Otherwise, I have been able to log in with Gnome, Xfce, or KDE.

However, I am not able to log out of any of them. When I log out, the display goes black. I don't know a key combination that will restore any control. The only thing I can do is hit the reset button on the tower.

Anyway, that's fairly easy to work around. I don't actually have to log out of a session--I'm the only one using this PC. But then I downloaded all 230 of the recommended updates, and that put a second Ubuntu kernel in GRUB. I have a 2.6.26-7 and a 2.6.26-11 version. The -11 version doesn't start up at all. When I try to start into it, I get some lines on one monitor, and my BIOS startup screen is tiled over the other screen.

I can still get into -7. But then this morning, I am not able to log into Gnome. From the Xubuntu log-in screen, I choose a Gnome session, and the Ubuntu desktop background will pop up, but the rest of the desktop never shows up. I am still able to log into Xfce and KDE.

Anyway, my question is, at what point is it a good idea to wipe the linux partition of my HDD and start from scratch?


*I have a dual monitor setup, with one monitor rotated 90 degrees. In Windows XP, I use Catalyst Hydravision to run an extended desktop between the two monitors. I hoped I would be able to use Catalyst the same way in Ubunutu. I don't see that I can, though.

---

### Post by KhaaL on 2009-02-25
Hi!

problem with ATI is that they haven't made their drivers as mature on linux as on windows compared to nvidia (but that might have changed today). I'd recommend you to stick to the driver in the repository, alternatively seek if there is a PPA for a ATI driver for ubuntu. 

I think its strange that you couldn't boot into your -11 kernel, it could be a issue with your video driver. The problem could be identified by seeing your /etc/X11/xorg.conf file.

Otherwise, i'd recommend you to reinstall... and in the meanwhile, learn about the magic keys here: [http://www.ubuntugeek.com/how-to-reboot-your-ubuntu-system-only-if-all-else-fails.html](http://www.ubuntugeek.com/how-to-reboot-your-ubuntu-system-only-if-all-else-fails.html) - they will eliminate your need for a reset button :-)

---

### Post by pperez2084 on 2009-02-25
Judging by the lack of ideas here, I guess it's time to start over from scratch.

---

### Post by Temposs on 2009-02-25
Additionally, you may want to try Ubuntu 8.04, since the current kernel version of Ubuntu 8.10 doesn't seem to readily work for you. Ubuntu 8.04 is generally more stable.

---

### Post by pperez2084 on 2009-02-25
Oh, thanks, the magic keys might help. I'll try that before I reinstall. I'm sure I'll still have to reinstall, but it'll be interesting to know if that works.

I tend to blame the ATI drivers for everything, I had a lot of trouble getting the display set up after I installed them. I wonder if the display is in some virtual space that doesn't overlap the actual screen. 

The trouble with the new kernel could also be a driver conflict...anyway, the 2.6.26-11 kernel definitely doesn't want to work with my graphics card.

I'll also post the xorg.conf file when I get back into ubuntu.

Thanks KhaaL!

---

### Post by pperez2084 on 2009-02-25
Here are the contents of the xorg.conf file. 


```
Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[1]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth	24
	SubSection "Display"
		Virtual   3200 1200
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	Monitor    "amdcccle-Monitor[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 1280 0
	Screen         "amdcccle-Screen[1]-1" 0 0
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	BusID       "PCI:1:0:0"
	Driver	"fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	BusID       "PCI:1:0:0"
	Screen      1
	Driver	"fglrx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

```

---


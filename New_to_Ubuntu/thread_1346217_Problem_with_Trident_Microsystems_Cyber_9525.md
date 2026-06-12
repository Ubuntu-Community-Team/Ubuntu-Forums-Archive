---
title: "Problem with Trident Microsystems Cyber 9525"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by yurfader on 2009-12-04
I have a very old Toshiba laptop that has a Trident Microsystems Cyber 9525 in which I already installed Ubuntu 9.10. The resolition that the system show is 800x600 but I know that the display can work with a resolution of 1024x768 with a depth of 16 bits. 

I tried configuring the Default file with xrandr and the option of 1024x768 is shown on the resolution options but when I apply the change to this resolution the system gives an error and do not configure the desired resolution.

I tried a different approach with the xorg.conf file and everything seems to work Ok at the startup, the system gets until the startup window with the right resolution, but once I enter the user and password, the system goes back to the same startup window.

I think that there is somehow a conflict between the new configuration of the xorg.conf file and the default configuration.

The problem if I configure the resolution with xrandr is that I have to change the depth to 16 in order I can use the 1024 resolution.

The xorg.conf file that I am using is the following:

```
ection "Device"
Identifier "Configured Video Device"
Boardname "vesa"
Busid "PCI:1:0:0"
Driver "trident"
Screen 0
EndSection

Section "Monitor"
Identifier "Configured Monitor"
Vendorname "Generic LCD Display"
Modelname "LCD Panel 1024x768"
Horizsync 31.5-48.0
Vertrefresh 56.0 - 65.0
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
Gamma 1.0
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
Defaultdepth 16
SubSection "Display"
Depth 16
Modes "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
EndSubSection
EndSection

```

I would appreciate any help.

---

### Post by yurfader on 2009-12-05
> **yurfader said:**
> I have a very old Toshiba laptop that has a Trident Microsystems Cyber 9525 in which I already installed Ubuntu 9.10. The resolition that the system show is 800x600 but I know that the display can work with a resolution of 1024x768 with a depth of 16 bits. 

I tried configuring the Default file with xrandr and the option of 1024x768 is shown on the resolution options but when I apply the change to this resolution the system gives an error and do not configure the desired resolution.

I tried a different approach with the xorg.conf file and everything seems to work Ok at the startup, the system gets until the startup window with the right resolution, but once I enter the user and password, the system goes back to the same startup window.

I think that there is somehow a conflict between the new configuration of the xorg.conf file and the default configuration.

The problem if I configure the resolution with xrandr is that I have to change the depth to 16 in order I can use the 1024 resolution.

The xorg.conf file that I am using is the following:

```
ection "Device"
Identifier "Configured Video Device"
Boardname "vesa"
Busid "PCI:1:0:0"
Driver "trident"
Screen 0
EndSection

Section "Monitor"
Identifier "Configured Monitor"
Vendorname "Generic LCD Display"
Modelname "LCD Panel 1024x768"
Horizsync 31.5-48.0
Vertrefresh 56.0 - 65.0
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
Gamma 1.0
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
Defaultdepth 16
SubSection "Display"
Depth 16
Modes "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
EndSubSection
EndSection

```I would appreciate any help.


**Any ideas?**

---

### Post by wojox on 2009-12-05
[http://ubuntuforums.org/showthread.php?t=763964&highlight=Trident+Microsystems](http://ubuntuforums.org/showthread.php?t=763964&highlight=Trident+Microsystems)

---

### Post by yurfader on 2009-12-05
Thanks, but I made a search for displayconfig-gtk on Ubuntu 9.10 and it is not there. It is not on the system nor on synaptic.

How changed the xorg configuration changed on Ubuntu 9.10? I think that there might be the answer.



Regards

---


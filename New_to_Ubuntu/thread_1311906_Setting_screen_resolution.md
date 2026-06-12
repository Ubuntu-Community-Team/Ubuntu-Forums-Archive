---
title: "Setting screen resolution"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by DWL52 on 2009-11-02
Hello all. I'm pretty new to Ubuntu and need your help. Just did a fresh install of 9.10, and have an Nvidia FX 5200 Graphics card installed. The only screen resolutions I have available are 640x480 and 320x240 (way too big). I have a non-PNP Spectre 19" monitor.I want to set the resolution to 1024x768 or 1280x1024, something around there. I know I have to go in somewhere and monitor a file to change this, but don't remember what line in what file to change. Any and all help is greatly appreciated.

Dave

---

### Post by NickJones on 2009-11-02
System, Prefernces, Displays, then the drop down resolution box.
Nick

---

### Post by cjohnston on 2009-11-02
Do you have the correct driver installed? Go to System > Admin > Hardware Drivers and make sure that the correct driver is installed.. If it isn't install it and try changing the resolution again.

---

### Post by DWL52 on 2009-11-02
> **FFEMTcJ said:**
> Do you have the correct driver installed? Go to System > Admin > Hardware Drivers and make sure that the correct driver is installed.. If it isn't install it and try changing the resolution again.

When I do this, a screen comes up that says "no proprietary drivers are in use in this system", then goes on to explain what it meant. I have two choices below that. One of which is the Nvidia version 173 driver, which is the recommended one. I have it activated, but when I go into System>Preferences>Display, I get the message "It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?" When I click yes, it goes into an Nvidia screen that is too big to fit and when I try to click on anything on the screen, it shifts to one direction or another. Besides that, I don't see anywhere to adjust resolution.

---

### Post by cjohnston on 2009-11-02
Oh ya... Ok.. So, enable the driver, and make sure to reboot... When you boot back up, open the terminal, and run:

sudo nvidia-xconfig

then 

sudo nvidia-settings

You should be able to now change the settings.. I think it's the second tab down that you would use to change the settings.. Let me know if this works.

---

### Post by DWL52 on 2009-11-02
> **FFEMTcJ said:**
> Oh ya... Ok.. So, enable the driver, and make sure to reboot... When you boot back up, open the terminal, and run:

sudo nvidia-xconfig

then 

sudo nvidia-settings

You should be able to now change the settings.. I think it's the second tab down that you would use to change the settings.. Let me know if this works.

No help. All it does is take me to the Nvidia configuration screen, which is too big to fit on the screen. I went in there as you said and the only choices available are 640x480 and 320x240. When I first installed Ubuntu, I ran into this same problem and was given the advice to go into some file and edit it to change the resolution, but I've forgotten what file it was or what to put in or take out of the file. Actually, about all the screens I go into, such as Evolution, are too big to fit the screen, and when I click on them anywhere, they shift from side to side, making choosing something on the screen next to impossible using the mouse.

---

### Post by cjohnston on 2009-11-02
I assume your talking about /etc/X11/xorg.conf

---

### Post by Locke_99GS on 2009-11-02
Try

```
xrandr -q
```

To see available detected resolutions. If 1280x1024 (or whatever you want) is on that list, you should be able to safely set it via:

```
xrandr -s 1280x1024
```

If the res you want is not on that list, set it to the highest possible, then run the first command again; sometimes it will show more options the second time. :???: Otherwise, you can try to force it to a particular resolution, but I'm unsure of what the consequences may be if it goes awry setting a resolution that doesn't show in the query.

---

### Post by DWL52 on 2009-11-03
When I run xrandr -q, the response is:
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  

When I run command xrandr -s 1280x1024, the response is:
Size 1280x1024 not found in available modes

The same holds true when I run xrandr -s 1024x768, which  is what I had the resolution set to in Ubuntu 9.04.

You mentioned file /etc/X11/xorg.conf. Is that where I can edit it to a specific resolution, and if so, what in that file do I need to edit?

---

### Post by DWL52 on 2009-11-04
Still needing help. I have edited xorg.conf per the online instructions, but still the highest res I can get is 800x600. Anyone??

---

### Post by realzippy on 2009-11-04
Suggest to start again.
assuming your nvidiadriver is running,open a terminal and delete your current xorg.conf:

**sudo rm /etc/X11/xorg.conf**

make new one:

**sudo nvidia-xconfig**

Log out and in to load it.

open terminal,type:

**gksudo nvidia-settings**

Make your settings,hit apply,hit (important!!) "save to X configuration file"

---


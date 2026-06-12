---
title: "resolution problems"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by al_ex on 2009-02-21
Hi, new to ubuntu, my names Alex

ok, been trying to install ubuntu for about 12 hours now, but now i need help.

ive edited my xorg.conf file so many times i cant remember what the original looked like,(no, i didn't back it up),  so i just deleted it,  and ran dpkg reconfigure to generate a new one, but i just dont know what to do now.

i know what my resolution should be and my horizontal and vertical refresh rates are but i dont know where to put them, ive tried a few times but always end up in low graphics mode.

hers what my xorg.conf file looks like at the moment
```

Section "Device"
        Identifier    "Configured Video Device"
EndSection

Section "Monitor"
        Identifier    "Configured Monitor"
EndSection

Section "Screen"
        Identifier    "Default Screen"
        Monitor       "Configured Monitor"
        Device        "Configured Video Device"
EndSection


```

where should i put the following?

resolution 1280x1024
horizontal frequency 30-82
vertical frequency 56-76

ive tried maybe 25-30 times to do it myself, but its useless, i end up in low graphics mode every time.

any ideas on what to do now?

---

### Post by RomeReactor on 2009-02-21
Hi. The X server (the program that handles your display) relies more on autoconfiguration now, so changes to xorg.conf don't always work. Try booting into recovery mode and select XFIX to see if that helps.

---

### Post by rafac24 on 2009-02-21
If you haven't already taken a look at this:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

May help some.

---

### Post by al_ex on 2009-02-21
after selecting xfix in recovery mode it keeps sayin 

"warning overwriting possibly customised configuration"

and some more beneath it which i cant read,  and then goes back to the menu.

Is it broken, becuase theres a dpkg option that fixes packages here, should i try that?

---

### Post by RomeReactor on 2009-02-21
> **al_ex said:**
> after selecting xfix in recovery mode it keeps sayin 

"warning overwriting possibly customised configuration"

and some more beneath it which i cant read,  and then goes back to the menu.

Is it broken, becuase theres a dpkg option that fixes packages here, should i try that?

That's a warning you get whenever you use XFIX; it's just telling you it will make changes to xorg.conf. After it goes back to the menu select "Resume normal boot".

Can you give us more details about your system--video card, processor, memory?

---

### Post by al_ex on 2009-02-21
ahh ok, i resumed boot anyway but nothing has changed
still only get 800x600 resolution at best

nVidia GeForce 6200LE
intel duo core e6750 @2.66GHz
1GB memory

8.10 intrepid (same probs with 8.04 tho)

do you think jaunty jackalope will be better with resolution issues?
ill download it anyway just incase

---

### Post by RomeReactor on 2009-02-21
Have you installed the nVidia drivers in 'System->Administration->Hardware Drivers'? Is this a laptop, or a desktop system?

---

### Post by al_ex on 2009-02-21
I've tried installing the drivers both the ubuntu way and envyNg way but nothing happens,  when i reboot,  they're not activated

desktop

thanks for helping BTW, i appreciate it

EDIT: just tried again, driver not activated again,  ive tried all 3 drivers on offer also. I usually end up rebooting in low graphics mode.

---

### Post by ajgreeny on 2009-02-21
Try making your xorg.conf look like this with a manual edit, and see if it helps.  This version is mine (minus the comments at the top of the file).
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-82
            VertRefresh    56-76
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```
You do not even need all the lower resolutions but can just leave the one you want, ie 1280x1024

God luck; I hope this is successful.

---

### Post by RomeReactor on 2009-02-21
In case you haven't tried this (from the terminal):
```
nvidia-xconfig
```

Also, you can try using the nvidia-glx-180 driver; in order for it to show up in 'Hardware Drivers', you need to install nvidia-180-modaliases:
```
sudo aptitude install nvidia-180-modaliases
```
And if you installed a driver through envy or directly from nVidia's site, make sure it's uninstalled.

---

### Post by al_ex on 2009-02-21
your a legend aj, thats fixed the resolution nicely:D

i tried nvidia-xconfig from the terminal a few times, nothing happened though.

thanks for the help ajgreeny and RomeReactor,  much appreciated.

just need to figure out why the screen is offset to the right by about a half an inch, but ill do that tomorrow ;)

---

### Post by ajgreeny on 2009-02-22
Glad to be of help.  The offset of your screen may just be a display attribute you can sort with an auto button on the monitor or by adjusting its position manually.

---


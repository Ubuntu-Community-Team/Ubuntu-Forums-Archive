---
title: "Compiz is crashing"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by reallunacy on 2009-08-05
When I load compiz using "compiz --replace" it will load compiz, then freeze if I try to open any programs after it. when it does this the mouse is almost entirely unresponsive. and the screen flashes grey. 

I downloaded compiz-check and when I type "./compiz-check" into the terminal I get this:
```
mike@mike-desktop:~/Desktop$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   Xfce
 Graphics chip:         nVidia Corporation GeForce 8400 GS (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```When I enter "compiz --replace I get:
```
mike@mike-desktop:~/Desktop$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Couldn't find a perfect decorator match; trying all decorators
Starting emerald
```

The only thing I can think of is it has to do with the Glg it states as, "not present," however I'm not sure how to fix that. I found what looked the download for it, but it was a .ymp file(i think) which only allowed me to open as a text document. Any help would be greatly appreciated.

edit: Where it says Starting emerald, that is the last line in the terminal and it never progresses. Also, in addition to the mouse being extremely sluggish and glitchy, the entire GUI is unrepsonsive. I always end up having to reboot via the button on my case.

My computer is an old eMachines that I uninstalled Windows XP off of.
Stats are 1.2gigs of DDR ram, 3.0Ghz Celeron D processor and a GeForce 8400 graphics card.

---

### Post by reallunacy on 2009-08-09
Anybody have any ideas?

---


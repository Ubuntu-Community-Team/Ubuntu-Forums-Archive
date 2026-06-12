---
title: "Error: Frequency Over Range (cannot open display)"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by okanagansage on 2010-03-19
I was trying out different refresh rates in Xubuntu 9.10 and chose one that my monitor apparently cannot handle. I tried a 70 hz or 75 hz refresh rate and the monitor went to sleep. I believe the resolution was 800 x 600. It's an old monitor from the late nineties (viewsonic a70). I now have the manual for the monitor and here's the listed maximum refresh rates:
   1280 x 1024 NI @ 66 hz
   1024 x 768 NI @ 87 hz
   800 x 600 NI @ 110 hz
   640 x 480 NI @ 135 hz
 
From the grub menu I have booted into recovery mode of the most recent kernel. I need to know how to change the refresh rate (and resolution?) from a command line. 

Please, only answer if you know how to do this in Xubuntu 9.10. I've search the forums and the things I've tried don't seem to apply to this distro. I have next to no experience with the terminal so please keep that in mind. Thanks for your help in advance.

---

### Post by okanagansage on 2010-03-19
I have navigated to the /etc/X11/ file but there's no xorg.conf file. 

The content list for the /etc/X11/ file is:

X (in light blue text)
Xresources (in blue text)
Xsession (in yellow text)
Xsession.d (in blue text)
Xsession.options
XvMCConfig
Xwrapper.config
app-defaults (in blue text)
cursors (in blue text)
default-display-manager
fonts (in blue text)
rgb.txt
xinit (in blue text)
xkb (in blue text)

---

### Post by halitech on 2010-03-19
xorg.conf is no longer created during a fresh install of 9.10 as the hardware detection is handled directly instead of requiring an xorg.conf file which is why you can't find it. 

I believe if you boot into recovery mode and run xfix it *should* repair X to a working condition. Do you know what video card you have installed in the machine?

---

### Post by okanagansage on 2010-03-19
It's fixed! 

I tried 'repair broken packages' from recovery kernel (grub selection). Also, on reboot after that, I pressed ctrl alt + (which changes screen resolution on the fly) just after putting in my user password. I'm not sure what worked (probably the 'repair broken packages') but the display stays on. Added bonus: my desktop just about fits my screen size. Before this all started, the black margins on the perimeter of my desktop were larger. Now there's only a small margin (less than a half-inch) on the top and left.

---

### Post by okanagansage on 2010-03-19
Hey, I just noticed your reply after getting this worked out. I'm guessing that what I did and your suggestion are the same option. Thanks for trying to help.

---


---
title: "Compiz problem | Checking for Xgl: not present"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by jbcollins on 2009-07-03
I was hoping to run the Mac4Lin theme. Everything works except for AWN - with a warning saying Compiz is not started. I am running a Dell Vostro with an onboard Intel GPU.

Thanks in advance for your help.

```
_@laptop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: Log level 16: Invalid borders specified for theme pixmap:
        /home/j/.themes/Mac4Lin_GTK_Aqua_v1.0/gtk-2.0/Shadows/shadow-out.png,
borders don't fit within the image
```

---

### Post by nhasian on 2009-07-04
you cant enable compiz because your intel video driver is blacklisted.  you can unblacklist it by copy & pasting the following command into a terminal:

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

[Here's]("https://bugs.launchpad.net/ubuntu/jaunty/+source/xserver-xorg-video-intel/+bug/359392") more information about the bug.

after you've unblacklisted your card, reboot and go to system->preferences->appearance and set the visual effects to Normal or Extra.  Hey now you've got wobbly windows enabled!  :)

---

### Post by jbcollins on 2009-07-04
@ nhasian,

Thanks for looking at my issue. Unfortunately, this did not fix my problem. After the code and reboot, I still cannot enable desktop effects.

---

### Post by mc4man on 2009-07-04
A bit of a longshot but worth checking.
Run this and under the apps -> metacity -> general make sure that metacity **isn't** set as compositing manager

```
gconf-editor
```

---

### Post by jbcollins on 2009-07-04
@ mc4man,

Thanks that worked. Whew!! I spent most of yesterday trying to fix this. Thanks again!

---

### Post by jbcollins on 2009-07-04
Update:

The desktop effects work, but the AWN will not work after restart. Typing Compiz in Terminal gives the following still: 

```
j@j-laptop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

I think I am done with AWN :-) I will let the gnome panel do its job. Thanks again!

---

### Post by 02ak on 2010-03-09
I am having same problem Gnome Do and AWN both don't work, until i run compiz -- replace

```

~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1366x768) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

i have installed my ATI Radeon drivers also, and also tried installing KDE, but KDE is stucks after i login just a terminal opens and even without a titlebar if i quite, i am back on login screen and in gnome this problem,

wot should i do =^___^=

---


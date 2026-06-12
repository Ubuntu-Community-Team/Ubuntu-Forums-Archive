---
title: "Need some help"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by clay woodruff on 2009-11-20
I've installed 9.10 on my computer and went to the hardware manager and downloaded the drivers for my nvidia card. its a 5200 fx. i can't set my resolution past 640x480. all i need is for the correct information to enter into my xorg.conf file to solve this problem. or does anyone know where to get it

---

### Post by Exadrid on 2009-11-20
First, if you have not yet, restart your comp it works better for installing a driver....

second try

> sudo nvidia-settings

then the second tab put the setting you want.

---

### Post by clay woodruff on 2009-11-21
i went into nvidia settings as sudo and in the panning line i entered 1024x748 @ 60hz and clicked on apply the screen got streatched long ways and width ways so i went back to terminal and this is what it said.
clay@clay-desktop:~$ sudo nvidia-settings 

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".

Segmentation fault
clay@clay-desktop:~$ 

so what happened i must of did something wrong

---

### Post by Darce on 2009-11-21
Try here :

[http://ubuntuforums.org/showthread.php?t=1326993](http://ubuntuforums.org/showthread.php?t=1326993)

---

### Post by clay woodruff on 2009-11-21
ok i think i'm getting somwhere at last. i actually managed to get into my xorg.conf file but this is all there was in it

Section "Screen"
    Identifier    "Default Screen"
    Option    "AddARGBGLXVisuals"    "True"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection


what do i need to do to make this file work for my nvidia 5200fx card and a hp vf51 flat panel monitor, i guess what i need is the right format to enter in the file. please be specific i have no clue as to how or what to do. it took me 3 days just to figure out how to get the file open. and countless hours searching forums youtube and google. i'm running 9.10 only no windows.

---


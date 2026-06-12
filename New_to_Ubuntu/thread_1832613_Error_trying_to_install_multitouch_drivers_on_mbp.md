---
title: "Error trying to install multitouch drivers on mbp"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by Dan Delano on 2011-08-25
I have a macbook pro 5,5 that I recently installed natty on. I went to [https://help.ubuntu.com/community/MacBookPro5-5/Natty#Touchpad](https://help.ubuntu.com/community/MacBookPro5-5/Natty#Touchpad) and tried to follow their instructions to set up multitouch.

When I try to run sudo apt-get install xf86-input-multitouch bcm5974-dkms I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xf86-input-multitouch
E: Unable to locate package bcm5974-dkms

Any help is appreciated.

---

### Post by androssofer on 2011-08-25
> **Dan Delano said:**
> I have a macbook pro 5,5 that I recently installed natty on. I went to [https://help.ubuntu.com/community/MacBookPro5-5/Natty#Touchpad](https://help.ubuntu.com/community/MacBookPro5-5/Natty#Touchpad) and tried to follow their instructions to set up multitouch.

When I try to run sudo apt-get install xf86-input-multitouch bcm5974-dkms I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xf86-input-multitouch
E: Unable to locate package bcm5974-dkms

Any help is appreciated.

looks like the repository for the files is missing, thet are part of the mactel packages, so try this:

```
sudo add-apt-repository ppa:mactel-support/ppa 
sudo apt-get update
```

then do the 

```
sudo apt-get install xf86-input-multitouch bcm5974-dkms
```

again

---

### Post by Dan Delano on 2011-08-26
[FONT=Verdana]Well, now that part seems to have worked (thanks). However, I am having trouble following the next step:

[/FONT][FONT=Verdana]Then add this to xorg.conf (or drop into  /usr/lib/X11/xorg.conf.d/99-multitouch.conf on Lucid or  /usr/share/X11/xorg.conf.d/99-multitouch.conf on Maverick and later). [/FONT]
[FONT=Verdana]Section "InputClass"     MatchIsTouchpad "true"     Identifier "Multitouch Touchpad"     Driver "multitouch" EndSection

I don't have 99-multitouch.conf in that folder.


[/FONT]

---

### Post by sandyd on 2011-08-26
> **Dan Delano said:**
> [FONT=Verdana]Well, now that part seems to have worked (thanks). However, I am having trouble following the next step:

[/FONT][FONT=Verdana]Then add this to xorg.conf (or drop into  /usr/lib/X11/xorg.conf.d/99-multitouch.conf on Lucid or  /usr/share/X11/xorg.conf.d/99-multitouch.conf on Maverick and later). [/FONT]
[FONT=Verdana]Section "InputClass"     MatchIsTouchpad "true"     Identifier "Multitouch Touchpad"     Driver "multitouch" EndSection

I don't have 99-multitouch.conf in that folder.


[/FONT]
```

[FONT=Verdana]Section "InputClass"     
MatchIsTouchpad "true" 
    Identifier "Multitouch Touchpad"     
Driver "multitouch" 
EndSection[/FONT]
```

if /etc/X11/xorg.conf exists, thats good.

If it doesn't. boot to recovery mode, and run
```

Xorg -configure
```

That should generate a sutible xorg.conf for you, and you can add the multitouch config into the xorg.conf.

---

### Post by Dan Delano on 2011-08-26
/etc/X11/xorg.conf exists. Is this where I should be adding that text?

fyi here is what is in /etc/X11/xorg.conf

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection


The instructions say to go to  /usr/share/X11/xorg.conf.d/99-multitouch.conf which is what does not exist. /usr/share/X11/xorg.conf.d exists, and it has files in it which appear to have similar naming schemes (for example 50-vmmouse.comf but 99-multitouch.conf does not exist

---

### Post by sandyd on 2011-08-26
> **Dan Delano said:**
> /etc/X11/xorg.conf exists. Is this where I should be adding that text?

fyi here is what is in /etc/X11/xorg.conf

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection


The instructions say to go to  /usr/share/X11/xorg.conf.d/99-multitouch.conf which is what does not exist. /usr/share/X11/xorg.conf.d exists, and it has files in it which appear to have similar naming schemes (for example 50-vmmouse.comf but 99-multitouch.conf does not exist
it says you can add it to xorg.conf.

---


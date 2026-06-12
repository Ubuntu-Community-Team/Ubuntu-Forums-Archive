---
title: "n00b has two x11 folders?"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by zerolgk on 2009-07-10
hey and thanks,
so i made the jump to ubuntu (9.04) the other night and ive been having some trouble with my nvidia settings. when i tried to use the gksudo gedit /etc/x11/xorg.config it came up blank, which i thought was weird until i looked in the filesystem and found two x11 folders. ](*,)
one is empty and un-deleteable, and the other wont let edit the file. 
any help would awesome.

---

### Post by kaotikzen on 2009-07-10
Are you sure you aren't looking for */etc/X11/xorg.conf*?

I don't think I've ever used any distribution of linux where the X11 folder was "x11" or the config file being name xorg.config.

The xorg.conf file will still be empty though, since later versions of X supports "hotplugging".  Editing the xorg.conf file is, from all appearances, deprecated.

What preferences were you trying to set?  Perhaps I can help you further.

---

### Post by earthpigg on 2009-07-10
linux is case sensitive -- if you where following some directions from a website that told you to do something involving /etc/_**X**_11/ and you entered /etc/_**x**_11/, then that could explain your issue :)

---

### Post by zerolgk on 2009-07-10
> **kaotikzen said:**
> Are you sure you aren't looking for */etc/X11/xorg.conf*?

I don't think I've ever used any distribution of linux where the X11 folder was "x11" or the config file being name xorg.config.

The xorg.conf file will still be empty though, since later versions of X supports "hotplugging".  Editing the xorg.conf file is, from all appearances, deprecated.

What preferences were you trying to set?  Perhaps I can help you further.

word, youre right. there is an "X11" folder and an "x11," the latter being empty. ultimately id like for my resolution settings to stick  after a reboot, and ive read that edit the xorg.conf file might help.

i did notice that the subsection "display" is missing.

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

so, if im not mistaken, i should change that to:

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
SubSuection "Display"
     Mode          "1280x800_60"
EndSubSection             
EndSection


maybe? thanks again.

*maybe not. Parsing error=fail...

---

### Post by earthpigg on 2009-07-10
zerolgk:

> Editing the xorg.conf file is, from all appearances, deprecated.

'depreciated' is another way of saying 'this crap dont matter any more, but it is still around for backward compatibility purposes.... dont bother with it.' :P

try changing your nvidia settings around in here:

```
sudo nvidia-settings
```

it opens the same window as system -> administration -> NVIDIA X Server Settings...

...but opens it *_as root_*, meaning you will be able to save changes. naturally, it is essential that you 'save to X configuration file'. <-- i only say that because i myself have made that error.

---

### Post by Rocdufer on 2009-11-18
I have something even more surprising. I recently upgrade from 8.04 to 9.10 Karmic Koala. I have "mediaplayerconnectivity" add-on in firefox 3.5.5, and, after trying to play an mp3 web file, it says it can not find "gmplayer". That was weird, because the "mediaplayerconnectivity wizard" found the gmplayer at first. Looking for gmplayer by terminal, however, I found many instances of gmplayer in many X11 "nested folders".  As I remember, I installed gmplayer from synaptic package manager, but now does not appear in this package list. Mmmm. I guess this is a problem with the file system for this Ubuntu version....something like a..bug. Perhaps X11 has a pointer to itself. Does any body find the same trouble? Any work around?

---


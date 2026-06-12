---
title: "[SOLVED] Xming Question / Full Desktop Environment"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by BassKozz on 2007-11-21
I've installed SSH and I got Xming working :D
But I was woundering if I can use Xming to display my "full desktop environment" ?

I am looking to use Xming as a VNC replacement sorta, since I [can't seem to get TightVNC to work properly :(](http://ubuntuforums.org/showthread.php?t=618937), is it possible to use Xming to get the "full desktop environment", or am I barking up the wrong tree?
TIA,
-BassKozz

---

### Post by BassKozz on 2007-11-23
Figured it out thanks to this post: [https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

All I had to do was replace the code in **~/.vnc/xstartup** with ```
##!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid navy # Choose your color
x-window-manager &
{
 (gnome-panel 2> /dev/null &)
}
xterm &
```And now I simply run "**~/.vnc/xstartup**" from Putty, and up comes the desktop :)

---


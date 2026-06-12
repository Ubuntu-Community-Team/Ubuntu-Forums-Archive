---
title: "Lubuntu 14.10 vnc not working"
date: 2015-03-06
forum: Networking &amp; Wireless
---

### Post by john364 on 2015-03-06
In a nutshell upgraded my file server from Lubuntu 11.10 to 14.10.
This all worked fine with Lubuntu 11.10
I even formted and installed Lubuntu 14.10 from scratch and the same thing happens.


I have installed x11vnc
I have auto login setup as its on a headless machine.
Created ~/.config/autostart/myvncserver.desktop

Which contains:
[Desktop Entry]
Encoding=UTF-8
Version=0.9.4
Type=Application
Name=server
Comment=
Exec=**x11vnc -xkb -usepw -display :0 -forever -shared**
StartupNotify=false
Terminal=false
Hidden=false


VNC works....
After 5 minutes VNC seems to be unresponsive the screen is frozen except you can move the mouse. You can't click anything.
Any suggestions?

---

### Post by andrew-codrington on 2015-03-22
> **john364 said:**
> In a nutshell upgraded my file server from Lubuntu 11.10 to 14.10.
I even formatted and installed Lubuntu 14.10 from scratch and the same thing happens.
..
VNC works....
After 5 minutes VNC seems to be unresponsive the screen is frozen except you can move the mouse. You can't click anything.
Any suggestions?

No suggestions, but I've been seeing similar. 
Just reinstalled a machine with Lubuntu 14.10.
I connect to X11vnc from a Mac using native OSX Yosemite Screen Sharing.

Things connect, work fine, then after I come back it is locked up. As above, cursor moves around in response to my remote movements, but clicks don't take effect.
Sometimes the Screen Sharing app runs away with the Macbook CPU too.

I still haven't isolated the problem - ubuntu or OSX - but just tried disabling LightLocker on the Ubuntu system since that caused lots of trouble for me in 14.04.

---

### Post by andrew-codrington on 2015-03-24
> **andrew-codrington said:**
> 
I still haven't isolated the problem - ubuntu or OSX - but just tried disabling LightLocker on the Ubuntu system since that caused lots of trouble for me in 14.04.

No lockups since I disabled Lightlocker.

---


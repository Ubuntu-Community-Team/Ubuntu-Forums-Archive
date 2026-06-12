---
title: "SSH + VNC = Blank display"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by joberly on 2008-04-28
Ok everyone.... here goes.

I have setup SSH and VNC (openssh and tightvnc on the server). I can login from the remote computer tunnelling through SSH and VNC just fine, however the VNC display is a grey background and that is all. 

The FIRST time I logged in with VNC, it had 2 terminal windows open. I closed the two windows and now they do not come back up.

Any ideas?

Using Putty and Tight VNC on the client computer. Putty is setup to forward X11 for display 1. (because I started the vncviewer :1 on the server)


My .xstartup file is as follows:


#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
gnome-session &


However, gnome does not run, just a solid grey background.

---

### Post by joberly on 2008-04-28
bump

---

### Post by RiMTrO on 2008-05-21
Having the same problem, hope to find an answer soon

---


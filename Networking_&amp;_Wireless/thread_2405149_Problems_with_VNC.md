---
title: "Problems with VNC"
date: 2018-11-01
forum: Networking &amp; Wireless
---

### Post by betsita on 2018-11-01
Hello, I am running ubuntu 18.04 and just sintalled a VNCserver on Gnome.

To do it, as it was the first time I tried it, I read an online guide, but there were a couple of points uncomplet or missing.

The results is I have the VNC server installed and I can connect to it, but when I do it from my Android tablet it only appears a grey screen.

This is the content of my config file:
> 
#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession


Also I killed all the running sesions and created a new one with "sudo vncserver -geometry 1280x720 -depth 24", but its the same result.

Help please

Thanks in advance

---

### Post by slickymaster on 2018-11-01
Thread moved to **Networking & Wireless** for a better fit

---


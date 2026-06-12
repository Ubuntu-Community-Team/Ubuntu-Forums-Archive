---
title: "VNC performance"
date: 2005-11-28
forum: Networking &amp; Wireless
---

### Post by analox on 2005-11-28
I test the performance of Sharing Desktop of a computer running Ubuntu (using vino-server) and a computer running Fedora 4 (using vncserver) from another remote desktop. It turns out that the Fedora one runs much better in term of speed, graphic quality :rolleyes:  and nice mouse pointer :D 

Then I try to replace vino-server by VNC server on Ubuntu (by Synaptic), but after running 
> vncserver :2
the VNC window viewd by VNCviewer has only one terminal and no desktop displayed like what in vino-server.
The xstartup script is quite different between 2 computers. I post it here for you to take a look
In Fedora:
> !/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
twm &
startx
In Ubuntu:
> !/bin/sh
exec /etc/vnc/xstartup
xrdb $HOME/.Xresources

xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &

Have you guys encounter this difference in performance before? And do you think if VNC server can open a new desktop (with taskbar, menu) for each vnc connection like what I see in Fedora?
cheers :D

---


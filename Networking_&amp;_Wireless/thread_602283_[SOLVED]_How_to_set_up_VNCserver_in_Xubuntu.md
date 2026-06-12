---
title: "[SOLVED] How to set up VNCserver in Xubuntu"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by IanB2 on 2007-11-04
I've successfully had VNCviewer/server running between to Ubuntu boxes, but then most of it is built into Ubuntu and can be done via a GUI. It works really well.

I'm now trying to connect to an old PC which is running Xubuntu. I've installed VNCserver4 on Xubuntu and can ssh into the machine from ubuntu. However, when I run vncviewer from a terminal in Ubuntu I don't see the desktop but just a grey screen with a cross.

I've attempted to modify the xstartup file on my xubuntu box to try to fix the problem but I'm struggling to understand what to do and what to add so I can see my xubuntu desktop when I vnc from ubuntu. Can anyone help please?

---

### Post by IanB2 on 2007-11-04
As a thought ...... should I install the gnome desktop to gain the extra functionality that I'm looking for? I'm reluctant to do this as I'm short of disk space and the machine only has 192MB ram.

Due to the light weight nature of Xubuntu (which runs really nicely on this 8 year old PC), is Xubuntu in territory that newbies should avoid?

---

### Post by IanB2 on 2007-11-06
I'd like to thank and recommend Chess Podcast episode 51 at Linux Reality.

I updated the xstartup file in the .vnc directory to the following:

#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &

# twm &

xfwm4 --display :1.0 &
xfce4-panel --display :1.0 &
xfdesktop --display :1.0 &


I was then able to ssh into the xubuntu box, start the vncserver and then connect and view the xubuntu desktop from my ubuntu laptop.

---


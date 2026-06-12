---
title: "Jaunty tightvncserver grey screen"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by Blond_Knight on 2009-08-24
Hey guys I need some help here I hope somebody knows how to fix this.  
In Ibex I used tightvncserver and tightvnc-java on port 80(lan only) and had the full gnome desktop.
Now I upgrade to Jaunty, launch vncserver with the same arguments and all I get is the grey screen.
Ive tried editing the xstartup file to no avail.
Anyone got this working?

---

### Post by Blond_Knight on 2009-08-24
OK I have a resolution for this.  It was broken in earlier version, then fixed in Ibex, now its broken again.
At any rate:

1. edit your ~/.vnc/xstartup to read:

```
unset SESSION_MANAGER
gnome-session &

xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
```
That gets you the desktop, but the keymap is corrupted, you cant type anything but gibberish some problem in Gnome apparently.  So...

2. Login to the effected server locally or through SSH and enter:

```
gconftool --set /desktop/gnome/peripherals/keyboard/kbd/layouts --type List --list-type String [aa]
```

Kill the vncserver session and restart

---


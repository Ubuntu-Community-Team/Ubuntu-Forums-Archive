---
title: "[for help]vnc4server has something wrong"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by leetom on 2009-08-16
I installed vnc4server,but it can't provide gnome for remote user(I use the same account) if I login with gnome.remote vncviewer login with 'could not acquire name on session bus'.Then cairo-dock and hotkeys can be used to run app but there's no gnome panel.My vnc4server xstartup is followed.things are all OK if I login Shell instead of gnome.
A nother question is how can I make remote user connected vnc at gdm? some vnc servers are like this.you can login with your own account, not the one that run vnc4serve.
```
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 800x600+10+10 -ls -title "$VNCDESKTOP Desktop" &
#twm &
gnome-session &
```

---


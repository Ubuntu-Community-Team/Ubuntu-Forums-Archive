---
title: "Xubuntu remote acces"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by Gryphin on 2007-06-04
Hi!
Only recently have my friend switched to Xubuntu and we can't find reomte desktop settings. In Ubuntu it is in System > Preferences menu. Where can we find it in Xubuntu? 

Are there any other way to allow remote users to acces Xubuntu desktop?

---

### Post by amireldor on 2007-06-27
hmm, the command System->Preferences->Remote Desktop launches something called "vino-preferences"
I ran it on my xfce and got the same dialog, but it wasn't working for xfce (installed xubuntu-desktop package over a regular ubuntu machine)
hmm...

I think on gnome ubuntu, the vncsever is built in into the desktop. This is not the caes in a XFCE desktop. You CAN however run a vncserver on the Xubuntu machine and connect remotely from a differnet machine and start a XFCE session, But that means that there's no desktop sharing between the local and remote XFCE sessions (which may be fine in most occasions).
You can however start a minimal window manager on the xubuntu machine and connect to the localhost VNC server and then the session can be shared.

I suggest running the vnc session over SSH, not only for security, but also because it enables compression and makes image data go faster.

Another solution is installing an NX server (on the Xubuntu machine) which is also cool and easier to setup IMHO than setting up VNC over SSH.

---

### Post by forpeterssake on 2007-07-14
[This thread](http://ubuntuforums.org/showthread.php?t=487737&highlight=xubuntu+remote) dealt with some of the same issues, connecting from a WinXP box using tightVNC. Here's how he solved it:

> **beengone said:**
> Got it!   In case anyone wants to do this running Feisty Xubuntu and vnc4server:

edit the file /etc/vnc/xstartup to look like this:

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



Next, start the server session like so:

vnc4server -extension XFIXES -depth 24 -geometry 1024x768


That should get you up and running with xfce/vnc4server.  I connected via tightvnc and it all works perfectly.

Dan J.

---

### Post by amireldor on 2007-07-15
on my VNC xstartup script i just start **xfce4-session &** instead of running xfwm, xfdesktop, and the xfce panel independently.

my ~/.vnc/xstartup:
```

#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
#exec /etc/X11/xinit/xinitrc
#exec gnome-session&
exec xfce4-session&
#exec fluxbox&

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey

```

---


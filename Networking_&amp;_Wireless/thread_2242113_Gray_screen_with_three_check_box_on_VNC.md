---
title: "Gray screen with three check box on VNC"
date: 2014-08-30
forum: Networking &amp; Wireless
---

### Post by rajagopal3 on 2014-08-30
[COLOR=#000000]*For the past 2 days i try to install gui on ubuntu server provided by amazon-ec2 1 year free tier. But i got only grey screen with 3 check box. I read so many posts but nothing helps. pls help me.*[/COLOR]

[COLOR=#000000]*Here is .vnc/xstartup:*[/COLOR]

```
[COLOR=#000000]*#!/bin/sh*[/COLOR]


[COLOR=#000000]*# Uncomment the following two lines for normal desktop:*[/COLOR]
[COLOR=#000000]*unset SESSION_MANAGER*[/COLOR]
[COLOR=#000000]*# exec /etc/X11/xinit/xinitrc*[/COLOR]
[COLOR=#000000]*gnome-session --session=gnome-classic &*[/COLOR]


[COLOR=#000000]*[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup*[/COLOR]
[COLOR=#000000]*[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources*[/COLOR]
[COLOR=#000000]*xsetroot -solid grey*[/COLOR]
[COLOR=#000000]*vncconfig -iconic &*[/COLOR]
[COLOR=#000000]*#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &*[/COLOR]
[COLOR=#000000]*#x-window-manager &*[/COLOR]


```
[COLOR=#000000]*Here is the vnc 1.log: *[/COLOR]```


[COLOR=#000000]*ubuntu@ip-172-31-34-182:~$ cat /home/ubuntu/.vnc/ip-172-31-34-182:1.log*[/COLOR]


[COLOR=#000000]*Xvnc Free Edition 4.1.1 - built Jan 14 2013 22:28:40*[/COLOR]
[COLOR=#000000]*Copyright (C) 2002-2005 RealVNC Ltd.*[/COLOR]
[COLOR=#000000]*See *[/COLOR][http://www.realvnc.com]("http://www.realvnc.com/")[COLOR=#000000]* for information on VNC.*[/COLOR]
[COLOR=#000000]*Underlying X server release 40300000, The XFree86 Project, Inc*[/COLOR]




[COLOR=#000000]*Sat Aug 30 16:45:05 2014*[/COLOR]
[COLOR=#000000]*vncext: VNC extension running!*[/COLOR]
[COLOR=#000000]*vncext: Listening for VNC connections on port 5901*[/COLOR]
[COLOR=#000000]*vncext: created VNC server for screen 0*[/COLOR]
[COLOR=#000000]*error opening security policy file /etc/X11/xserver/SecurityPolicy*[/COLOR]
[COLOR=#000000]*Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!*[/COLOR]
[COLOR=#000000]*Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!*[/COLOR]
[COLOR=#000000]*Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from l ist!*[/COLOR]
[COLOR=#000000]*Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!*[/COLOR]
[COLOR=#000000]*Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!*[/COLOR]
[COLOR=#000000]*Could not init font path element /usr/share/fonts/X11/Type1/, removing from list !*[/COLOR]
[COLOR=#000000]*Could not init font path element /usr/share/fonts/X11/75dpi/, removing from list !*[/COLOR]
[COLOR=#000000]*Could not init font path element /usr/share/fonts/X11/100dpi/, removing from lis t!*[/COLOR]
[COLOR=#000000]*gnome-session-is-accelerated: No composite extension.*[/COLOR]
[COLOR=#000000]*gnome-session-check-accelerated: Helper exited with code 256*[/COLOR]
[COLOR=#000000]*gnome-session-is-accelerated: No composite extension.*[/COLOR]
[COLOR=#000000]*gnome-session-check-accelerated: Helper exited with code 256*[/COLOR]


[COLOR=#000000]*** (process:20160): WARNING **: software acceleration check failed: Child proces s exited with code 1*[/COLOR]


[COLOR=#000000]*** (gnome-session:20160): CRITICAL **: We failed, but the fail whale is dead. So rry....*[/COLOR]


[COLOR=#000000]*Sat Aug 30 16:45:17 2014*[/COLOR]
[COLOR=#000000]*Connections: accepted: 0.0.0.0::62050*[/COLOR]


[COLOR=#000000]*Sat Aug 30 16:45:18 2014*[/COLOR]
[COLOR=#000000]*SConnection: Client needs protocol version 3.8*[/COLOR]


[COLOR=#000000]*Sat Aug 30 16:45:20 2014*[/COLOR]
[COLOR=#000000]*SConnection: Client requests security type VncAuth(2)*[/COLOR]


[COLOR=#000000]*Sat Aug 30 16:45:24 2014*[/COLOR]
[COLOR=#000000]*VNCSConnST: Server default pixel format depth 16 (16bpp) little-endian rgb565*[/COLOR]


[COLOR=#000000]*Sat Aug 30 16:45:25 2014*[/COLOR]
[COLOR=#000000][I]VNCSConnST: Client pixel format depth 24 (32bpp) little-endian rgb888
[/I][/COLOR]
```

---

### Post by Toz on 2014-08-30
*Moved to Networking & Wireless*.

I found [this bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1251281") which looks related.

EDIT: [Another link]("http://www.havetheknowhow.com/Configure-the-server/Install-VNC.html").

---


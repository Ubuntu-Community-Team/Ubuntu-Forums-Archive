---
title: "Remote Login with ssh to view Ubuntu screen"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by unix_user on 2010-11-25
Hi,
I am trying to connect to Ubuntu server from my Windows Laptop. I have Cygwin installed and want to view Ubuntu Server screen remotely.

Approach 1:
1. Start Xming 
2. putty to Ubuntu with X11 forwarding 
3. ubuntu> gedit &                    # brings up editor fine on Windows
4. gnome-panel &                      # brings up blank panels at top and bottom of screen


Approach 2
1. Installed cygwin
2. WinCygwin>  ssh -X -C -c blowfish mylogin@myserver  gnome-panel
Warning: untrusted X11 forwarding setup failed: xauth key data not generated
Warning: No xauth data; using fake authentication data for X11 forwarding.
connect /tmp/.X11-unix/X0: No such file or directory

(gnome-panel:14477): Gtk-WARNING **: cannot open display: localhost:11.0

Is there any other setup missing, X11 forwarding is enabled on Ubuntu.

Please advise if I have missed any steps,

Thanks in advance,

---

### Post by Foxheadz on 2010-11-25
Well if the computers are on the same network you could just get a VNC client on the pc and connect to the ubuntu via the built in Remote desktop viewer app (applications>internet>remote desktop viewer

---


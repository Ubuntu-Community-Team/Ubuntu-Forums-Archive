---
title: "nvidia says it's easy"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by nnjond on 2009-10-31
Hi,

I want my old res back:  1600x1200 @ 75Hz

I'm told to  simply edit my X configuration file; "Run nvidia-xconfig as Root". 

Presumably i can do it from a terminal do you know the command/procedure ?

Thanks

---

### Post by Liolikas on 2009-10-31
sudo nvidia-xconfig

---

### Post by nnjond on 2009-10-31
Oh,oh. I've been here before; my res has dropped to 600x480 and the gui if it's working ok is to big to use for my display

---

### Post by Liolikas on 2009-10-31
You can also try to manually edit: /etc/x11/xorg.conf (I hope you still have it at all it is quite old school)
Not very easy, but if you loook google/forum search for examples you can do it.

---

### Post by nnjond on 2009-10-31
Thanks for your help.

I have found this:

nnjond@den-desktop:~$ cd /etc/X11
nnjond@den-desktop:/etc/X11$ ls
app-defaults             xkb                               Xresources
cursors                  xorg.conf                         Xsession
default-display-manager  xorg.conf-backup-091031201327     Xsession.d
fonts                    xorg.conf.failsafe                Xsession.options
X                        xorg.conf_xconfig.20091031212303  XvMCConfig
xinit                    xorg.conf_xconfig.20091031212318  Xwrapper.config
nnjond@den-desktop:/etc/X11$ etc/X11

Am i right in thinking i manually open one of these files and add the lines at the apropriate places ?

---


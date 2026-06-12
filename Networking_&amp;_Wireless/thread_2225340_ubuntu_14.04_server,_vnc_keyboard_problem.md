---
title: "ubuntu 14.04 server, vnc keyboard problem"
date: 2014-05-21
forum: Networking &amp; Wireless
---

### Post by mcheung63 on 2014-05-21
Hi All
   ubuntu 14.04 server, vnc keyboard problem: when i press d, it minimize all windowes. when i press s, it popup the start menu.
thanks
from Peter (cmk128@hotmail.com)

---

### Post by BillyBarty on 2014-08-21
I am having this same issue.  Works fine in 13.10, but 14.04 gives me the issue.

---

### Post by BillyBarty on 2014-08-21
I fixed this from information I found here: [https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/658723](https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/658723).  Specifically, what I did was go to the physical machine that I was VNC'ing to, open dconf-editor, and search for "keybind" (since I was at the physical machine I had no problem typing the "d").  This enabled me to find org->gnome->desktop->wm->keybindings.  In the right pane for org->gnome->desktop->wm->keybindings, I then looked for all settings that included <Super> and deleted those settings.  I then killed my VNC server, started it again, and connected with RealVNC (my usual client from Windows).  No unwanted behavior typing "d" or "s" (or anything else) now!

---

### Post by Larry_Irwin on 2014-08-29
I think this will implement removal of all "Super" key bindings for all vncserver instances site-wide.
[i.e. all those problems with "s", "m", "h", etc. that get in the way of vnc client applications]

```

# /etc/dconf/db/gdm.d/10-nosuperkey-settings
#
# This file is a site config file to disable "Super/Windows" key bindings
# so that vnc clients can operate properly.
#
# use "dconf update" to incorporate into db the first time
#

[org/gnome/desktop/wm/keybindings]
maximize='' 
minimize='' 
move-to-workspace-down=['<Control><Shift><Alt>Down']
move-to-workspace-up=['<Control><Shift><Alt>Up']
panel-main-menu=['<Alt>F1'] 
switch-applications=['<Alt>Tab']
switch-group=['<Alt>Above_Tab'] 
switch-input-source=''
switch-input-source-backward='' 
switch-to-workspace-down=['<Control><Alt>Down']
switch-to-workspace-up=['<Control><Alt>Up']
unmaximize=['<Alt>F5']

```

---


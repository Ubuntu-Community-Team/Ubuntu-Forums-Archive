---
title: "VNC Keyboard issue"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by arbulus on 2008-03-07
Here's my setup:  I have a box running Ubuntu Gutsy acting as a headless file server.  My personal desktop machine is also running Ubuntu Gutsy.  Installed tightvnc on the file server so I can use my personal desktop to manage it.  When I connect using either vncviewer or Terminal Server Client, I have a serious issue with the keyboard.  Everything else is perfectly responsive, but when I try to type anything, i get mis-matched keys.  Like when I type a "v" i get a comma, I type an "s" and I get a "b."  It's all gobbeldygook. 

The odd thing is this:  when I first connect to the file server, I have a plain x window interface with just xterm running.  I type "gnome-session" to start a gnome interface.  When I'm in the x window with xterm interface, the keyboard works just fine. But as soon as I start gnome, it goes haywire. 

I tried resetting to defaults in the gnome keyboard settings, and that did nothing.  Killing and restarting the vncserver does nothing to help.

Does anyone know what I can do to get the file server to properly interpret my keyboard input?

---

### Post by arbulus on 2008-03-09
Bump

---

### Post by abhi.datt on 2008-03-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/feisty/+source/vino/+bug/112955](https://bugs.launchpad.net/ubuntu/feisty/+source/vino/+bug/112955) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				There seems to be a bug that is spilling from fiesty to gutsy. For detailed discussions you can go the url mentioned below. To save you time, here is how you should edit your  $HOME/.vnc/xstartup file:

#!/bin/sh

xrdb $HOME/.Xresources
gnome-wm &
gnome-panel &
nautilus --no-default-window &
gnome-cups-icon &
gnome-volume-manager &
xterm &



Save it and restart vncserver

[https://bugs.launchpad.net/ubuntu/feisty/+source/vino/+bug/112955](https://bugs.launchpad.net/ubuntu/feisty/+source/vino/+bug/112955)

---

### Post by abhi.datt on 2008-03-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/vino/+bug/112955/comments/31](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/112955/comments/31) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Even better workaround:
[https://bugs.launchpad.net/ubuntu/+source/vino/+bug/112955/comments/31](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/112955/comments/31)

---


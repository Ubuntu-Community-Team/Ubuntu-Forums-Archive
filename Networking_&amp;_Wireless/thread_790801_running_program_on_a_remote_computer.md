---
title: "running program on a remote computer"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by ticklj on 2008-05-11
Gnome-I am trying to run a program on a remote computer with the
output displayed on the local-ubuntu-gnome.I am having many problem
but they may be involved with verizon-dsl firewalls etc. These are
not the reason for this posting. I have read beaucoup postings
Xhost DISPLAY etc. My question is more simple. Exactly WHERE do I expect to see the graphic output? Where is the x-window? Does it
get created when the application sends output. What I have is a terminal window which I ssh'd to do the DISPLAY thing and start
the application. That sits on the GNOME desktop. I would think I
would need to replace the desktop by a full screen X-window. I cant
believe the output is to go to that little terminal. I should add that this is my first GNOME experience so if this is obvious do forgive me.
Confused!

---

### Post by Whiffle on 2008-05-11
All you should need to do is:

ssh -X user@remotehost

and then run the app, assuming X11 forwarding is enabled on the host.  It should show up on your desktop just like any other program.

---

### Post by ticklj on 2008-05-12
That worked well. thanks. I have to find out what -X does. Also got my
questioned that is a window is opend up on the desktop.

---


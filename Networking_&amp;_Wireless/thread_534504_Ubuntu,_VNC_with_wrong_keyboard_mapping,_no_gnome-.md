---
title: "Ubuntu, VNC with wrong keyboard mapping, no gnome-settings-daemon"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by amireldor on 2007-08-25
VNC (through SSH), mouse works fine but keyboard mapping is not correct. For example, I type "I like spam" and it outputs "gsdkjk1jk5999".
I believe this is because Gnome does something funny, because if I start fluxbox instead of Gnome the keyboard input is fine (even on stuff like gnome-terminal) but if I start Gnome (i.e. with gnome-session instead of fluxbox on my VNC xstartup file) there is *funny business*.

Also, when I run Gnome, even when sitting infront of the computer (i.e. not remotely with VNC), and I try to get to the keyboard setting, it says that it is unable to load the gnome-settings-daemon (although it does run on the background somewhere). Is it somehow related to the funny business problem when running Gnome under VNC?

This was previous discussed but I haven't found a proper solution yet.

I can also run fluxbox on the VNC server and then fire up gnome-panel and nautilus but that's just too ugly for me as a workaround.

---

### Post by stooshbunutu on 2008-03-01
you can run gnome settings daemon manually by pressinf Alt+F2 to open a run dialogue

Type:
```
gnome-settings-daemon
```
and then click on run.

Hope this helps, im not too sure bout the other stuff

---

### Post by LoneSt4r on 2008-04-30
> **stooshbunutu said:**
> you can run gnome settings daemon manually by pressinf Alt+F2 to open a run dialogue

Type:
```
gnome-settings-daemon
```
and then click on run.

Hope this helps, im not too sure bout the other stuff

I tried this (running vncserver direct on a local LAN).  I see the icons in the toolbar change briefly, then revert the the "non ubuntu" default.  It looks like gnome-settings-daemon just does not stick.

I am running compiz on the server.  Could that be related?

Thanks!

---

### Post by StoneUSA7 on 2008-05-02
I'm having this same issue logging into my headless server.  I upgraded a few days ago from 7.10 server to 8.04 server, and it went smoothly.  It doesn't seem to happen when I log in locally to the machine, only when I VNC in.  In the worst case scenario, I'll get this error:

"Gnome Settings Daemon restarted too many times"

Which is actually better because then it stays on the ugly default icons/panel and doesn't eat up all the bandwidth trying to reload the icons/panel every 2 seconds.

This happens across multiple user accounts, and even after I reset all the gnome settings by deleting the corresponding folders in the user home folder.

Maybe uninstall and reinstall gnome-settings-daemon?  I just don't want to break my gnome install.

---

### Post by charmcity on 2008-05-06
Hi,

I'm having the same problem.   I get the gnome settings daemon error box upon connection / login to gnome.  Can't type without it coming out jibberish, otherwise everything seems to work fine.  

Any help is appreciated very much

Thanks very much,
Tom

---


---
title: "Trouble installing a plug-in"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by zookrider on 2009-10-19
I'm trying to install a third party plug-in for Pidgin, and when I download it I get the following error:

> /tmp/pidgin-facebookchat-1.61.deb could not be saved, because you cannot change the contents of that folder.

Change the folder properties and try again, or try saving in a different location.

If I try to save it the package installer says:

> Error: Dependency is not satisfiable: libjson-glib-1.0-0 (>= 0.7.6)

I have no idea what this means or how to fix it. I googled the message and could not find an applicable fix. Please help.

I'm running Jaunty on a Toshiba Satellite A135.

---

### Post by LowSky on 2009-10-19
save the file to another location, like the desktop.
and that version of the facebook addin, wont work with jaunty, its for Karmic (9.10). sorry to tell you that..
[http://packages.ubuntu.com/karmic/libjson-glib-1.0-0](http://packages.ubuntu.com/karmic/libjson-glib-1.0-0)

---

### Post by zookrider on 2009-10-19
> **LowSky said:**
> save the file to another location, like the desktop.
and that version of the facebook addin, wont work with jaunty, its for Karmic (9.10). sorry to tell you that..
[http://packages.ubuntu.com/karmic/libjson-glib-1.0-0](http://packages.ubuntu.com/karmic/libjson-glib-1.0-0)

Bummer. Thanks for the help.

---

### Post by zookrider on 2009-10-19
I just checked and that plugin was originally uploaded in '07 so I can't imagine that it wouldn't work with Jaunty. Also, I have the software package (little cardboard box icon) saved to the desktop right now. When I double-click on it is when I get the following:

> Error: Dependency is not satisfiable: libjson-glib-1.0-0 (>= 0.7.6) 

---

### Post by CaptainMark on 2009-10-19
the jaunty facebook plugin is in synaptic, ive been using it for 6 months no probs

---

### Post by zookrider on 2009-10-19
> **CaptainMark said:**
> the jaunty facebook plugin is in synaptic, ive been using it for 6 months no probs

Awesome, worked like a charm, thanks.

---


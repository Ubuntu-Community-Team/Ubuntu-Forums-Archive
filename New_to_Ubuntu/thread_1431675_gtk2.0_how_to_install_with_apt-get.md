---
title: "gtk2.0 how to install with apt-get"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by kernelnewbie1 on 2010-03-16
i want to install gtk+2.0 latest version i.e 2.18 or so
i downloaded  gtk and configured it , and ended up with

"checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.21.3    atk >= 1.13.0    pango >= 1.20    cairo >= 1.6) were not met::
Requested 'glib-2.0 >= 2.21.3' but version of GLib is 2.20.1"


if i do sudo apt-get install libglib2.0-dev
it said latest is already installed 

Help me please !

---

### Post by MechaMechanism on 2010-03-19
What version of Ubuntu are you using?  Generally you can not mix and match Ubuntu versions.  If you would like to mix and match you are better off running Debian testing or unstable.  It is possible to mix Ubuntu versions and I have done it before myself for building from source, but Debian is light years much easer in this regard.

---

### Post by robot_chicken_parm on 2010-04-30
hi.  i was wondering about this too.  i didnt want to just apt-get gtk because i dont know much about it but i have been coming across things that im reading would be better with gtk2 like certain themes and their components and diff programs like qalculate.  im pretty sure that i need some kind of gtk2 for the gui benefits of certain programs.  thanks :)

---

### Post by anewguy on 2010-04-30
Why not simply go to Synaptic Package Manager and do a search on GTK, find the things you want, mark them for install and apply?

Dave ;)

---

### Post by MechaMechanism on 2010-04-30
Uh, well Gnome for all intents and purposes is GTK.  So the only reason for the dev versions is for compiling from source.

---


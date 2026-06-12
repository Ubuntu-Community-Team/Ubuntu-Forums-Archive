---
title: "trying to install tar.gz file, hit a snag"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by leavitodeaver on 2010-03-03
i'm probably over my head here, but i'm trying to install the newest version of desmume.  i downloaded the file, ran the ./configure, and it spat this out:

config.status: executing po/stamp-it commands
grep: po/Makefile.in: No such file or directory
config.status: error: po/Makefile.in.in was not created by intltoolize.

how do i fix this so i can finish installing? i've never messed with anything but the add/remove programs thing, so assume i'm almost completely useless. thanks!

---

### Post by leavitodeaver on 2010-03-03
i'm running karmic koala and already had to get 2 other packages from synaptic, if that helps, zlib and antigrain

---

### Post by nothingspecial on 2010-03-03
```
sudo apt-get install build-essential autoconf automake libgtk2.0-dev libglu1-mesa-dev libsdl1.2-dev libglade2-dev libgtkglext1-dev gettext zlib1g-dev libosmesa6-dev intltool libagg-dev libasound2-dev
``` and try again

---

### Post by leavitodeaver on 2010-03-03
you sir, are a gentleman and a scholar.  i'll post again if i run into anything else, but it looks to be running.  you are my best friend

---


---
title: "Install X11 version 7.4"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by kilinki on 2009-02-26
I want install Mplayer to play media files, and it request X!!. Can I install X11 7.4 from tarball.:lolflag:

---

### Post by ptn107 on 2009-02-26
X.org X server 7.4 is installed by default already in Ubuntu 8.10 (xserver-xorg 1:7.4~5ubuntu3).  Installing Mplayer should only take one command from the command line:
```
sudo apt-get install mplayer -y
```
There is no need to compile a new X server from source.

---


---
title: "Qt4 help"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by Morphaeus on 2009-03-14
I'm trying to install qt4 so I can satisfy dependencies to install ipod linux

```
victor@ristau-desktop:~$ cd /home/victor/Desktop/qt4
victor@ristau-desktop:~/Desktop/qt4$ ./configure -make

This is the Qt/X11 Open Source Edition.

shift: 1858: can't shift that many
victor@ristau-desktop:~/Desktop/qt4$ 

```

Any ideas?

thanks in advance

---

### Post by snova on 2009-03-15
You shouldn't have to compile from source (unless you know you need a newer version than is available in the repos).

Open System -> Administration -> Synaptic. Search for and install **libqt4-gui**. That should be enough for it, but post back if there are continuing errors.

---


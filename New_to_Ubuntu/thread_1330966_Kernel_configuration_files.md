---
title: "Kernel configuration files"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by SteelCore on 2009-11-18
Where are the Ubuntu kernel configuration files in both 9.04 and 9.10 (under which directory)
Thanks

---

### Post by wojox on 2009-11-18
/usr/src/

---

### Post by SteelCore on 2009-11-19
I am trying to (learn to) compile my own Linux kernel and to make it support my hardware I want to use the currently running Ubuntu configuration file.  According to the book I'm reading this file is usually named config.gz yet I couldn't find that under /usr/src/. Some more help on this is appreciated.

---

### Post by falconindy on 2009-11-19
That file, if it exists, is /proc/config.gz. In order for that file to exist, you have to elect its creation in the kernel config process. By default, Ubuntu kernels don't include this so using 'make oldconfig' is going to be a little difficult. Dive in with 'make menuconfig' and have fun!

If you'd like some extra resources, I've found [this guy's](http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/) blog to be an awesome (and thorough) tutorial on compiling clean Ubuntu kernels.

---


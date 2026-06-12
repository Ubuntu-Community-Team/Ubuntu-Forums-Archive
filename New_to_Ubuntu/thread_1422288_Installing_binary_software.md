---
title: "Installing binary software"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by SteelCore on 2010-03-05
I'm trying to install the Sleuthkit using the tar.gz file. I went thru the ./configure and make steps. Make notified that I need g++
```
../../config/depcomp: line 566: exec: g++: not found
```
now I can easily install g++ from Synaptic. The question is, after installing g++ do I need to go over ./configure and make again or just resume with 'make install'?
Thanks

---

### Post by nothingspecial on 2010-03-05
Do your self a favour and install build-essential which will install other compilation software as well if you are going to start compiling.

Yes you will have to ./configure again

---


---
title: "programs folder"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by kiridude on 2009-04-05
Can someone tell me in which directory are all my programs stored?

I am referring to programs in the synaptic manager AS WELL AS programs downloaded as tarballs.

Thanx

---

### Post by mvalviar on 2009-04-05
/bin, /usr/sbin, /usr/bin

---

### Post by Ms_Angel_D on 2009-04-05
There is no One folder which holds all an applications parts for a better understanding look here [http://www.reallylinux.com/docs/windowstolinux.shtml](http://www.reallylinux.com/docs/windowstolinux.shtml) scroll down to the part about Finding Programs on your system

---

### Post by spiderbatdad on 2009-04-05
in your terminal run:
```
which synaptic
```your programs are not all installed to the same directory. in general /usr/sbin or /usr/local/sbin but there other directories from which they can run also. Another good command is find, or locate. You many need to run updatedb before using locate.

---


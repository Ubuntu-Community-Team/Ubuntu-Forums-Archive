---
title: "X11/Xutil.h: No such file or directory"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by LAF4444 on 2010-09-11
Hi 

I am trying to install software that relies on gfortran/gcc to compile.  It hangs when it reaches gcc with an error X11/Xutil.h: No such file or directory.  I am looking for this in packages,  X11-dev,  but this will not install on my machine.  I am running Ubuntu,  my /usr/include/X11 only has bitmaps.  What  do I need to install to get Xutil.h and Xlib.h

The error:

gcc -c -g   -I/usr/include/X11 get_color_ro.c
get_color_ro.c:7:22: error: X11/Xlib.h: No such file or directory
get_color_ro.c:8:23: error: X11/Xutil.h: No such file or directory
get_color_ro.c:9:21: error: X11/Xos.h: No such file or directory

Thank you

---

### Post by lloyd_b on 2010-09-11
X11/Xutil.h and X11/Xlib.h are both part of the package "libx11-dev".  X11/Xos.h is from the package "x11proto-core-dev". 

Lloyd B.

---


---
title: "freeciv client"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by anatak on 2009-11-28
I would like to install freeciv but I am confused as what client I need.
the package manager lists 3 clients: freeciv-client-gtk , xaw3d and sdl.

I tried to google the meaning of the three clients but did not found anything that helps me decide what I need.

I run ubuntu 9.04 jaunty
can anyone explain to me the difference between the freeciv clients ?

thank you very much
anatak

---

### Post by jamieleshaw on 2009-11-28
You need freeciv-client-gtk.
It will resolve the dependencies.

> 
A package, is basically a program with metadata.
 A package management system is system or program for installing, removing and managing software dependencies, and just generally managing whats installed on your computer, Ubuntu uses the Debian Package Management System.
 A dependency is when you want to install say a music player program, but this program is **dependent** on say a playback library.
 Here I’ll explain apt-get usage a front-end to dpkg(The base Debian Package Management System).

---

### Post by anatak on 2009-11-28
thank you very much

---

### Post by bryar on 2009-11-29
I am trying to install the 2.1.9 version of Freeciv on Karmic after I got some window glitch issues with the version that is in the dependencies. I got the packages I needed to install it and got the zlib package installed but it still gave me a fail message. I was reading the config.log file to find where it went wrong. 

Heres a quote from the log:

configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE_URL ""
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:3420: result: gcc -E
configure:3440: gcc -E  conftest.c
configure:3440: $? = 0
configure:3454: gcc -E  conftest.c
conftest.c:9:28: error: ac_nonexistent.h: No such file or directory
configure:3454: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE_URL ""
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>

---


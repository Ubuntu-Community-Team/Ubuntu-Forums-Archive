---
title: "which development packages do i have to install to install xautoclick?"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by khfrekek on 2009-06-05
okay i am trying to install a program i found, xautcoclick, and in the install file, it says: "Be sure you have the proper development packages for your distribution
installed (i.e. something like xserver-xorg-dev, gtk2-dev, et cetera)." and then when i run ./configure, the build doesnt work.

does anyone know which dev packages i need to install to make this work?
thanks!

---

### Post by DBrocks on 2009-06-05
Run the ./configure again and post what happens (the entire terminal window). This will help determine what packages are missing. I'll keep looking up dependencies

---

### Post by khfrekek on 2009-06-05
okay i ran ./configure again, and it said this:


Checking for c compiler ... gcc
Checking for c++ compiler ... can't find g++
Checking for gcc as c++ compiler ... no, disabling compilation of all c++ code
Checking for GNU Make ... yes, using make
Checking for extra headers ... no
Checking for extra libraries ... no
Checking for gcc support of -MM option ... yes
Checking for inttypes.h ... yes
Checking for unistd.h ... yes
Checking for malloc.h ... yes
Checking for X11 header presence ... not found (check if the dev(el) packages are installed
Checking for X11 ... no
Checking for XTest extension ... no
No X11 found. Not building anything that depends on it

Debug symbols disabled.
All compiler warnings disabled.

Cleaning up source tree ... done

Generating config.mak ... done.

aAutoClick    : no
cAutoClick    : no
gAutoClick    : no
gAutoClick2   : no
qtAutoClick   : no

Installation to /usr/local

test: 785: ==: unexpected operator
Now type 'make' to build.



then when i run make, it says this:


make: Nothing to be done for `all'.


thanks so much for helping! :D

---


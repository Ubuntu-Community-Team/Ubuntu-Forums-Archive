---
title: "Install dpkg-dev"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by Silvr2008 on 2009-06-22
I need to install dpkg-dev so that I can install build-essentials and get my modem working to use apt-get. When I make dpkg-dev I get:

bcompat -I../lib     -c -o basecmds.o basecmds.cc
../config/depcomp: line 571: exec: g++: not found
make[2]: *** [basecmds.o] Error 127
make[2]: Leaving directory `/media/disk/dpkg-1.14.24ubuntu1/dselect'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/media/disk/dpkg-1.14.24ubuntu1/dselect'
make: *** [install-recursive] Error 1

Doesn't Ubuntu come with g++ installed?

---

### Post by Mornedhel on 2009-06-22
Nope, which is most likely why you need build-essential.

Have you tried getting the packages directly from packages.ubuntu.com ?  It can be used as a direct download mirror as a last resort.

---

### Post by jmszr on 2009-06-22
Silvr2008,

Edit: Did not read your post properly,sorry.

---

### Post by master_kernel on 2009-06-22
Mornedhel is right. You could probably copy the straight .debs (dpkg-dev and build-essential) from packages.ubuntu.com onto a flash drive and install them with dpkg -i.

---


---
title: "Ktorrent Idiot."
date: 2009-04-25
forum: New to Ubuntu
---

### Post by Spiritous on 2009-04-25
I'm A complete noob to ubuntu, i have NO IDEA How to compile this program KTorrent, Can anyone explain ? I'm stuck on ```
cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`.. 
``` When i enter it i get the error: ```
-- The C compiler identification is GNU
-- The CXX compiler identification is unknown
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
CMake Error at /usr/share/cmake-2.6/Modules/FindKDE4.cmake:84 (MESSAGE):
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in
  /home/simon/.kde/share/apps;/usr/share/kde4/apps
Call Stack (most recent call first):
  CMakeLists.txt:2 (find_package)


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.6)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

```My head hurts :(

---

### Post by o.besner on 2009-04-25
might wanna have a look at this :

[http://ktorrent.org/forum/viewtopic.php?t=2714](http://ktorrent.org/forum/viewtopic.php?t=2714)

---

### Post by mhh91 on 2009-04-25
try installing CMake or CMake-dev maybe ?


this thread really shouldn't be in this section,because complining programs isn't really for beginners :D

---

### Post by Seks on 2009-04-25
try this:

sudo apt-get update && sudo apt-get install ktorrent

---

### Post by kpkeerthi on 2009-04-25
Applications -> Add/Remove, search and install ktorrent (beware, this might pull a lot of KDE dependencies as this is a KDE application)

Any specific reason why you want to compile it yourself?

Ubuntu comes with Transmission, simple and functional. You may also try deluge if you need a bit more tweakable features. Unlike Ktorrent, deluge and transmission are made for GNOME.

---

### Post by Spiritous on 2009-04-25
> **Seks said:**
> try this:

sudo apt-get update && sudo apt-get install ktorrent

Thanks 100,000 Times! I'd +rep if I could :(

---

### Post by Spiritous on 2009-04-25
> **kpkeerthi said:**
> Applications -> Add/Remove, search and install ktorrent (beware, this might pull a lot of KDE dependencies as this is a KDE application)

Any specific reason why you want to compile it yourself?

Ubuntu comes with Transmission, simple and functional. You may also try deluge if you need a bit more tweakable features. Unlike Ktorrent, deluge and transmission are made for GNOME.

Yes... I just wanted a challenge, Obviously too much for me

---


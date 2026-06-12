---
title: "Error when installing kTorrent"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by jadavi on 2011-02-23
When I try to run this command to install ktorrent
> cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..

I get this error message

> CMake Error at /usr/share/cmake-2.8/Modules/FindKDE4.cmake:98 (MESSAGE):
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in
  /home/phr34k/.kde/share/apps;/usr/share/kde4/apps
Call Stack (most recent call first):
  CMakeLists.txt:2 (find_package)


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.8)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring incomplete, errors occurred!

Any ideas?

---

### Post by Perfect Storm on 2011-02-23
Why not install ktorrent from Ubuntu Software Center?

Also have you checked out Deluge? It's more integrated into Ubuntu (gnomes) environment: [http://deluge-torrent.org/](http://deluge-torrent.org/)


You rarely need to grab software outside Ubuntu Software Center
But if you insist on compiling yourself, the error tells you you need to install cmake.

---

### Post by jadavi on 2011-02-23
Well honestly because I am not sure where the software center is.  I know its embarrassing.  I did however google it and came up with a nice wikipedia article for reading but alas no software center. I looked through my computer and didn´t find anything either.

---

### Post by Perfect Storm on 2011-02-23
Which version of Ubuntu do you use?

If 10.10 = Applications tab ---> Ubuntu Software Center

---

### Post by jadavi on 2011-02-23
Yeah I just noticed that.  I feel like an idiot. Thanks for the info AI.

---


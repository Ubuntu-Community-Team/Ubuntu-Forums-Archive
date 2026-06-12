---
title: "Compile SMPlayer From Source?"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-06-19
I've built Mplayer from source and apparently to use smplayer with it I have to build smplayer from source as well...

so how? I've downloaded the source to my desktop but what now? I'm using jaunty x64

---

### Post by rvm4000 on 2009-06-19
From Install.txt:

> 
1) How to make a deb package
----------------------------
Be sure you have installed the following packages: libqt4-dev, zlib1g-dev,
fakeroot, build-essential, devscripts, debhelper and g++.
Now run ./create_deb.sh


BTW, 0.6.7 will fail to build on Jaunty. I suggest to compile a package from svn:
[ftp://ftp.berlios.de/pub/smplayer/source/](ftp://ftp.berlios.de/pub/smplayer/source/)

---

### Post by kamitsukai on 2009-06-19
> **rvm4000 said:**
> From Install.txt:



BTW, 0.6.7 will fail to build on Jaunty. I suggest to compile a package from svn:
[ftp://ftp.berlios.de/pub/smplayer/source/](ftp://ftp.berlios.de/pub/smplayer/source/)

yer read that in the end xD

---


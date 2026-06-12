---
title: "How to install Mesa 7.5"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by hennessy87 on 2009-07-20
How do I install Mesa 7.5?

---

### Post by LowSky on 2009-07-21
Mesa 7.5 will not be in Ubuntu until 9.04 which releases in October, you can get the files need though from [_here_]("http://packages.ubuntu.com/source/jaunty-updates/mesa")
I cannot say if they will work on 9.04 or lower and it might require other packages to be upgraded as well, which also I have no idea if they will work.... and realisticlaly with staying ubuntu point of interenst you should wait until 9.10 comes out to use Mesa 7.5

 try these instructions that might not work I make no garantees, make sure all old version have been removed from your computer before using these commands

download this file to your desktop
[http://archive.ubuntu.com/ubuntu/pool/main/m/mesa/mesa_7.5.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/m/mesa/mesa_7.5.orig.tar.gz)

open a terminal
type each line seperately
```
cd Desktop
tar xvfz mesa_7.5.orig.tar.gz
cd mesa_7.5.orig
./configure
make
make install
```

---


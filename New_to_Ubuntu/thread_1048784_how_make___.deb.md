---
title: "how make   *.deb"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by lord-zk on 2009-01-23
how make new package *.deb from source code 
to make install from apt

---

### Post by dnRoyston on 2009-01-23
Here you go, this guide should help you:
[http://www.linuxdevices.com/articles/AT8047723203.html](http://www.linuxdevices.com/articles/AT8047723203.html)

---

### Post by lord-zk on 2009-01-23
i want the command to make *.deb

---

### Post by x33a on 2009-01-23
checkinstall is the command to make a deb.

follow these instructions and you'll be able to make a deb.

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by albinootje on 2009-01-23
> **lord-zk said:**
> i want the command to make *.deb
From the mentioned [http://www.linuxdevices.com/articles/AT8047723203.html](http://www.linuxdevices.com/articles/AT8047723203.html)
> 
You'll use the dpkg command with the -b or --build option (-b and --build are the same). The syntax for creating a package is dpkg -b directory packagename.deb where directory contains the filesystem tree with all the requisite files for your program.


If this is too much to deal with, then install the "checkinstall" package, and use that.

And there's of course, as last resort, also the "alien" package to convert .tgz and .rpm packages to .deb. 
If you know where all the files from source are gonna be installed it's relatively easy to create a .tgz package and then convert that to .deb.

---


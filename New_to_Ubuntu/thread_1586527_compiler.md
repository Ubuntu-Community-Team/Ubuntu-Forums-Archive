---
title: "compiler"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by mbogo.kariuki on 2010-10-02
Am trying to install the program R on Ubntu 9.0.4 but I a reply "f77 complire not found" every time I try to run the command ./configure. I downloaded g95 compiler from the net but cannot get it running. I cannot get this program directly using packages as i cannot get my modem running on Ubuntu. Someone help!!

---

### Post by HermanAB on 2010-10-02
Eeeeugh...  It sounds like you need Fortran 77.  

The best way to experiment with such prehistoric schtuff is inside a virtual machine, so that you don't screw up your main system.  So start with installing VMware Player or Virtualbox, install Ubuntu or something similar inside that and then try to install the old development tools required for compiling your program.

Good luck!

---

### Post by 3rdalbum on 2010-10-02
You should really get an internet connection. If necessary you could use another computer to maintain the connection, and then use some method of internet connection sharing. Just to download a precompiled version of R from the R repository ([http://cran.r-project.org/bin/linux/ubuntu/README](http://cran.r-project.org/bin/linux/ubuntu/README)).

You can compile software without an internet connection, but you will need the 'build-essential' package from the repositories ([http://packages.ubuntu.com](http://packages.ubuntu.com)). This is just a 'metapackage' - you'll need to look at what the dependencies of build-essential are, and download those too and install them. This might take some time and effort to download them all and install them in the right order, whereas the package manager does this for you which is why I recommend obtaining an internet connection from somewhere.

Your third option is some software called Keryx ([http://keryxproject.org/](http://keryxproject.org/)). I have never used it before, but it consists of a package manager on Windows that can download the build-essential package and its dependencies, and a Linux program that can install the packages in the correct order for you. Many users here swear by it - maybe give it a try?

---


---
title: "cannot create directory    Permission denied"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by beningh on 2009-12-15
I am trying to install QLandkarteGT (gps) on Ubuntu 9.10,
I Install the following packages to satisfy the dependencies of QLandkarte GT.
=======================
[COLOR=Blue]sudo aptitude install cmake gdal-bin libgdal1-1.5.0 libgdal-dev 
libqt4-dev libusb-dev subversion build-essential[/COLOR]
==============================
then I
==============================
[COLOR=Blue]cd /opt
svn co [https://qlandkartegt.svn.sourceforge.net/svnroot/qlandkartegt/QLandkarteGT/trunk](https://qlandkartegt.svn.sourceforge.net/svnroot/qlandkartegt/QLandkarteGT/trunk) QLandkarteGT
mkdir build_QLandkarteGT
cd build_QLandkarteGT
ccmake ../QLandkarteGT
sudo make[/COLOR]
========================
I got this back
========================
[COLOR=Blue]barry@barry-laptop:~$ cd /opt
barry@barry-laptop:/opt$ svn co [https://qlandkartegt.svn.sourceforge.net/svnroot/qlandkartegt/QLandkarteGT/trunk](https://qlandkartegt.svn.sourceforge.net/svnroot/qlandkartegt/QLandkarteGT/trunk) QLandkarteGT
svn: 
barry@barry-laptop:/opt$ mkdir build_QLandkarteGT
mkdir: cannot create directory `build_QLandkarteGT': Permission denied
barry@barry-laptop:/opt$ cd build_QLandkarteGT
bash: cd: build_QLandkarteGT: No such file or directory
barry@barry-laptop:/opt$ ccmake ../QLandkarteGT


barry@barry-laptop:/opt$  make^C
barry@barry-laptop:/opt$ [/COLOR]
========================
What's wrong?

---

### Post by Arash18k on 2009-12-15
try
[COLOR=Blue]sudo [/COLOR][COLOR=Blue]mkdir build_QLandkarteGT[/COLOR]
beside
[COLOR=Blue]mkdir build_QLandkarteGT[/COLOR][COLOR=Blue]
[/COLOR]

---

### Post by 3rdalbum on 2009-12-15
Firstly, don't run "sudo make". Make merely compiles in the current working directory (within your home directory), it doesn't need root access.

Anything that modifies files outside your home directory needs to be run with 'sudo', so that includes your svn access and making directories.

---

### Post by nothingspecial on 2009-12-15
> **beningh said:**
> 

What's wrong?

You don`t need to be in /opt

---

### Post by northern lights on 2009-12-15
Run this from your /home folder - nothing will have to be run as root. If you choose to do it outside of /home, subversion and mkdir have to be run as root as well.
```
svn co https://qlandkartegt.svn.sourceforge.net/svnroot/qlandkartegt/QLandkarteGT/trunk QLandkarteGT

mkdir build_QLandkarteGT 

cd  build_QLandkarteGT 

ccmake ../QLandkarteGT 

make
```

---


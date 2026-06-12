---
title: "Vedics"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by COMPUTIAC on 2011-02-22
Hello, I am trying to use VEDICS.  I have downloaded it, it downloads with Archive Manager. It is a tar.gz  .

  How do I open this, install it, and use it.

                   Thank's,       COMPUTIAC



  [http://iweb.dl.sourceforge.net/project/vedics/Beta%20Release/VEDICS-beta-0.3.tar.gz](http://iweb.dl.sourceforge.net/project/vedics/Beta%20Release/VEDICS-beta-0.3.tar.gz)

---

### Post by TeoBigusGeekus on 2011-02-22
[There]("https://help.ubuntu.com/community/CompilingEasyHowTo") you go.

---

### Post by COMPUTIAC on 2011-02-22
Hello, I got as far as apt-file update, can not make any progress after this.



                Thank's,   COMPUTIAC

---

### Post by TeoBigusGeekus on 2011-02-22
Have you run
```
./configure
```
inside the extracted folder?

---

### Post by COMPUTIAC on 2011-02-22
Yes,  nothing happens.

---

### Post by TeoBigusGeekus on 2011-02-22
Ok. Try
```
make
```
and then
```
sudo checkinstall
```

---

### Post by COMPUTIAC on 2011-02-22
entered make,  last line says: no such file or directory compilation terminated.

entered  sudo checklist, says:   The package Documentation Directory ./doc-pak does not exist.
                                               Should I create a default set of package docs?  [y]:

---

### Post by TeoBigusGeekus on 2011-02-22
> **COMPUTIAC said:**
> entered make,  last line says: no such file or directory compilation terminated.


Which file is this? Perhaps it's a missing dependency.

---

### Post by COMPUTIAC on 2011-02-22
This is still for VEDICS, I do not remember the exact one. I think I am to the point where it looks for dependences. I can not go any further.

---

### Post by COMPUTIAC on 2011-02-22
Should I let it create a default set of docs ?

---

### Post by TeoBigusGeekus on 2011-02-22
Let it, it doesn't matter at the moment.
Can you post the last lines from the make output?

---

### Post by COMPUTIAC on 2011-02-22
This is the last two lines from make output;


fatal error: panel -applet.h: No such file or directory compilation terminated.
 make:  ***  [VEDICS] Error 1


This is what I got after letting it make new docs;



This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]:                          

Preparing package documentation...OK

*** No known documentation files were found. The new package 
*** won't include a documentation directory.

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@bob-HP-dc5000-uT-DZ216AV ]
1 -  Summary: [ VEDICS EOF ]
2 -  Name:    [ bob ]
3 -  Version: [ 20110222 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ bob ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ bob ]
12 - Conflicts: [  ]
13 - Replaces: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

---

### Post by oldos2er on 2011-02-22
According to the README, run ./install.sh 

There's also a list of dependencies in README.

---

### Post by COMPUTIAC on 2011-02-22
Hello, I finally have this installed. I used kludge_tarball_installer .  The only way I got to work at all was to download VEDICS to the desktop, then use kludge to open it.

This brought up the license agreements, and install.sh     

When I was using the previous system to install VEDICS it would keep coming up with; can not open configure, can not find config, broken package.

  The problem I have now is it will not start at all. When I click on the icon to start it the CPU hits 100 %. There is no way to stop this without doing a restart.

What is the fix for this ??

                           Thank's   COMPUTIAC






[https://help.ubuntu.com/community/CompilingEasyHowTo?action=AttachFile&do=view&target=kludge_tarball_installer_v0.9.2.tar](https://help.ubuntu.com/community/CompilingEasyHowTo?action=AttachFile&do=view&target=kludge_tarball_installer_v0.9.2.tar)

---

### Post by omonemo on 2011-03-09
When I run vedics it takes one command then asks what i was saying then errors out saying something went wrong and asks me to restart.  Does anyone know how to trasc/fix/work around this?

---


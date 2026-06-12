---
title: "probelm in qgis"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by bijay_panda on 2009-02-04
Hi All,
I am new to QGIS.I want to write plugins.
While compiling a program,including simple header like
#include "qgisplugin.h" showing error.
Can u plz tell me what packages to install.

Thanks in advance 
Bijay

---

### Post by petervk on 2009-02-04
How did you install qgis?

If you did it by the ppa on the qgis site [http://download.qgis.org/downloads.rhtml](http://download.qgis.org/downloads.rhtml)
> Add these lines to your /etc/apt/sources.list 
deb [http://ppa.launchpad.net/qgis/ubuntu](http://ppa.launchpad.net/qgis/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/qgis/ubuntu](http://ppa.launchpad.net/qgis/ubuntu) intrepid main


Then all you should have to do is install the libqgis1-dev package.
```
sudo apt-get install libqgis1-dev
```

---

### Post by bijay_panda on 2009-02-05
> **petervk said:**
> How did you install qgis?

If you did it by the ppa on the qgis site [http://download.qgis.org/downloads.rhtml](http://download.qgis.org/downloads.rhtml)


Then all you should have to do is install the libqgis1-dev package.
```
sudo apt-get install libqgis1-dev
```

Hi,
Thanx for ur reply.
I am using ubuntu 8.04.I installed it like bellow.
in /etc/apt/sources.list i added these lines

deb [http://ppa.launchpad.net/qgis/ubuntu](http://ppa.launchpad.net/qgis/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/qgis/ubuntu](http://ppa.launchpad.net/qgis/ubuntu) hardy main

then i uesd the command
sudo apt-get update
sudo apt-get install qgis

and also i did
sudo apt-get install libqgis1-dev

I can see the packages in my package manager like
qgis                        1.0.0
qgis-plugin-grass   1.0.0
qgit                       1.5.7
libqgis1-dev          1.0.0
libqgis-core0.11      0.11.0-1
libqgis-core1        1.0.0
libqgisgrass0.11   0.11.0-2
libqgis-gui0.11     0.11.0-2
libqgis-gui1          1.0.0
libqglviewer2       2.2.6-3-1

But still i m unable to add the headers in my program.
Can u plz plz help me out.

---


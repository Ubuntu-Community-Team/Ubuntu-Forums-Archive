---
title: "Install KDE without installing the software which comes with it?"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by cyb3r_sn4k3 on 2011-01-14
Hi everybody when I installed kde last time it installed alot of other software like k3b etc.

How can I avoid this I just want the desktop environment not the whole package with the softwares?

---

### Post by Paqman on 2011-01-14
If you're running Karmic or Lucid you can install the package kde-minimal. Unfortunately it's not available for Maverick or later, you have to install the whole thing.

---

### Post by vacco on 2011-01-14
See if you can find any packages called kde-core or kde-minimal. (Might be kde-desktop-core/kde-desktop-minimal as well, I can't remember.)

---

### Post by cyb3r_sn4k3 on 2011-01-15
Nope the kde-minimal/core dosen't work. yes I am running Maverick.

---

### Post by cascade9 on 2011-01-15
kde-core, kde-minimal dont exist in 10.10. kde-full and kubuntu-desktop are your only options (go for kde-full, its what you are after)

[http://packages.ubuntu.com/maverick/kde-full](http://packages.ubuntu.com/maverick/kde-full)

[http://packages.ubuntu.com/maverick/kubuntu-desktop](http://packages.ubuntu.com/maverick/kubuntu-desktop)

---

### Post by delix on 2011-05-07
In Natty the minimal package is 
[http://packages.ubuntu.com/natty/kde/kde-plasma-desktop]("http://packages.ubuntu.com/natty/kde/kde-plasma-desktop")

> This metapackage pulls in the core modules released with the KDE Software Compilation including the basic KDE Plasma Desktop, minimal set of basic applications (browser, file manager, text editor, system settings, panel, etc.), important libraries and data.

---

### Post by Advice Pro on 2012-02-17
The command below doesn't work in 10.04

[The Ubuntu Docs](https://help.ubuntu.com/community/InstallingKDE) read:

> kde-plasma-desktop --- This will install the core -- the bare-minimum required-- of KDE. That is, kdebase-apps, kdebase-runtime, kdebase-workspace and kdm. 

---


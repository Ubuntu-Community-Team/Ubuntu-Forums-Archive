---
title: "/etc/apt/sources.list (dist) error"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-12-09
how to correct what does line 51 refer to
 here is spm error  E: Malformed line 51 in source list /etc/apt/sources.list (dist)
E: Unable to lock the list directory

here is update manager error E:Malformed line 51 in source list /etc/apt/sources.list (dist)'

no idea how to fix
tks

---

### Post by karthick87 on 2010-12-09
Post the output of, 

```
sudo apt-get update
```

---

### Post by rburkartjo on 2010-12-09
just some more info


ray@ray-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ray@ray-desktop:~$ sudo apt-get update
E: Malformed line 51 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.

---

### Post by rburkartjo on 2010-12-09
kar i already tried but get this when i did


ray@ray-desktop:~$ sudo apt-get update
[sudo] password for ray: 
E: Malformed line 51 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
ray@ray-desktop:~$

---

### Post by sp-1070 on 2010-12-09
please copy line 51 of sources.list

---

### Post by karthick87 on 2010-12-09
Post your output with code tags,

```
cat /etc/apt/sources.list
```

---

### Post by wojox on 2010-12-09
```
gksudo gedit /etc/apt/sources.list
```

Press Ctrl+I and enter 51 into the box. Hit enter.

---

### Post by rburkartjo on 2010-12-09
wu and kat

here it is
gksudo gedit /etc/apt/sources.list
 # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 10.04 _Lucid Lynx_ - Alpha i386 (20100224.1)]/ lucid main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security universe

# deb [http://download.tuxfamily.org/gericom/libreoffice](http://download.tuxfamily.org/gericom/libreoffice) /
# deb [http://download.tuxfamily.org/gericom/libreoffice](http://download.tuxfamily.org/gericom/libreoffice) /
# deb [http://download.tuxfamily.org/gericom/libreoffice](http://download.tuxfamily.org/gericom/libreoffice) /
deb [http://download.tuxfamily.com/gericom/libreoffice/](http://download.tuxfamily.com/gericom/libreoffice/)

should i just put a # or delete correct or advise/tks

---

### Post by wojox on 2010-12-09
The last line:

```
deb http://download.tuxfamily.com/gericom/libreoffice/
```

Comment it out (#)

---

### Post by karthick87 on 2010-12-09
Put # sign infront of the last line,and run
```

sudo apt-get update
```

---

### Post by rburkartjo on 2010-12-09
tks ya'll worked like a charm

---

### Post by karthick87 on 2010-12-09
Mark this thread as [COLOR=Red][SOLVED][/COLOR]

---

### Post by freefallindz on 2011-06-10
Thanks for this post, I had a similar issue and commented out the sources.list file after trying to install Cairo Dock.  This solved my problems.

---


---
title: "when i try to edit options.conf its blank"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by ubunguy on 2010-07-16
Hello im trying to get the internal card reader to work in easy peasy on a aa1 532 i found out the code from another post but it says edit options.conf but when i log in and go to terminal and try and edit this file its empty ,i did save this code to the file but again there was nothing in options.conf what should i do? to make sure i am editing the right file with root privelges?

---

### Post by bodhi.zazen on 2010-07-16
What is the full path to options.conf ?

Can you post the link you are following please.

---

### Post by ubunguy on 2010-07-16
this is the thread i am following

[http://ubuntuforums.org/showthread.php?t=1199753](http://ubuntuforums.org/showthread.php?t=1199753)

the path to options.conf

etc/modeprobe.d

options is in modprobe.d folder

i went in and when i did edit the file it was blank now my options.conf just looks like this
options sdhci debug_quirks=1
ProblemType: Bug
Architecture: i386
DistroRelease: Ubuntu 9.04
Package: linux-image-2.6.28-6-generic 2.6.28-6.17
ProcCmdLine: User Name=UUID=e309fb14-05db-4e9a-b137-c6bf63eeb6a4 ro quiet splash elevator=noop
ProcEnviron:
SHELL=/bin/bash
LANG=it_IT.UTF-8
ProcVersionSignature: Ubuntu 2.6.28-6.17-generic
SourcePackage: linux

---

### Post by bodhi.zazen on 2010-07-16
The location of the file should be
[FONT=monospace]
[/FONT]/etc/modprobe.d/options.conf

This is a custom file, to, yes it will be empty when you first "open" it.

---


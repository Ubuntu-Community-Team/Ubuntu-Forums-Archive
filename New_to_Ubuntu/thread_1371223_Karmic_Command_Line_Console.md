---
title: "Karmic Command Line Console"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by PatK100 on 2010-01-03
Hello Peaps

Really simple question - am very new to Karmic - how do you open a command line console and how do I set up network shares - do I need to install Samba as when I try to share a folder it says unable to setup Sharing Service

Many thanks



Pat

---

### Post by Methuselah on 2010-01-03
You open a terminal by going to Accessories->Terminal in the menu.
If you need share that windows machines can access, SAMBA is needed, yes.

[https://help.ubuntu.com/9.10/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/9.10/serverguide/C/samba-fileserver.html)

---

### Post by audiomick on 2010-01-03
There is a really long thread about samba here:
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)
Look at the links in dmizer's signature

---

### Post by PatK100 on 2010-01-03
Help :-(

pat@CCBC-13112:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  samba-common-bin smbclient samba-common
E: Package samba has no installation candidate

---


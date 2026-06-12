---
title: "Can't install/remove anything?"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by ojdon on 2010-05-16
Hi, I was trying to get "globalmenu" to install yesterday had a few problems with it but it seemed to install in the end. Though today I've noticed something has gone horrible wrong and now I can't install or remove anything otherwise I get this error: 

```
ollie@ollie-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up cvs (1:1.12.13-12ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing cvs (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up gettext (0.17-8ubuntu3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing gettext (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of intltool:
 intltool depends on gettext (>= 0.10.36-1); however:
  Package gettext is not configured yet.
dpkg: error processing intltool (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Errors were encountered while processing:
 cvs
 gettext
 intltool
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Anyone know how to solve this problem?

---

### Post by ssj6akshat on 2010-05-16
yes I am also getting this type of error but with gnome-office.Very annoying.

---

### Post by ojdon on 2010-05-16
Anyone know of a possible solution? :confused:

---

### Post by mahurst on 2010-05-16
How did you install global menu?

---

### Post by ndstate on 2010-05-18
If any of you find a solution please post.

---

### Post by ndstate on 2010-05-18
I had similar problems and [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096) fixed it for me.

Good luck

---


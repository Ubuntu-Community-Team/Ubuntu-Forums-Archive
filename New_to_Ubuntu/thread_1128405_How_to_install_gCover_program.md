---
title: "How to install gCover program?"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by ferral-cat on 2009-04-17
Hi There,

I cant find gCover in the repos.  

I cannot find a .deb package for it anywhere on the web.  Only a .rpm package or the source.  

So I tried to install the source package but i cant even get past the first step without an error: 

```
daka@daRk-deSkTop:~$ cd /home/daka/Desktop/gcover-0.1.3
daka@daRk-deSkTop:~/Desktop/gcover-0.1.3$ ls
ABOUT-NLS       config.h.in   DEPENDS     Makefile.in    src
aclocal.m4      config.sub    INSTALL     missing        stamp-h.in
AUTHORS         configure     install-sh  mkinstalldirs
autom4te.cache  configure.in  intl        NEWS
ChangeLog       COPYING       ltmain.sh   po
config.guess    depcomp       macros      README
daka@daRk-deSkTop:~/Desktop/gcover-0.1.3$ sudo ./configure 
[sudo] password for daka: 
configure: error: cannot find install-sh or install.sh in . ./.. ./../..
daka@daRk-deSkTop:~/Desktop/gcover-0.1.3$ sh configure
configure: line 1100: config.log: Permission denied
daka@daRk-deSkTop:~/Desktop/gcover-0.1.3$ sudo sh configure
configure: error: cannot find install-sh or install.sh in . ./.. ./../..
daka@daRk-deSkTop:~/Desktop/gcover-0.1.3$ ls
ABOUT-NLS       config.h.in   depcomp     macros         README
aclocal.m4      config.log    DEPENDS     Makefile.in    src
AUTHORS         config.sub    INSTALL     missing        stamp-h.in
autom4te.cache  configure     install-sh  mkinstalldirs
ChangeLog       configure.in  intl        NEWS
config.guess    COPYING       ltmain.sh   po
daka@daRk-deSkTop:~/Desktop/gcover-0.1.3$ pwd
/home/daka/Desktop/gcover-0.1.3
daka@daRk-deSkTop:~/Desktop/gcover-0.1.3$ /home/daka/Desktop/gcover-0.1.3/ sudo sh configure
bash: /home/daka/Desktop/gcover-0.1.3/: is a directory
daka@daRk-deSkTop:~/Desktop/gcover-0.1.3$ sudo sh /home/daka/Desktop/gcover-0.1.3/configure
configure: error: cannot find install-sh or install.sh in /home/daka/Desktop/gcover-0.1.3 /home/daka/Desktop/gcover-0.1.3/.. /home/daka/Desktop/gcover-0.1.3/../..
daka@daRk-deSkTop:~/Desktop/gcover-0.1.3$ 

 
```

What am I doing wrong?

---

### Post by Mark Phelps on 2009-04-17
I don't know what it wrong, but if you install "alien" it will allow you to convert rpm packages to deb packages.  You can install that from synaptic.

---


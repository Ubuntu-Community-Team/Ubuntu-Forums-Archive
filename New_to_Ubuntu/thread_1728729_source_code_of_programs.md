---
title: "source code of programs"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by RobikShrestha on 2011-04-14
I want to view source files of the softwares from software center. I have checked "
source code" in the software center options, but i do not know where the code is. I tried
sudo apt-get source $name. But I do not know what to write in the $name. I tried writing
name.deb (name from var/cache/apt) but it does not work. What programming languages are 
used for those softwares?

---

### Post by nothingspecial on 2011-04-14
```
sudo apt-get source *package*
```

The source code will be downloaded to the directory you are in, then you can browse it

eg

```

ns@netbook:~$ sudo apt-get source feh
[sudo] password for ns: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
NOTICE: 'feh' packaging is maintained in the 'Git' version control system at:
git://git.debian.org/git/pkg-phototools/feh.git
Need to get 2511 kB of source archives.
Get:1 http://gb.archive.ubuntu.com/ubuntu/ natty/universe feh 1.10-1 (dsc) [1348 B]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ natty/universe feh 1.10-1 (tar) [2502 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ natty/universe feh 1.10-1 (diff) [7614 B]
Fetched 2511 kB in 20s (123 kB/s)                                              
gpgv: Signature made Mon Oct 18 22:35:08 2010 BST using DSA key ID C09FD35A
gpgv: Can't check signature: public key not found
dpkg-source: warning: failed to verify signature on ./feh_1.10-1.dsc
dpkg-source: info: extracting feh in feh-1.10
dpkg-source: info: unpacking feh_1.10.orig.tar.bz2
dpkg-source: info: unpacking feh_1.10-1.debian.tar.bz2
dpkg-source: info: applying 10_makefile_clean.patch
dpkg-source: info: applying debian-changes-1.10-1
ns@netbook:~$ ls
Audiobooks  Music     Templates         feh-1.10
Desktop     Pictures  Ubuntu One        feh_1.10-1.debian.tar.bz2
Documents   Podcasts  Videos            feh_1.10-1.dsc
Downloads   Public    examples.desktop  feh_1.10.orig.tar.bz2
ns@netbook:~$ cd feh-1.10/
ns@netbook:~/feh-1.10$ ls
AUTHORS  ChangeLog  README  cam        data    man      src
COPYING  Makefile   TODO    config.mk  debian  scripts  test
ns@netbook:~/feh-1.10$ cd src
ns@netbook:~/feh-1.10/src$ ls
Makefile   feh_png.c   getopt1.c    md5.c          signals.c    thumbnail.h
collage.c  feh_png.h   help.raw     md5.h          signals.h    timers.c
debug.h    fehrc.raw   imlib.c      menu.c         slideshow.c  timers.h
deps.mk    filelist.c  index.c      menu.h         structs.h    utils.c
events.c   filelist.h  keyevents.c  multiwindow.c  support.c    utils.h
events.h   getopt.c    list.c       options.c      support.h    winwidget.c
feh.h      getopt.h    main.c       options.h      thumbnail.c  winwidget.h
ns@netbook:~/feh-1.10/src$ less main.c
```

---

### Post by RobikShrestha on 2011-04-14
I get the following error:


suzuki@suzuki-laptop:~$ sudo apt-get source feh
[sudo] password for suzuki: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/apt.wxwidgets.org_dists_gutsy-wx_main_source_Sources - open (2: No such file or directory)


How do I know the package name??

---

### Post by RobikShrestha on 2011-04-14
I went to /etc/apt and editted sources.lst through terminal
sudo gedit sources.lst
then I commented out apt.wxwidgets and saved the file
I was then able to get the source code through
apt-get source netbeans

---

### Post by wolfgangmcq on 2011-04-14
sudo is not needed to apt-get source--just run apt-get source in a folder you have permissions on, like your home folder. (This does not apply to any other apt-get commands)

---


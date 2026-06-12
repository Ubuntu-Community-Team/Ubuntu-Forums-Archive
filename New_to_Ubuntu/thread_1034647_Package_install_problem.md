---
title: "Package install problem"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by bsmith52 on 2009-01-08
I tried to download a package from [www.linux.org](www.linux.org).  I was able to get it to my desktop.  It was a .gz file so I got into a terminal session, changed directory to Desktop, and did a tar command on the package. I then changed directory to the folder with the "unziped" (what is the Linux term?) folder.  I then did the "./configure" command (as per package install instructions). This is what I got:

billsmith@billsmith-desktop:~/Desktop$ ls
kpsk  kpsk-1.2rc2.tar.gz  sis_drv_i386.tar
billsmith@billsmith-desktop:~/Desktop$ cd kpsk
billsmith@billsmith-desktop:~/Desktop/kpsk$ ls
acinclude.m4  config.h.in      configure.in.in  kpsk         README
admin         configure        COPYING          Makefile.am  stamp-h.in
AUTHORS       configure.files  doc              Makefile.in  TODO
ChangeLog     configure.in     INSTALL          po
billsmith@billsmith-desktop:~/Desktop/kpsk$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... not found
configure: error: The important program kde-config was not found!
Please check whether you installed KDE correctly.

Is the package so old that it doesn't know where ubuntu keeps the kde-config (or the ubuntu equivalent) file?

Thanks

---

### Post by Tim Sharitt on 2009-01-08
The config file should look at the PKG_CONFIG directory, so that shouldn't be the problem, unless you have installed it in a non-standard location. You may need the kde-config development files, something like kde-config-dev.

---

### Post by bsmith52 on 2009-01-08
Thanks.  I'll proceed on the basis that I need to install those files before I can install this package.

---

### Post by Sorivenul on 2009-01-08
I believe that "kpsk" is in the repositories, so:
```
sudo apt-get install kpsk
```

After that, you should be up and running. Should be no need to mess with compiling it yourself.

---


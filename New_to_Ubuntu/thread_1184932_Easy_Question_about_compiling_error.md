---
title: "Easy Question about compiling error"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by julian.irwin on 2009-06-11
I just installed ubuntu and I am in the process of figuring out how to install tarballs.

I installed build-essential, git-core, cvs, mercurial...all the stuff the help page told me to do. 

Im trying to get keypassx to work. I installed qmake qt4 and ran it on the extracted tarball. It worked and made  a Makefile in they keypass directory.

The install file told me my my next step was the command: make; then make install.

Both of these show up errors, either 2 or 127. It says that the commmands it wants to use dont exist, but i installed all of the necessary packages. Is there another library i need? Maybe a library that goes with qmake?

jules@9000JR:/media/disk/KeypassX/src$ make
/usr/bin/uic-qt4 /home/jules/Desktop/keepassx-0.4.0/src/forms/AutoTypeDlg.ui -o ../build/ui/ui_AutoTypeDlg.h
make: /usr/bin/uic-qt4: Command not found
make: *** [../build/ui/ui_AutoTypeDlg.h] Error 127

or

jules@9000JR:/media/disk/KeypassX$ make
cd src/ && make -f Makefile 
make[1]: Entering directory `/media/disk/KeypassX/src'
/usr/bin/uic-qt4 /home/jules/Desktop/keepassx-0.4.0/src/forms/AutoTypeDlg.ui -o ../build/ui/ui_AutoTypeDlg.h
make[1]: /usr/bin/uic-qt4: Command not found
make[1]: *** [../build/ui/ui_AutoTypeDlg.h] Error 127
make[1]: Leaving directory `/media/disk/KeypassX/src'
make: *** [sub-src-make_default] Error 2

thanks!!

---

### Post by unutbu on 2009-06-11
Notice this error:

> make: /usr/bin/uic-qt4: Command not found

Apparently you are missing the uic-qt4 program. 
To find if an Ubuntu package provides this program go to 

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Go to the second search form, entitiled "Search the contents of packages".
Type in uic-qt4

and click search. You should be send to this page: 
[http://packages.ubuntu.com/search?searchon=contents&keywords=uic-qt4&mode=exactfilename&suite=jaunty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=uic-qt4&mode=exactfilename&suite=jaunty&arch=any)

Thus, it appears you need to install the libqt4-dev package.

---

### Post by hellofriendz on 2010-02-28
i think its better to use qt3

---

### Post by francis.pilon on 2010-10-30
```

sudo apt-get install libxtst-dev build-essential libqt4-dev qt4-qmake

```

---

### Post by rubo77 on 2013-04-11
use cmake instead:

this shows how to install keepassx from source:
[http://askubuntu.com/a/280155/34298](http://askubuntu.com/a/280155/34298)

---

### Post by lisati on 2013-04-11
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---


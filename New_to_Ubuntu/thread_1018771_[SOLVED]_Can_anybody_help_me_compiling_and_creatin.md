---
title: "[SOLVED] Can anybody help me compiling and creating a .deb please?"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by Kosimo on 2008-12-22
Hello, I want to compile this: pidgin-libnotify-0.14

I have all dependencies installed and ```
.configure
``` and ```
make 
``` had no errors.

But when trying to create a .deb by: ```
sudo checkinstall -D
``` this is what I get:

> *****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@cosimo-laptop ]
1 -  Summary: [ Notifications for Pidgin ]
2 -  Name:    [ pidgin-libnotify ]
3 -  Version: [ 0.14 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ pidgin-libnotify-0.14 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ pidgin-libnotify ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
Making install in po
make[1]: Entering directory `/home/cosimo/Desktop/pidgin-libnotify-0.14/po'
linguas="es fr it nl pl pt pt_BR sl hu zh_CN ro gl ru bg de sv "; \
	for lang in $linguas; do \
	  dir=/usr/local/share/locale/$lang/LC_MESSAGES; \
	  /bin/sh /home/cosimo/Desktop/pidgin-libnotify-0.14/install-sh -d $dir; \
	  if test -r $lang.gmo; then \
	    /usr/bin/install -c -m 644 $lang.gmo $dir/pidgin-libnotify.mo; \
	    echo "installing $lang.gmo as $dir/pidgin-libnotify.mo"; \
	  else \
	    /usr/bin/install -c -m 644 ./$lang.gmo $dir/pidgin-libnotify.mo; \
	    echo "installing ./$lang.gmo as" \
		 "$dir/pidgin-libnotify.mo"; \
	  fi; \
	  if test -r $lang.gmo.m; then \
	    /usr/bin/install -c -m 644 $lang.gmo.m $dir/pidgin-libnotify.mo.m; \
	    echo "installing $lang.gmo.m as $dir/pidgin-libnotify.mo.m"; \
	  else \
	    if test -r ./$lang.gmo.m ; then \
	      /usr/bin/install -c -m 644 ./$lang.gmo.m \
		$dir/pidgin-libnotify.mo.m; \
	      echo "installing ./$lang.gmo.m as" \
		   "$dir/pidgin-libnotify.mo.m"; \
	    else \
	      true; \
	    fi; \
	  fi; \
	done
installing es.gmo as /usr/local/share/locale/es/LC_MESSAGES/pidgin-libnotify.mo
installing fr.gmo as /usr/local/share/locale/fr/LC_MESSAGES/pidgin-libnotify.mo
installing it.gmo as /usr/local/share/locale/it/LC_MESSAGES/pidgin-libnotify.mo
installing nl.gmo as /usr/local/share/locale/nl/LC_MESSAGES/pidgin-libnotify.mo
installing pl.gmo as /usr/local/share/locale/pl/LC_MESSAGES/pidgin-libnotify.mo
installing pt.gmo as /usr/local/share/locale/pt/LC_MESSAGES/pidgin-libnotify.mo
installing pt_BR.gmo as /usr/local/share/locale/pt_BR/LC_MESSAGES/pidgin-libnotify.mo
installing sl.gmo as /usr/local/share/locale/sl/LC_MESSAGES/pidgin-libnotify.mo
installing hu.gmo as /usr/local/share/locale/hu/LC_MESSAGES/pidgin-libnotify.mo
installing zh_CN.gmo as /usr/local/share/locale/zh_CN/LC_MESSAGES/pidgin-libnotify.mo
installing ro.gmo as /usr/local/share/locale/ro/LC_MESSAGES/pidgin-libnotify.mo
installing gl.gmo as /usr/local/share/locale/gl/LC_MESSAGES/pidgin-libnotify.mo
installing ru.gmo as /usr/local/share/locale/ru/LC_MESSAGES/pidgin-libnotify.mo
installing bg.gmo as /usr/local/share/locale/bg/LC_MESSAGES/pidgin-libnotify.mo
installing de.gmo as /usr/local/share/locale/de/LC_MESSAGES/pidgin-libnotify.mo
installing sv.gmo as /usr/local/share/locale/sv/LC_MESSAGES/pidgin-libnotify.mo
make[1]: Leaving directory `/home/cosimo/Desktop/pidgin-libnotify-0.14/po'
Making install in src
make[1]: Entering directory `/home/cosimo/Desktop/pidgin-libnotify-0.14/src'
make[2]: Entering directory `/home/cosimo/Desktop/pidgin-libnotify-0.14/src'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/purple-2" || /bin/mkdir -p "/usr/lib/purple-2"
 /bin/bash ../libtool --silent   --mode=install /usr/bin/install -c  'pidgin-libnotify.la' '/usr/lib/purple-2/pidgin-libnotify.la'
chmod: changing permissions of `/usr/lib/purple-2/pidgin-libnotify.a': No such file or directory
make[2]: *** [install-gdLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/cosimo/Desktop/pidgin-libnotify-0.14/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/cosimo/Desktop/pidgin-libnotify-0.14/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.



Any idea about what happens there? 
Thank you!

---

### Post by mc4man on 2008-12-22
Try using this originally as checkinstall command

```
sudo checkinstall --fstrans=no
```

or to just make the.deb
```
sudo checkinstall --fstrans=no --install=no
```

---

### Post by Xiong Chiamiov on 2008-12-22
Try doing it [from scratch]("http://ubuntuforums.org/showthread.php?t=51003").

---

### Post by Kosimo on 2008-12-22
> **mc4man said:**
> Try using this originally as checkinstall command

```
sudo checkinstall --fstrans=no
```

or to just make the.deb
```
sudo checkinstall --fstrans=no --install=no
```

that worked perfectly.

Thank you so much! ;)

---

### Post by mc4man on 2008-12-22
In some cases where checkinstall will work (doesn't on all compiles), but fails even with the fstrans the work around is to go 

sudo make install, then 

sudo checkinstall --fstrans=no --install=no

followed by (if package is created

sudo make uninstall 

and then use the.deb

---

### Post by Kosimo on 2008-12-22
> **mc4man said:**
> In some cases where checkinstall will work (doesn't on all compiles), but fails even with the fstrans the work around is to go 

sudo make install, then 

sudo checkinstall --fstrans=no --install=no

followed by (if package is created

sudo make uninstall 

and then use the.deb

I still have to learn a lot about compiling, but I'm trying to do it insted of downloading debs (when something isn't in official repos) 

I didn't understand exactly why checkinstall sometimes fails. Why when compiling some program, it needs that many dependencies (that once compiled doesn't need).  Just a question: There's any way to know all the dependencies needed and install all of them before compiling a specific software? (for now what I do is ./configure, and wait 'till it warms me that something is missing and then install it one by one)... 

Anyway I'm happy with the result.

Thank you again!

---

### Post by mc4man on 2008-12-22
Generally sudo apt-get build-dep will acquire the majority of deps. if the app is available in a version near to the source your building in one of your repos.

Otherwise read thru any install, readme, ect. text files in the source and or google the app for wiki's, compile pages, ect.

Note on apt-get build-dep on 8.10 (Intrepid)
Actually just read here, midway down (I guess the op find a way or decided not worth the effort

[http://ubuntuforums.org/showthread.php?p=6408071#post6408071](http://ubuntuforums.org/showthread.php?p=6408071#post6408071)

This apt-get build-dep behavior is just on 8.10

---


---
title: "Geany source code"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by shankhs on 2009-01-22
I was trying to install geanydebug plugin but couldnt ./configure.
```

FATAL ERROR: Geany source code not found
make sure you install Geany source code
Use --with-geany-src=ARG option to
specify it's location

```
How can I find where is the source code of geany in my system.I installed geany using
```

sudo apt-get install geany

```
OR for that matter where is the source code of any of my installed apps (that i installed through apt-get) in ubuntu 8.10 system?

---

### Post by KIAaze on 2009-01-22
There doesn't seem to be any geany source code package.

Header files for libraries are usually in *-dev packages, but geany doesn't seem to have one.

[edit]
Oops, I was wrong. The Geany package actually contains it's own header files in "/usr/include/geany/".
cf: [http://packages.ubuntu.com/intrepid/i386/geany/filelist](http://packages.ubuntu.com/intrepid/i386/geany/filelist)
So try:
```
./configure --with-geany-src=/usr/include/geany/
```
[/edit]

> OR for that matter where is the source code of any of my installed apps (that i installed through apt-get) in ubuntu 8.10 system?

This is actually pretty easy on Debian based systems:
```
apt-get source PACKAGE
```
This will get you the source code used to build the packages from the repositories.

Feel the power of the source! :)

Note: You'll have to enable the source repositories eventually.

_To get a more recent version of the geany source code:_
1) Download source tarballs here: [http://www.geany.org/Download/Releases](http://www.geany.org/Download/Releases)
2) Check out the svn (latest possible version, potentially unstable):
```
 svn co https://geany.svn.sourceforge.net/svnroot/geany/trunk geany
```

---

### Post by shankhs on 2009-01-22
Thanks a lot for your swift reply.
```

./configure --with-geany-src=/usr/include/geany/

```
doesn't work it says:
```

checking for /usr/include/geany//src/geany.h... no
FATAL ERROR: Geany source code not found
make sure you install Geany source code
Use --with-geany-src=ARG option to
specify it's location

```
where does ```
 sudo apt-get source PACKAGE
``` stores the source files.

svn doesn't work for me as my system is behind a proxy with authentication and I dont know how to make svn work in such cases("export http_proxy=http://..." doesn't work).If you know how to make it work then please do tell me...

---

### Post by KIAaze on 2009-01-22
"apt-get source" downloads and extracts the source to the directory you ran the command from.
Actually, it doesn't require sudo. Sorry about that.

Anyway, I took a look at the plugin files and here's what might work:
Modify configure.in to look like this:
```
dnl Process this file with autoconf to produce a configure script.


AC_INIT([geanydebug], [0.0.1], [yetanothergeek@gmail.com])

PACKAGE="geanydebug"
VERSION=0.0.1

AM_INIT_AUTOMAKE([${PACKAGE}], ${VERSION} )


AC_PROG_CC
AC_PROG_LIBTOOL

PKG_CHECK_MODULES(GTK, [gtk+-2.0])
AC_SUBST(GTK_CFLAGS)
AC_SUBST(GTK_LIBS)

dnl check for geany source location

AC_ARG_WITH(geany-src, [  --with-geany-src=ARG	Geany source code location (default ../geany)],[
GEANY_SRC=${withval}
],[
GEANY_SRC=../geany
])
AC_CHECK_FILE(${GEANY_SRC}/geany.h,[],[
echo "FATAL ERROR: Geany source code not found"
echo "make sure you install Geany source code"
echo "Use --with-geany-src=ARG option to"
echo "specify it's location"
exit 1
])
AC_SUBST(GEANY_SRC)



AC_CONFIG_FILES([Makefile])
AC_OUTPUT



echo ""
echo "Configuration complete, now type 'make'"
echo ""
```

Only the "AC_CHECK_FILE(${GEANY_SRC}/geany.h,[],[" line is changed.

Then run:
```
autoconf
./configure --with-geany-src=/usr/include/geany/

```

autoconf regenerates the configure script, which should then hopefully work.

If this does work, please contact the plugin developers so they can improve their package or the INSTALL file (which you should read). ;)

---

### Post by shankhs on 2009-01-23
Thanks,I was able to successfully run 
```

autoconf
./configure --with-geany-src=/usr/include/geany/

```
by changing the configure.in file as suggested.

But when i typed "make" and pressed enter it showed something like:
```

shankhs@shankhs:~/Desktop/geanydebug-0.0.1$ make
 cd . && /bin/bash /home/shankhs/Desktop/geanydebug-0.0.1/missing --run automake-1.10 --gnu 
Makefile.am:5: Libtool library used but `LIBTOOL' is undefined
Makefile.am:5:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
Makefile.am:5:   to `configure.in' and run `aclocal' and `autoconf' again.
Makefile.am:5:   If `AC_PROG_LIBTOOL' is in `configure.in', make sure
Makefile.am:5:   its definition is in aclocal's search path.
make: *** [Makefile.in] Error 1

```
I have automake installed and when I am running automake its also giving the same error message.
I am stuck ....:( 
Can you please help 
btw sorry for late reply.

---

### Post by KIAaze on 2009-01-24
Unfortunately, I still didn't have time to try to install it on my PC yet (was at work previously and now on a windows PC :/ ).
As soon as I manage to install the plugin on my laptop, I'll tell you how in case you still have problems. ;)

I don't know about the LIBTOOL error, but I also think changing the configure.in wasn't the best thing to do because the rest of code might look for "src" directory too.

Try reusing the original configure.in (i.e. do a clean extract again), but do the following:
```
ln -s /usr/include/geany/ ./src
./configure --with-geany-src=$PWD

```
or
```

mkdir -p ../geany
ln -s /usr/include/geany/ ../geany/src
./configure

```

"ln -s" creates a symbolic link to the /usr/include/geany/ directory where the headers are.

---

### Post by KIAaze on 2009-01-24
Geany debug plugin successfully installed on Ubuntu 8.10 with Geany 0.14!

Just download ./geanydebug-0.0.1.tar.gz and run the following script in the directory you downloaded it too. :)

_install_geanydebug.sh_
```

#!/bin/bash
set -e -u -x
apt-get source geany
tar -xzvf ./geanydebug-0.0.1.tar.gz
cd ./geanydebug-0.0.1
./configure --with-geany-src=../geany-0.14
make
make install

```

_Notes:_
1)"set -e -u -x" is just for debugging the script. (-e: exit on error, -u: exit on unbound variable, -x: print executed commands)
2)You must enable the source repositories for "apt-get source" to work.
3)The plugin doesn't work with the Geany 0.15 source code. I already tried.
4)The Geany v0.14 source code doesn't seem to be available on sourceforge.

---

### Post by shankhs on 2009-01-24
Thanx a lot the plugin is working fine.

Just a few things before wrapping all this up:
instead of
```

cd ./geanydebug-0.0.1

```
this worked
```

cd geanydebug-0.0.1

```

Thanx a lot again for your valuable help.

---

### Post by KIAaze on 2009-01-24
Mmh, those two commands are pretty much the same. It would be strange if the first one didn't work. O.o
"." is just the current directory.

Glad to hear it worked. :)

---

### Post by shankhs on 2009-01-24
I am extremely sorry I was doing some silly mistakes.I apologize.
One more thing I am posting your code to the geany developer mailing list so that it can be of help to developers and users to install geanydebug in ubuntu.
```

#!/bin/bash
#Thanx to KIAaze
#http://ubuntuforums.org/member.php?u=240158
#http://ubuntuforums.org/showthread.php?t=1047433
set -e -u -x
apt-get source geany
tar -xzvf geanydebug-0.0.1.tar.gz
cd ./geanydebug-0.0.1
./configure --with-geany-src=../geany-0.14
make
make install

```
I hope you wont mind.If you have any problem please tell me I wont mail it.
I can forward the mail to you. :)

---

### Post by KIAaze on 2009-01-24
No problem at all. :)

---


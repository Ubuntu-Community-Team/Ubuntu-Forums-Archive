---
title: "QTScrobbler in Ubuntu?"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by Bazirker on 2010-10-29
Has anyone ever installed QTScrobbler in Ubuntu?  I can't figure out how to compile it and stuff, only the source is provided.

[http://qtscrob.sourceforge.net/](http://qtscrob.sourceforge.net/) (or, more specifically, [http://prdownloads.sourceforge.net/qtscrob/qtscrob-0.10.tar.bz2](http://prdownloads.sourceforge.net/qtscrob/qtscrob-0.10.tar.bz2))

Any help on how to get this installed would be much appreciated  :)

---

### Post by bioterror on 2010-10-29
:confused:> **Bazirker said:**
> Has anyone ever installed QTScrobbler in Ubuntu?  I can't figure out how to compile it and stuff, only the source is provided.

[http://qtscrob.sourceforge.net/](http://qtscrob.sourceforge.net/) (or, more specifically, [http://prdownloads.sourceforge.net/qtscrob/qtscrob-0.10.tar.bz2](http://prdownloads.sourceforge.net/qtscrob/qtscrob-0.10.tar.bz2))

Any help on how to get this installed would be much appreciated  :)

```

~/Documents/qtscrob-0.10$ ls
AUTHORS  CHANGELOG  COPYING  README  src  vs2008
user@computer:~/Documents/qtscrob-0.10$ cat README 
QTScrobbler ships both GUI and cli versions.

GUI version requires Qt>=4.3 and libcurl.
cli version requires libcurl.

Optional MTP support requires libmtp-dev and pkg-config

To compile GUI version: "cd src/qt && qmake && make"
To compile cli version: "cd src/cli && make"

```

So, next you will do:

apt-cache search qt|more
apt-get install qtpackage which you searched
apt-get install libcurl
apt-get install libmtp-dev pkg-config
apt-get install gcc

And I suggest you to check out this [http://checkinstall.izto.org/]("http://checkinstall.izto.org/")

---

### Post by mahavishnu on 2011-09-12
I'm struggling to get QTscrobbler work in order to scrobble from my Sony Walkman E345.

Don't know what I'm doing wrong.
I suspect there's one error in curl.



ubuntu@ubuntu-desktop:~$ cd qtscrob-0.10/
ubuntu@ubuntu-desktop:~/qtscrob-0.10$ cd src/qt && qmake && make
Project MESSAGE: You can provide your own prefix.
Project MESSAGE: Example: prefix="/usr" qmake-qt4
Project MESSAGE: QTScrobbler will be installed in /usr/local
potential duplicate alias detected: 'language.qm'
g++ -c -pipe -O2 -D_REENTRANT -Wall -W -DHAVE_LIBMTP -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Isrc/ui -I../lib -I/usr/X11R6/include -Ibuild/.moc -Ibuild/.ui -o build/.o/main.o src/main.cpp
In file included from src/qtscrob.h:31,
                 from src/main.cpp:20:
../lib/libscrobble.h:30:23: error: curl/curl.h: No such file or directory
make: *** [build/.o/main.o] Error 1
ubuntu@ubuntu-desktop:~/qtscrob-0.10/src/qt$

---

### Post by Bazirker on 2011-09-12
> **mahavishnu said:**
> I'm struggling to get QTscrobbler work in order to scrobble from my Sony Walkman E345.

Don't know what I'm doing wrong.
I suspect there's one error in curl.



ubuntu@ubuntu-desktop:~$ cd qtscrob-0.10/
ubuntu@ubuntu-desktop:~/qtscrob-0.10$ cd src/qt && qmake && make
Project MESSAGE: You can provide your own prefix.
Project MESSAGE: Example: prefix="/usr" qmake-qt4
Project MESSAGE: QTScrobbler will be installed in /usr/local
potential duplicate alias detected: 'language.qm'
g++ -c -pipe -O2 -D_REENTRANT -Wall -W -DHAVE_LIBMTP -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Isrc/ui -I../lib -I/usr/X11R6/include -Ibuild/.moc -Ibuild/.ui -o build/.o/main.o src/main.cpp
In file included from src/qtscrob.h:31,
                 from src/main.cpp:20:
../lib/libscrobble.h:30:23: error: curl/curl.h: No such file or directory
make: *** [build/.o/main.o] Error 1
ubuntu@ubuntu-desktop:~/qtscrob-0.10/src/qt$

This is a crappy suggestion as a fix, but...

I run the Windows version of QTScrobbler in Wine, and that works great for me.

---

### Post by mahavishnu on 2011-09-13
**libcurl4-openssl-dev** and **libXext-dev solved instalation**.
But now QTscrobble can't recognize my Walkman E345.:(

---


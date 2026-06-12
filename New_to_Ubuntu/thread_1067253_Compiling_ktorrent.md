---
title: "Compiling ktorrent"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by WitchCraft on 2009-02-11
I want to compile ktorrent:

i did 

apt-get source ktorrent
apt-get build-dep ktorrent

but that gives you some wired cmake files, and no additional information...

I basically want to get some addon to work.
It has an
#include <kurl.h>

in its header file

I search with apt-file and get:
```

all:~# apt-file search kurl.h
kdelibs4-dev: /usr/include/kde/kurl.h
kdelibs5-dev: /usr/include/kurl.h

```i do apt-get install kdelibs5-dev

the scons file of the addon says:
```

    CPPPATH=['/usr/include/qt3', '/usr/include/kde'],
    LIBS=['dl'],
    LINKFLAGS=['-s'],

...

if not conf.CheckLibWithHeader('qt-mt', 'qt.h', 'C++', autoadd=True):
    print 'Error: Qt 3.x library is missing.'
    Exit(1)

if not conf.CheckLibWithHeader('kdecore', 'kurl.h', 'C++', autoadd=True):
    print 'Error: KDE 3.x library is missing.'
    Exit(1)


```

i installed libqt3-mt-dev, and that got rid of the first error message, but now I'm stuck with the kdecore...


Can anybody help me, please ?

---

### Post by zvacet on 2009-02-14
This is probably trivial,but did you looked at [this]("http://ktorrent.org/?q=downloads") and [this]("http://ktorrent.org/?q=faq#q3") page?

---

### Post by WitchCraft on 2009-03-01
> **zvacet said:**
> This is probably trivial,but did you looked at [this]("http://ktorrent.org/?q=downloads") and [this]("http://ktorrent.org/?q=faq#q3") page?

lol, true I should read the FAQ...

However, the FAQ is a bit outdated, and "mkdir build" and "cd build" won't work...
[FONT=Verdana]Besides, [/FONT]it doesn't build with the sources from the repository.

You need to download the latest released ktorrent (3.2), which compiles fine.
(But only after installing this additional library)
```

apt-get install kdepimlibs5-dev 

```

Then compiling works fine:
```

cd ~/sources/ktorrent/ktorrent-3.2
cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`..
make
make install

```

---

### Post by WitchCraft on 2009-03-01
Works like a charm!


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=105011&stc=1&d=1235955196[/IMG]

---


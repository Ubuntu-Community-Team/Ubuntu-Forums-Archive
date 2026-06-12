---
title: "Compiling GEBC from Source Issues"
date: 2011-09-07
forum: New to Ubuntu
---

### Post by amonaaron on 2011-09-07
I'm not sure if this is exactly the place to post this issue, but it seemed the most appropriate given my luck with compiling from source code.

I've been trying to install GNU Exterior Ballistics Calculator from source tonight, but I keep running into issues when I use the "make" command. From what I can tell I have all of the appropriate libraries installed (no errors with ./configure). Below is  what happens in the terminal when I use that command. 

I'm thinking that there is something my package (Ubuntu 10.10) is lacking that is preventing me from properly installing this, but I'm not 100% certain on that. Any help that you can provide would be greatly appreciated.

```

aaron@Odin:~/gebc-1.07$ make
Making all in ./lib/ballistics/
make[1]: Entering directory `/home/aaron/gebc-1.07/lib/ballistics'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/aaron/gebc-1.07/lib/ballistics'
make[1]: Entering directory `/home/aaron/gebc-1.07'
g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"gebc\" -DVERSION=\"1.07\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_MATH_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STDIO_H=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -I.    -O3 -g -O2 -MT InputWindow.o -MD -MP -MF .deps/InputWindow.Tpo -c -o InputWindow.o InputWindow.cpp
In file included from InputWindow.h:28,
                 from InputWindow.cpp:2:
RangeWindow.h:16:18: error: hpdf.h: No such file or directory
In file included from InputWindow.h:31,
                 from InputWindow.cpp:2:
PlotWindow.h:9:24: error: FL/fl_draw.h: No such file or directory
make[1]: *** [InputWindow.o] Error 1
make[1]: Leaving directory `/home/aaron/gebc-1.07'
make: *** [all-recursive] Error 1
```

---

### Post by Toz on 2011-09-15
I think you might be missing some dependencies.

```
$ apt-file search fl_draw.H
libfltk1.1-dev: /usr/include/FL/fl_draw.H

```

```
$ apt-file search hpdf.h
libhpdf-dev: /usr/include/hpdf.h

```

You should check to see if those packages are installed.

However, I've been able to successfully run the slackware-packaged version ([http://sourceforge.net/projects/balcomp/files/GNU%20Ballistics%20-%20Slackware%2012/Version%201.07/gebc-1.07-i386-slack12.tar.gz/download]("http://sourceforge.net/projects/balcomp/files/GNU%20Ballistics%20-%20Slackware%2012/Version%201.07/gebc-1.07-i386-slack12.tar.gz/download")) on Ubuntu 11.04. All I needed to do was install the **libpng3** package (it appears to be a dependency).

Plus I was also able to run the windows version through wine.

Unless you have some pressing need/desire to compile from source, you can get away with running the application without the need to do so.

---


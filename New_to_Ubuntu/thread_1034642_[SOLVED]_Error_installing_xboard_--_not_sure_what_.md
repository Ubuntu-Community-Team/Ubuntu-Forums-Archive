---
title: "[SOLVED] Error installing xboard -- not sure what the problem is"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by d.asahi on 2009-01-08
I'm trying to install xboard. I managed to figure out the problems with xwindow headers and libraries and so forth, but this one I'm not sure what to do about.

I do [FONT="Courier New"]sudo ./configure[/FONT], that works fine. I type in "make" and this happens:

```
root@NNtop:/usr/local/xboard-4.2.7# make
gcc -DHAVE_CONFIG_H -I. -I.   -DINFODIR=\"/usr/local/share/info\" -c parser.c
gcc -DHAVE_CONFIG_H -I. -I.   -DINFODIR=\"/usr/local/share/info\" -c xboard.c
gcc -DHAVE_CONFIG_H -I. -I.   -DINFODIR=\"/usr/local/share/info\" -c backend.c
gcc -DHAVE_CONFIG_H -I. -I.   -DINFODIR=\"/usr/local/share/info\" -c moves.c
gcc -DHAVE_CONFIG_H -I. -I.   -DINFODIR=\"/usr/local/share/info\" -c childio.c
gcc -DHAVE_CONFIG_H -I. -I.   -DINFODIR=\"/usr/local/share/info\" -c gamelist.c
gcc -DHAVE_CONFIG_H -I. -I.   -DINFODIR=\"/usr/local/share/info\" -c lists.c
gcc -DHAVE_CONFIG_H -I. -I.   -DINFODIR=\"/usr/local/share/info\" -c pgntags.c
gcc -DHAVE_CONFIG_H -I. -I.   -DINFODIR=\"/usr/local/share/info\" -c xgamelist.c
gcc -DHAVE_CONFIG_H -I. -I.   -DINFODIR=\"/usr/local/share/info\" -c xedittags.c
gcc -DHAVE_CONFIG_H -I. -I.   -DINFODIR=\"/usr/local/share/info\" -c xhistory.c
gcc -DHAVE_CONFIG_H -I. -I.   -DINFODIR=\"/usr/local/share/info\" -c zippy.c
gcc -o xboard  parser.o xboard.o backend.o moves.o childio.o
gamelist.o lists.o pgntags.o xgamelist.o xedittags.o xhistory.o
zippy.o -lXaw  -lXmu  -lXt -lXext -lXpm  -lSM -lICE -lX11   -lm
/usr/bin/ld: cannot find -lXaw
collect2: ld returned 1 exit status
make: *** [xboard] Error 1
```

Many thanks to whoever can help me out with this.

So far all my questions have been answered on this forum. You guys rock.:D

---

### Post by jken146 on 2009-01-08
xboard is in the repositories.  Just type ```
sudo apt-get install xboard
```

---

### Post by d.asahi on 2009-01-08
Wow, that was easy. Thank you. :D

---


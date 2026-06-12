---
title: "Help with qmake application"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by User X on 2010-01-02
am trying to install mythvodka on a new installation of Mythbuntu 9.10 and I get to the part of this tutorial:

[http://www.mythtv.org/wiki/MythVodka](http://www.mythtv.org/wiki/MythVodka)

where I execute the line "qmake mythvodka.pro" and I get "qmake: command not found".  I visited synaptic to see if I could download qmake, but all I come up with is "qt4-qmake".  If I install this and execute "qmake mythvodka.pro", the next step  -  "make" returns:

cd mythvodka/ && make -f Makefile 
make[1]: Entering directory `/usr/lib/mythtv/plugins/mythvodka/mythvodka'
make[1]: *** No rule to make target `/usr/qt/3/mkspecs/linux-g++/qmake.conf', needed by `Makefile'.  Stop.
make[1]: Leaving directory `/usr/lib/mythtv/plugins/mythvodka/mythvodka'
make: *** [sub-mythvodka-make_default] Error 2

Can someone help me out?

---


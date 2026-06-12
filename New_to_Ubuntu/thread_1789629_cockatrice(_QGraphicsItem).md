---
title: "cockatrice( QGraphicsItem)"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by joshcanfield on 2011-06-24
hey I have installed cockatrice on my maverick, and after a little work got it up and running. I kept a log of everything i typed in so my bro, who also has the same os, could install but as we started to download it to his computer we ran in to a problem mine didnt here is what we did

1. go to cockatrice.de and click to download the source, then move it to your downloads folder

2. go to download folder and right click on cockatrice_source_2110309.tar.gz and click to extrct here.

3. open terminal and enter
          cd Downloads/cockatrice*
(downloads must be capitalized)
hit enter

4. then type
          sudo apt-get install libqt4-dev
hit enter

5. then type
          sudo apt-get install build-essential
hit enter

6. then type
          cd cockatrice
hit enter

7. then type
          lrelease translations/*.ts && qmake && make
hit enter

8. then type
          cd ../oracle
hit enter

9. then type
          qmake && make
hit enter

10. then open folder downloads, cockatrice, oracle, oracle, download card list

11.  lastly open folder downloads, cockatrice, cockatrice, cockatrice, when  set up comes open in the card database box click the three dotted lines  to browse and go through folders downloads, cockatrice, oracle,  cards.xml
hit ok

12. run cockatrice...go places, downloads, cockatrice, cockatrice, cockatrice and voila cockatrice is done on ubuntu.

but when we reach step 7 it stops and this is what we got...

jonathan@jonathan-DW236A-ABA-a545c:~/Downloads/cockatrice-20110309/cockatrice$  lrelease translations/*.ts && qmake && make
g++ -c  -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT  -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I.  -Isrc -I../common -I/usr/include/qt3 -Ibuild/ -o  build/abstractcounter.o src/abstractcounter.cpp
In file included from src/abstractcounter.cpp:1:0:
src/abstractcounter.h:4:25: fatal error: QGraphicsItem: No such file or directory
compilation terminated.
make: *** [build/abstractcounter.o] Error 1

I looked for something about qgraphicsitem and cant find anything and i dont know what this message means.


so does any body have any suggestions?

---

### Post by Abir Valg on 2011-06-25
Without more in-depth study, my first impression is this:

> DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -Isrc -I../common -I/usr/include/qt3 -Ibuild/ -o build/

I see qt3 in here, whereas QGraphicsItem is qt4 feature.
Maybe you could ask cockatrice developers why that is the case...

---

### Post by Abir Valg on 2011-06-25
Also, a quote from cockatrice.de
> To compile Cockatrice from source, you need at least Qt 4.5. We do not recommend using Qt 4.5.0; newer versions are fine. However, Qt 4.6 or higher is recommended since all 4.5.x versions exhibit weird behavior regarding graphics item updating.

Ubuntu's libqt4-dev is version 4.4
This should be the reason of failed compilation.

---


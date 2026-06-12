---
title: "Compilation error, libtool"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by trenkoff on 2009-06-06
Hi,

I am trying to compile an old software and make spits out an error. I believe the error has something to do with qt; tried to install all qt packages through the software manager to no avail.

This is the error given:
 ```

libtool --mode=link g++  -O0 -g3 -Wall -o qtvl  -L/usr/X11R6/lib  mydebug.o mywindow.o main.o mydebug.moc.o mywindow.moc.o  -lqt -lXext -lX11 
libtool: link: g++ -O0 -g3 -Wall -o qtvl mydebug.o mywindow.o main.o mydebug.moc.o mywindow.moc.o  -L/usr/X11R6/lib -lqt -lXext -lX11
/usr/bin/ld: cannot find -lqt
collect2: ld returned 1 exit status
make[1]: *** [qtvl] Error 1
make[1]: Leaving directory `/home/HP12a/Desktop/v2vhdl/qt_client'
make: *** [all] Error 2

```

Any help will be appreciated.

---

### Post by ibuclaw on 2009-06-06
You'll need to install the development packages of qt.

ie:
```
sudo apt-get install libqt4-dev
```
Regards
Iain

---

### Post by trenkoff on 2009-06-06
The libqt4-dev package is already installed. 
The program I am trying to compile was developed for qt3, could there be incompatibilities between the libqt versions?

---

### Post by ibuclaw on 2009-06-06
> **trenkoff said:**
> The libqt4-dev package is already installed. 
The program I am trying to compile was developed for qt3, could there be incompatibilities between the libqt versions?

Perhaps, there could be a distinction between the two now:

ie: -lqt3 and -lqt4

If you run:
```
ls /usr/lib/pkgconfig/qt*
```
You'll be able to see all pkg-config files for qt.

Choose one, and use it in the command 'pkg-config'.
ie: **glib-2.0.pc**
```
pkg-config --libs glib-2.0
```
To which you get back the answer: **-lglib-2.0**

(I don't actually have qt/kde on my system, and my internet connection is not good, else I would grab the qt-dev packages and look it up for you).

Regards
Iain

---


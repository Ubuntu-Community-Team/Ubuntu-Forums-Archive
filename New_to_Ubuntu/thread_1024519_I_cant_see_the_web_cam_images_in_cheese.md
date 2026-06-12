---
title: "I cant see the web cam images in cheese"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by halovivek on 2008-12-29
Hi 
i have installed cheese program in my ubuntu.
I am using 64-bit ubuntu. If i open the cheese program in the Gnome desktop.
I do have only one desktop installed GNOME only. I can see just the fingers of the legs is running and nothing more. 
If I go to preferences and check it shows my ACER Crystal clear and i cant select other and even i cant change the preferences.
Can you tell me how to overcome this problem?
:P

---

### Post by nhasian on 2008-12-29
launch cheese from a terminal with the command

```
cheese
```

if you receive an error like this:
```

(cheese:31132): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

(cheese:31132): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

(cheese:31132): GStreamer-WARNING **: pad video_source:src returned caps which are not a real subset of its template caps
libv4l2: error converting / decoding frame data: v4l-convert: error destination buffer too small
```

then you can fix cheese with the instructions from this page:

[http://bugzilla.gnome.org/show_bug.cgi?id=545033](http://bugzilla.gnome.org/show_bug.cgi?id=545033)

---

### Post by halovivek on 2008-12-29
> **nhasian said:**
> launch cheese from a terminal with the command

```
cheese
```

if you receive an error like this:
```

(cheese:31132): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

(cheese:31132): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

(cheese:31132): GStreamer-WARNING **: pad video_source:src returned caps which are not a real subset of its template caps
libv4l2: error converting / decoding frame data: v4l-convert: error destination buffer too small
```

then you can fix cheese with the instructions from this page:

[http://bugzilla.gnome.org/show_bug.cgi?id=545033](http://bugzilla.gnome.org/show_bug.cgi?id=545033)

i am getting this error in the terminal
gurudheva@gurudheva-laptop:~$ cheese

(cheese:6244): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

but i went to the place where you told. but i dont know how to do ? could you please guide me more?

---

### Post by halovivek on 2008-12-29
hi 
i have done as it says. please check the log whether i have done correct below.

gurudheva@gurudheva-laptop:~$ ls
c         Documents  photos-20081228-0.db  Templates
cxoffice  Examples   Pictures              Unsaved Document 1
Desktop   Music      Public                Videos
gurudheva@gurudheva-laptop:~$ cd Desktop
gurudheva@gurudheva-laptop:~/Desktop$ dir
CEH-Certified.Ethical.Hacker.Certification.Exam_312-50
GuruDheva.pls
Hackers\ 1,\ 2,\ 3
IE7-WindowsXP-x86-enu.exe
Jet\ Li\ -\ Once\ Upon\ A\ Time\ In\ China\ 1,\ 2,\ 3,\ 4,\ 5,\ 6\ DVDRIP
libflashplayer.so
libv4l-0.3.7
libv4l-0.3.8
paarkadal-1b.jpg
pidgin.desktop
Playlist.pls
qttube-0.2~pre1
untitled\ folder
untitled\ folder\ 2
utube_1.7-1_i386.gtk.deb
wine-config-sidenet
gurudheva@gurudheva-laptop:~/Desktop$ cd libv4l-0.3.8
gurudheva@gurudheva-laptop:~/Desktop/libv4l-0.3.8$ make
make -C libv4lconvert V4L2_LIB_VERSION=0.3.8 all
make[1]: Entering directory `/home/gurudheva/Desktop/libv4l-0.3.8/libv4lconvert'
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o libv4lconvert.o libv4lconvert.c
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o tinyjpeg.o tinyjpeg.c
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o sn9c10x.o sn9c10x.c
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o pac207.o pac207.c
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o jidctflt.o jidctflt.c
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o spca561-decompress.o spca561-decompress.c
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o rgbyuv.o rgbyuv.c
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o spca501.o spca501.c
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o bayer.o bayer.c
gcc -shared -Wl,-soname,libv4lconvert.so.0 -o libv4lconvert.so.0 libv4lconvert.o tinyjpeg.o sn9c10x.o pac207.o jidctflt.o spca561-decompress.o rgbyuv.o spca501.o bayer.o
ln -f -s libv4lconvert.so.0 libv4lconvert.so
echo prefix=/usr/local > libv4lconvert.pc
echo libdir=/usr/local/lib >> libv4lconvert.pc
echo >> libv4lconvert.pc
echo 'Name: libv4lconvert' >> libv4lconvert.pc
echo 'Description: v4l format conversion library' >> libv4lconvert.pc
echo 'Version: '0.3.8 >> libv4lconvert.pc
echo 'Libs: -L${libdir} -lv4lconvert' >> libv4lconvert.pc
echo 'Cflags: -I${prefix}/include' >> libv4lconvert.pc
make[1]: Leaving directory `/home/gurudheva/Desktop/libv4l-0.3.8/libv4lconvert'
make -C libv4l2 V4L2_LIB_VERSION=0.3.8 all
make[1]: Entering directory `/home/gurudheva/Desktop/libv4l-0.3.8/libv4l2'
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o libv4l2.o libv4l2.c
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o log.o log.c
gcc -shared -Wl,-soname,libv4l2.so.0 -o libv4l2.so.0 libv4l2.o log.o ../libv4lconvert/libv4lconvert.so
ln -f -s libv4l2.so.0 libv4l2.so
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o v4l2convert.o v4l2convert.c
gcc -shared -Wl,-soname,v4l2convert.so.0 -o v4l2convert.so.0 v4l2convert.o libv4l2.so
ln -f -s v4l2convert.so.0 v4l2convert.so
echo prefix=/usr/local > libv4l2.pc
echo libdir=/usr/local/lib >> libv4l2.pc
echo >> libv4l2.pc
echo 'Name: libv4l2' >> libv4l2.pc
echo 'Description: v4l2 device access library' >> libv4l2.pc
echo 'Version: '0.3.8 >> libv4l2.pc
echo 'Libs: -L${libdir} -lv4l2' >> libv4l2.pc
echo 'Cflags: -I${prefix}/include' >> libv4l2.pc
make[1]: Leaving directory `/home/gurudheva/Desktop/libv4l-0.3.8/libv4l2'
make -C libv4l1 V4L2_LIB_VERSION=0.3.8 all
make[1]: Entering directory `/home/gurudheva/Desktop/libv4l-0.3.8/libv4l1'
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o libv4l1.o libv4l1.c
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o log.o log.c
gcc -shared -Wl,-soname,libv4l1.so.0 -o libv4l1.so.0 libv4l1.o log.o ../libv4l2/libv4l2.so
ln -f -s libv4l1.so.0 libv4l1.so
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o v4l1compat.o v4l1compat.c
gcc -shared -Wl,-soname,v4l1compat.so.0 -o v4l1compat.so.0 v4l1compat.o libv4l1.so
ln -f -s v4l1compat.so.0 v4l1compat.so
echo prefix=/usr/local > libv4l1.pc
echo libdir=/usr/local/lib >> libv4l1.pc
echo >> libv4l1.pc
echo 'Name: libv4l1' >> libv4l1.pc
echo 'Description: v4l1 compatibility library' >> libv4l1.pc
echo 'Version: '0.3.8 >> libv4l1.pc
echo 'Libs: -L${libdir} -lv4l1' >> libv4l1.pc
echo 'Cflags: -I${prefix}/include' >> libv4l1.pc
make[1]: Leaving directory `/home/gurudheva/Desktop/libv4l-0.3.8/libv4l1'
gurudheva@gurudheva-laptop:~/Desktop/libv4l-0.3.8$ make install PREFIX=/usr/local
make -C libv4lconvert V4L2_LIB_VERSION=0.3.8 install
make[1]: Entering directory `/home/gurudheva/Desktop/libv4l-0.3.8/libv4lconvert'
mkdir -p /usr/local/include
install -p -m 644 ../include/libv4lconvert.h /usr/local/include
install: cannot create regular file `/usr/local/include/libv4lconvert.h': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/gurudheva/Desktop/libv4l-0.3.8/libv4lconvert'
make: *** [install] Error 2
gurudheva@gurudheva-laptop:~/Desktop/libv4l-0.3.8$ sudo su
[sudo] password for gurudheva: 
root@gurudheva-laptop:/home/gurudheva/Desktop/libv4l-0.3.8# make install PREFIX=/usr/local
make -C libv4lconvert V4L2_LIB_VERSION=0.3.8 install
make[1]: Entering directory `/home/gurudheva/Desktop/libv4l-0.3.8/libv4lconvert'
mkdir -p /usr/local/include
install -p -m 644 ../include/libv4lconvert.h /usr/local/include
mkdir -p /usr/local/lib
install -m 755 libv4lconvert.so.0 /usr/local/lib
cd /usr/local/lib && \
	  ln -f -s libv4lconvert.so.0 libv4lconvert.so
mkdir -p /usr/local/lib/pkgconfig
install -m 644 libv4lconvert.pc /usr/local/lib/pkgconfig
make[1]: Leaving directory `/home/gurudheva/Desktop/libv4l-0.3.8/libv4lconvert'
make -C libv4l2 V4L2_LIB_VERSION=0.3.8 install
make[1]: Entering directory `/home/gurudheva/Desktop/libv4l-0.3.8/libv4l2'
mkdir -p /usr/local/include
install -p -m 644 ../include/libv4l2.h /usr/local/include
mkdir -p /usr/local/lib/libv4l
install -m 755 libv4l2.so.0 /usr/local/lib
cd /usr/local/lib && \
	  ln -f -s libv4l2.so.0 libv4l2.so
install -m 755 v4l2convert.so.0 \
	  /usr/local/lib/libv4l/v4l2convert.so
mkdir -p /usr/local/lib/pkgconfig
install -m 644 libv4l2.pc /usr/local/lib/pkgconfig
make[1]: Leaving directory `/home/gurudheva/Desktop/libv4l-0.3.8/libv4l2'
make -C libv4l1 V4L2_LIB_VERSION=0.3.8 install
make[1]: Entering directory `/home/gurudheva/Desktop/libv4l-0.3.8/libv4l1'
mkdir -p /usr/local/include
install -p -m 644 ../include/libv4l1.h /usr/local/include
mkdir -p /usr/local/lib/libv4l
install -m 755 libv4l1.so.0 /usr/local/lib
cd /usr/local/lib && \
	  ln -f -s libv4l1.so.0 libv4l1.so
install -m 755 v4l1compat.so.0 \
	  /usr/local/lib/libv4l/v4l1compat.so
mkdir -p /usr/local/lib/pkgconfig
install -m 644 libv4l1.pc /usr/local/lib/pkgconfig
make[1]: Leaving directory `/home/gurudheva/Desktop/libv4l-0.3.8/libv4l1'
root@gurudheva-laptop:/home/gurudheva/Desktop/libv4l-0.3.8#

---

### Post by halovivek on 2008-12-29
[SIZE="3"]***_[COLOR="Red"]i tried this one also[/COLOR]_***[/SIZE]
gurudheva@gurudheva-laptop:~$ cd Desktop
gurudheva@gurudheva-laptop:~/Desktop$ ls
CEH-Certified.Ethical.Hacker.Certification.Exam_312-50
GuruDheva.pls
Hackers 1, 2, 3
IE7-WindowsXP-x86-enu.exe
Jet Li - Once Upon A Time In China 1, 2, 3, 4, 5, 6 DVDRIP
libflashplayer.so
libv4l-0.3.7
libv4l-0.3.8
paarkadal-1b.jpg
pidgin.desktop
Playlist.pls
qttube-0.2~pre1
untitled folder
untitled folder 2
utube_1.7-1_i386.gtk.deb
wine-config-sidenet
gurudheva@gurudheva-laptop:~/Desktop$ 
gurudheva@gurudheva-laptop:~/Desktop$ cd libv4l-0.3.7
gurudheva@gurudheva-laptop:~/Desktop/libv4l-0.3.7$ make
make -C libv4lconvert all
make[1]: Entering directory `/home/gurudheva/Desktop/libv4l-0.3.7/libv4lconvert'
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o libv4lconvert.o libv4lconvert.c
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o tinyjpeg.o tinyjpeg.c
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o sn9c10x.o sn9c10x.c
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o pac207.o pac207.c
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o jidctflt.o jidctflt.c
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o spca561-decompress.o spca561-decompress.c
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o rgbyuv.o rgbyuv.c
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o spca501.o spca501.c
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o bayer.o bayer.c
gcc -shared -Wl,-soname,libv4lconvert.so.0 -o libv4lconvert.so.0 libv4lconvert.o tinyjpeg.o sn9c10x.o pac207.o jidctflt.o spca561-decompress.o rgbyuv.o spca501.o bayer.o
ln -f -s libv4lconvert.so.0 libv4lconvert.so
make[1]: Leaving directory `/home/gurudheva/Desktop/libv4l-0.3.7/libv4lconvert'
make -C libv4l2 all
make[1]: Entering directory `/home/gurudheva/Desktop/libv4l-0.3.7/libv4l2'
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o libv4l2.o libv4l2.c
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o log.o log.c
gcc -shared -Wl,-soname,libv4l2.so.0 -o libv4l2.so.0 libv4l2.o log.o ../libv4lconvert/libv4lconvert.so
ln -f -s libv4l2.so.0 libv4l2.so
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o v4l2convert.o v4l2convert.c
gcc -shared -Wl,-soname,v4l2convert.so.0 -o v4l2convert.so.0 v4l2convert.o libv4l2.so
ln -f -s v4l2convert.so.0 v4l2convert.so
make[1]: Leaving directory `/home/gurudheva/Desktop/libv4l-0.3.7/libv4l2'
make -C libv4l1 all
make[1]: Entering directory `/home/gurudheva/Desktop/libv4l-0.3.7/libv4l1'
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o libv4l1.o libv4l1.c
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o log.o log.c
gcc -shared -Wl,-soname,libv4l1.so.0 -o libv4l1.so.0 libv4l1.o log.o ../libv4l2/libv4l2.so
ln -f -s libv4l1.so.0 libv4l1.so
gcc -c -MMD -fPIC -I../include -I../../../../linux/include -g -O1 -Wall -W -Wno-unused -Wpointer-arith -Wstrict-prototypes -o v4l1compat.o v4l1compat.c
gcc -shared -Wl,-soname,v4l1compat.so.0 -o v4l1compat.so.0 v4l1compat.o libv4l1.so
ln -f -s v4l1compat.so.0 v4l1compat.so
make[1]: Leaving directory `/home/gurudheva/Desktop/libv4l-0.3.7/libv4l1'
gurudheva@gurudheva-laptop:~/Desktop/libv4l-0.3.7$ sudo su
root@gurudheva-laptop:/home/gurudheva/Desktop/libv4l-0.3.7# make
make -C libv4lconvert all
make[1]: Entering directory `/home/gurudheva/Desktop/libv4l-0.3.7/libv4lconvert'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/gurudheva/Desktop/libv4l-0.3.7/libv4lconvert'
make -C libv4l2 all
make[1]: Entering directory `/home/gurudheva/Desktop/libv4l-0.3.7/libv4l2'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/gurudheva/Desktop/libv4l-0.3.7/libv4l2'
make -C libv4l1 all
make[1]: Entering directory `/home/gurudheva/Desktop/libv4l-0.3.7/libv4l1'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/gurudheva/Desktop/libv4l-0.3.7/libv4l1'
root@gurudheva-laptop:/home/gurudheva/Desktop/libv4l-0.3.7# make install PREFIX=/usr/local
make -C libv4lconvert install
make[1]: Entering directory `/home/gurudheva/Desktop/libv4l-0.3.7/libv4lconvert'
mkdir -p /usr/local/include
install -p -m 644 ../include/libv4lconvert.h /usr/local/include
mkdir -p /usr/local/lib
install -m 755 libv4lconvert.so.0 /usr/local/lib
cd /usr/local/lib && \
	  ln -f -s libv4lconvert.so.0 libv4lconvert.so
make[1]: Leaving directory `/home/gurudheva/Desktop/libv4l-0.3.7/libv4lconvert'
make -C libv4l2 install
make[1]: Entering directory `/home/gurudheva/Desktop/libv4l-0.3.7/libv4l2'
mkdir -p /usr/local/include
install -p -m 644 ../include/libv4l2.h /usr/local/include
mkdir -p /usr/local/lib/libv4l
install -m 755 libv4l2.so.0 /usr/local/lib
cd /usr/local/lib && \
	  ln -f -s libv4l2.so.0 libv4l2.so
install -m 755 v4l2convert.so.0 \
	  /usr/local/lib/libv4l/v4l2convert.so
make[1]: Leaving directory `/home/gurudheva/Desktop/libv4l-0.3.7/libv4l2'
make -C libv4l1 install
make[1]: Entering directory `/home/gurudheva/Desktop/libv4l-0.3.7/libv4l1'
mkdir -p /usr/local/include
install -p -m 644 ../include/libv4l1.h /usr/local/include
mkdir -p /usr/local/lib/libv4l
install -m 755 libv4l1.so.0 /usr/local/lib
cd /usr/local/lib && \
	  ln -f -s libv4l1.so.0 libv4l1.so
install -m 755 v4l1compat.so.0 \
	  /usr/local/lib/libv4l/v4l1compat.so
make[1]: Leaving directory `/home/gurudheva/Desktop/libv4l-0.3.7/libv4l1'
root@gurudheva-laptop:/home/gurudheva/Desktop/libv4l-0.3.7#

---

### Post by halovivek on 2008-12-29
the same error is coming . i dont know what to do. i have tried to start the cheese from terminal.

---

### Post by halovivek on 2009-01-02
hi
till now i have tried it is not working ? any other nice program is there than cheese? or else i have to bump?

---

### Post by Hobgoblin on 2009-01-02
Try xawtv  (you can install that from add/remove or from synaptics, or **sudo apt-get install xawtv**

There will be an icon to launch it from the menu or you can launch it from the command line.

---

### Post by halovivek on 2009-01-03
> **Hobgoblin said:**
> Try xawtv  (you can install that from add/remove or from synaptics, or **sudo apt-get install xawtv**

There will be an icon to launch it from the menu or you can launch it from the command line.

hi 
i have installed that one. when i open it one the screen becomes blank and i cant go further so i decided to uninstall and i have done that. 
thanks

---

### Post by Otto-C on 2009-01-03
using 8.04.1

did a sudo install. icon shows up in sound & video. clicking
returns nowthing. from the command line get:
:~$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-22-generic)
xinerama 0: 1280x800+0+0
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

any ideas

tia
otto-c

---

### Post by Otto-C on 2009-01-05
bump

---

### Post by halovivek on 2009-01-05
Bump

---


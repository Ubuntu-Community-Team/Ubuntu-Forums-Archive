---
title: "Kdenlive"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by allanek on 2009-01-21
Hi good people, please forgive me if this is a stupid question or has been answered elsewhere, but I have searched every where and found no solution.

I have installed Kdenlive on ubuntu 8.10, and all works properly except capture from 1394.

I know this is an issue about permissions, but i cant find a way to fix it. if i try to open kedit through sudo i get this message:

jalongshadow@jalongshadow-laptop:~$ sudo kdenlive
Error: "/tmp/kde-jalongshadow" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-jalongshadow" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-jalongshadow" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-jalongshadow" is owned by uid 1000 instead of uid 0.
kbuildsycoca running...
Error: "/var/tmp/kdecache-jalongshadow" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-jalongshadow" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-jalongshadow" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-jalongshadow" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-jalongshadow" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-jalongshadow" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-jalongshadow" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-jalongshadow" is owned by uid 1000 instead of uid 0.


if i try to capture i get the following:

Error: no camera exists

FFplay version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2003-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:3
, gcc: 4.3.2
pipe:: I/O error occured
Usually that means that input file is truncated and/or corrupted.

So can anybody offer me a step by step guide to get this fixed?

many thanks in anticipation,

allanek

---

### Post by blueridgedog on 2009-01-21
Is your device on the list of supported ones?

[http://kdenlive.org/video-editor](http://kdenlive.org/video-editor)

---

### Post by allanek on 2009-01-22
Hi thanks for response.

I am using a canon XM2 - which surprisingly appears to be unsupported :(

any suggestions?

---


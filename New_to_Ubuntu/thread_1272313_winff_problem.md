---
title: "winff problem"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by almoravid on 2009-09-22
Hi.. I'm trying to convert a video from .wmv to quicktime mov but it just not work.. I got this message come out

FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
[wmv3 @ 0x9ca0e90]Extra data: 8 bits left, value: 0

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 30.00 (30/1)
Input #0, asf, from '/media/jue's-1-/pms lama.wmv':
  Duration: 00:00:08.66, start: 1.579000, bitrate: 2286 kb/s
    Stream #0.0: Audio: wmav2, 44100 Hz, stereo, s16, 160 kb/s
    Stream #0.1: Video: wmv3, yuv420p, 640x480, 1900 kb/s, 30 tbr, 1k tbn, 1k tbc
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Unknown encoder 'libmp3lame'
Press Enter to Continue

Is there anybody have any solution?

---

### Post by almoravid on 2009-09-22
Ok.. I got the solution now.. just follow this [link]("http://ubuntuforums.org/showthread.php?t=1117283") for those who are having the same problem that I had

[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

---


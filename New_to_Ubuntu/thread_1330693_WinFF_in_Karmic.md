---
title: "WinFF in Karmic"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by smitty96 on 2009-11-18
I'm trying to convert videos in Karmic, but WinFF doesn't work anymore. When I try, it says ```
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.92 (359/12)
Input #0, flv, from '/home/tim/video1.flv':
  Duration: 00:03:08.47, start: 0.000000, bitrate: 8 kb/s
    Stream #0.0: Video: flv, yuv420p, 424x318, 29.92 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, stereo, s16, 8 kb/s
Unknown encoder 'libfaac'
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 20.00 (20/1)
Input #0, flv, from '/home/tim/video2.flv':
  Duration: 00:01:25.45, start: 0.000000, bitrate: 56 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x240, 20 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, stereo, s16, 56 kb/s
Unknown encoder 'libfaac'
Press Enter to Continue

``` Does anyone know what this means? I have libfaac0 installed..

---

### Post by philinux on 2009-11-18
[http://ubuntuforums.org/showthread.php?t=1163442](http://ubuntuforums.org/showthread.php?t=1163442)

---

### Post by FakeOutdoorsman on 2009-11-18
Right now there is no way to encode AAC audio with FFmpeg from the Karmic Koala repository.  The *libfaac* encoder has been removed due to licensing issues.  You will have to compile FFmpeg yourself to encode with *libfaac* when using FFmpeg and/or WinFF:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---


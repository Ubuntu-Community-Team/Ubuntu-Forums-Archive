---
title: "WinnFF doesnt convert?"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by Ryan8524 on 2009-08-19
The video converting program, winFF isn't working for me.
I'm trying to convert my videos to mp4.

Everytime i press convert, this terminal mesage shows up:
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
Input #0, avi, from '/home/ryan/Videos/Avi Movies/Role Models':
  Duration: 01:41:09.31, start: 0.000000, bitrate: 969 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 624x328 [PAR 1:1 DAR 78:41], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 112 kb/s
Unknown encoder 'libx264'
Press Enter to Continue




I press enter, but nothing happens afterwards.



What do I do?

---

### Post by credobyte on 2009-08-19
Have you installed x264 ?

---

### Post by paul.gevers on 2009-08-20
> **credobyte said:**
> Have you installed x264 ?

No need for x264. What you probably forgot to install is the UNSTRIPPED variant of ffmpeg. So you have libavcodec52 installed, while instead you need libavcodec-unstripped-52 from the multiverse repository. Just (most likely, except when you disabled the multiverse repository) install it with your favorite package manager.

---

### Post by credobyte on 2009-08-20
> **paul.gevers said:**
> No need for x264. What you probably forgot to install is the UNSTRIPPED variant of ffmpeg. So you have libavcodec52 installed, while instead you need libavcodec-unstripped-52 from the multiverse repository. Just (most likely, except when you disabled the multiverse repository) install it with your favorite package manager.

```
Unknown encoder 'libx264'
```
This is why I asked about x264.

---

### Post by paul.gevers on 2009-08-20
> **credobyte said:**
> ```
Unknown encoder 'libx264'
```
This is why I asked about x264.

I understand, but all the codecs that ffmpeg uses are either compiled into the libavcodec library, or not available for ffmpeg. So installing extra libraries does NEVER help ffmpeg converting videos. Libavcodec is created by the same source-package as ffmpeg and USES the source for libx264 to create the libavcodec-unstripped-xx binaries.

---


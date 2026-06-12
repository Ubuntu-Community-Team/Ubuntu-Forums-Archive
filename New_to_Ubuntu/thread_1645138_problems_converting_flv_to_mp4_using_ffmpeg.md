---
title: "problems converting flv to mp4 using ffmpeg"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by Jonas thomas on 2010-12-14
I want to download this lecture series from youtube and convert them to flv to mp4 so I can't watch them on my E71
I managed to download using youtube-dl  (I'm on 10.04 and the version in synaptic is broke(download from github)).
[http://www.youtube.com/watch?v=jTSvthW34GU&feature=list_related&playnext=1&list=PL9D558D49CA734A02]("http://www.youtube.com/watch?v=jTSvthW34GU&feature=list_related&playnext=1&list=PL9D558D49CA734A02")

When I run ffmpeg I get this message:

> jonas@jonas5:~/youtube$ ffmpeg -i Lecture01.flv ppLec01.mp4
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 60.00 (60/1) -> 29.97 (30000/1001)
Input #0, flv, from 'Lecture01.flv':
  Duration: 00:17:25.03, start: 0.000000, bitrate: 405 kb/s
    Stream #0.0: Video: h264, yuv420p, 480x360 [PAR 1:1 DAR 4:3], 405 kb/s, 29.97 tbr, 1k tbn, 60 tbc
    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
File 'ppLec01.mp4' already exists. Overwrite ? [y/N] y
Output #0, mp4, to 'ppLec01.mp4':
    Stream #0.0: Video: mpeg4, yuv420p, 480x360 [PAR 1:1 DAR 4:3], q=2-31, 200 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: 0x0000, 22050 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1
jonas@jonas5:~/youtube$ 


An empty mp4 is written out.

---

### Post by nothingspecial on 2010-12-14
You probably need to do this

[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by FakeOutdoorsman on 2010-12-14
This phone claims to be able to play H.264 video. The file from Youtube is in this format, so instead of re-encoding you can copy the video and audio into a new container:
```
ffmpeg -i input.flv -vcodec copy -acodec copy output.mp4
```
I'm not sure what limitations the phone has, so this command is not guaranteed to work.

---

### Post by Jonas thomas on 2010-12-14
Thanks everyone.
I found this stuff interesting also.
[http://ubuntuforums.org/showthread.php?t=1587514]("http://ubuntuforums.org/showthread.php?t=1587514")
[http://ubuntuforums.org/showthread.php?t=988366]("http://ubuntuforums.org/showthread.php?t=988366")

After spending hours on this I discovered my solution was a button click away.
Apparently on certain videos (like the one lectures I'm interested in) youtube has an option to download to a mp4. This is probably why the mp4 torrent link doesn't works on the Standford site.  (If I would have looked I would have seen it, but I made an assumption.)
But... I'm sure at some point I'll want to look at something on my phone that isn't purely educational and I'm sure this will come in handy..
Thanks,

---


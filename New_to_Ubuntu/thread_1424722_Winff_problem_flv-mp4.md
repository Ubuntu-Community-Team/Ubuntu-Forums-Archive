---
title: "Winff problem flv-mp4"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by MisFitt on 2010-03-08
This is the problem I had when attempting to covert the file:
brice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:20:33, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, flv, from '/media/New Volume ext HD/backup my documents/Dirty Three - Everything's ******.flv':
  Duration: 00:05:28.16, start: 0.000000, bitrate: 387 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x256, 331 kb/s, 25 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 56 kb/s
Unknown encoder 'libx264'
Press Enter to Continue
and I do press enter and it closes for the above reasons-is there a way?
Can anyone tell by what I cut and pasted from the terminal what the problem is I'm having?
Is something missing?Wrong?Broken?

Thanks
In advance

---

### Post by MisFitt on 2010-03-08
I found this,for anyone else who may be interested who,like me hadn't looked thru' here thoroughly enough:
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)
seems there's a LOT to this winff I hadn't yet realised
(so much to learn but so good for you)

---


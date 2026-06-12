---
title: "ffmpeg/winff question"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by gwilkins82 on 2010-08-30
Hello,

I am working on doing some video transcoding - from avi to mp4 with h264 encoding.  I set up ffmpeg and winff to do this, but when I click convert, I get an error:

Seems stream 0 codec frame rate differs from container frame rate: 2997.00 (2997/1) -> 23.98 (24000/1001)
Input #0, avi, from '/home/***/***/*****/*******/bogokhranetvse.avi':
  Duration: 00:01:20.45, start: 0.000000, bitrate: 947 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 23.98 tbr, 23.98 tbn, 2997 tbc
    Stream #0.1: Audio: wmav2, 44100 Hz, stereo, s16, 160 kb/s
/usr/bin/ffmpeg: unrecognized option '-me'

Any ideas?

Thanks!

---


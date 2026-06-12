---
title: "What's the best way to encode video in WebM format using Ubuntu?"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by brucewagner on 2010-05-19
What's the best way to encode video in WebM format using Ubuntu?

---

### Post by BoneyOne on 2010-05-20
If I read correctly on thei WebM project page then if you have FFmpeg revision #23165 installed then you can grab the patches available at the downloads page (link below) which will allow you to encode VP8 using FFmpeg. If you don't have FFmpeg then just get it from their SVN.

```
svn checkout -r 23165 svn://svn.ffmpeg.org/ffmpeg/ ffmpeg
```[http://code.google.com/p/webm/downloads/list](http://code.google.com/p/webm/downloads/list)

---

### Post by FakeOutdoorsman on 2010-05-20
Here's a good tutorial on the subject: [VP8, WebM, and FFmpeg](http://lardbucket.org/blog/archives/2010/05/19/vp8-webm-and-ffmpeg/). Unfortunately, the libvpx install target [doesn't work as expected](http://lists.mplayerhq.hu/pipermail/ffmpeg-devel/2010-May/088864.html), so you may have to manually install the headers and libs as shown in the tutorial.  Maybe a good package wrangler knows of a better method?

Those using 64-bit installs may want to use *--target=x86_64-linux-gcc* instead.

---


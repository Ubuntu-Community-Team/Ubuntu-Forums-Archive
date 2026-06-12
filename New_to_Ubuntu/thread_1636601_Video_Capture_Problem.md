---
title: "Video Capture Problem"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by splosh5 on 2010-12-03
Hey, I just installed ubuntu on my HP G62 laptop 64bit. And i used the following code:
```
ffmpeg -f alsa -ac 2 -i hw:0,0 -f x11grab -r 30 -s $(xwininfo -root |  grep 'geometry' | awk '{print $2;}') -i :0.0 -acodec pcm_s16le -vcodec  libx264 -vpre lossless_ultrafast -threads 0 -y output.mkv
```

So i typed this code into terminal, and it came up with this message: 
```
Unknown encoder: libx264 
```

Before i did this though i installed many different video and audio codecs to see if that would work. and it did not work. 

All i want to do it have a terminal based app that will record sound my my USB clear chat pro headset and record my screen at 30-50 FPS. at a resolution at 1366x768.

Many thanks
Splosh5

---

### Post by FakeOutdoorsman on 2010-12-03
Your FFmpeg probably doesn't have **libx264** enabled.  See:
[url=http://ubuntuforums.org/showthread.php?t=1117283]
HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg[/url]

---


---
title: "ffmpeg : how to put an offset between sound and video?"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by honeybear on 2010-10-02
[http://www.ffmpeg.org/ffmpeg-doc.html](http://www.ffmpeg.org/ffmpeg-doc.html)

audio and video arent matching of some few secs.

```
$ rm test.avi ;  ffmpeg -f alsa -i hw:3,0 -r 5 -s 320x240 -f video4linux2 -i /dev/video0  -timestamp now  test.avi
```

I tried itsoffet but no changes :(
-itsoffset -4 

any hints welcome

thanks

---

### Post by andrewthomas on 2010-10-02
I use avidemux when I have a problem with sound and video sync.  Try it out it is pretty easy

---

### Post by honeybear on 2010-10-02
> **andrewthomas said:**
> I use avidemux when I have a problem with sound and video sync.  Try it out it is pretty easy

with avidemux it cannot make bash scripts for command line for recording :( video + audio of mic usb + webcam

---

### Post by lidex on 2010-10-03
This thread is rather all-encompassing for ffmpeg:
[http://ubuntuforums.org/showthread.php?t=1392026](http://ubuntuforums.org/showthread.php?t=1392026)

---


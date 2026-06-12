---
title: "Choose 1 of 2 audio tracks for encoding with mencoder"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by paal on 2009-06-23
Just can't figure this one out... I've got an video file (.avi for the record) that I want to encode with mencoder. This file has two audio tracks and I'd like to use the second one. however, when encoding with
```
mencoder in.avi -o out.avi -vf scale=320:240 -oac  mp3lame -aid 2 -ovc xvid -xvidencopts bitrate=800
```
it gives me the first audio track and not the second. I've tried to play it with
```
mplayer in.avi -aid 2
```
and that works.

What am I doing wrong?

---

### Post by TeoBigusGeekus on 2009-06-24
Why don't you try with Avidemux?

---


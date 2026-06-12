---
title: "record music software"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by Old-un on 2011-05-05
I am running Ubuntu 11.04 without any problems and i'm really happy with it. But could someone tell this old noob what type of (free) software i would need in order to record the music from Youtube video's please.

---

### Post by TeoBigusGeekus on 2011-05-05
See my posts in [this]("http://ubuntuforums.org/showthread.php?t=1688948") thread.
Once you've captured the video, you can do whatever you want with it. To extract the audio and convert it to mp3, I use ffmpeg:
```
ffmpeg -i /path/video -acodec libmp3lame -ab 320k nameofsong.mp3
```
320kb is a bit too much for youtube videos, you can lower it if your want to (192k would be fine).

---


---
title: "Sound problem Compaq CQ60-108"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by fazillatheef on 2008-12-25
I bought a new compaq laptop .. the model number is CQ60-108

After installing ubuntu 8.04 , I installed all the mp3 codecs and vlc...

but when I try to play any sound (either in a video or a single audio file) the sound breaks and repeats for a long time... while logging into ubuntu the startup sound was repeating for long time... after I played a video the sound got screwed up and system got stuck

---

### Post by zzHanks on 2008-12-25
Try this ```
sudo apt-get install alsa-oss
```Hope this helps.

*Assuming that alsa-base is installed

---


---
title: "Extracting audio from a video"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by Ozymandias_117 on 2010-02-27
Hey, I'm trying to figure out how to extract the audio from a movie clip, It seems like it must be possible with PiTiVi, I can get the video gone, but I can't select an audio only container... Any idea of a better program or how to do it with PiTiVi?

---

### Post by ercferret18 on 2010-02-27
[http://www.mediaconverter.org/](http://www.mediaconverter.org/)

try that

---

### Post by d3v1150m471c on 2010-02-27
```

mencoder -of rawaudio -ovc copy -oac mp3lame -o namethemp3tomake.mp3 yourvideo.avi

```
That will make an mp3 of .avi format videos.

---

### Post by Ozymandias_117 on 2010-02-28
@d3v1150m471c Do you know of a reference that I can check out for various other formats? I'm trying to get audio from .mov, .wmv, and .flv

---

### Post by pastalavista on 2010-02-28
> **Ozymandias_117 said:**
> @d3v1150m471c Do you know of a reference that I can check out for various other formats? I'm trying to get audio from .mov, .wmv, and .flv
 Try WinFF in the Software Center. Very nice little GUI tool.

---

### Post by 3rdalbum on 2010-02-28
Open the video in Audacity and then export the resulting audio to whatever format you want.

---


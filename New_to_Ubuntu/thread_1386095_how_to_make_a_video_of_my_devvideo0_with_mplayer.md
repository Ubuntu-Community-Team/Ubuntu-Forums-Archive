---
title: "how to make a video of my /dev/video0 with mplayer ?"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-01-20
Hello , 

I do try this 

```
mplayer -noframedrop -dumpstream  -tv device=/dev/video0 tv://   -dumpfile aamyavi.avi

```

Not working 


Is there some solution to record an avi of the webcam?

---

### Post by frenchn00b on 2010-01-20
```
mencoder tv:// -tv driver=v4l2:device=/dev/video0:forceaudio:adevice=/dev/dsp -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o $1
```

solved

---


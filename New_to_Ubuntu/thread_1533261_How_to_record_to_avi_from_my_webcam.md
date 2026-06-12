---
title: "How to record to avi from my webcam?"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-07-17
Hello,

I do this: webcam is working
```
 mplayer -tv device=/dev/video0  tv://
```

I do this :
error 
```


 /usr/bin/mencoder tv:// -tv driver=v4l2:width=320:height=240:outfmt=yuy2:device=/dev/video0:alsa:adevice=hw.2,0:amode=1:audiorate=32000:forceaudio:forcechan=1:buffersize=64 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1200:keyint=30 -oac mp3lame -lameopts br=128:cbr:mode=3 -ffourcc divx -endpos 1819 -o  file.avi
```

any ideas how to record?

---


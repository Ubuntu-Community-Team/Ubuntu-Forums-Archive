---
title: "how to record from hw:6 (cardX) ?"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by honeybear on 2011-04-23
how to record from :

Mixer Device : hw:6 (cardX) 
Mixer Element: Aux

with aplay, mplayer, mencoder... whatever works please? 

I use now but not working... 

this is not recording the sound (video but no sound):
```
/usr/bin/mencoder tv:// -tv driver=v4l2:input=0:norm=pal:channel="$1":chanlist=switzerland:width=320:height=240:outfmt=yuy2:device=/dev/video1:alsa:adevice=hw.6,2:amode=1:audiorate=32000:forceaudio:forcechan=1:buffersize=64
```


this is not recording the sound (video but no sound):
> mencoder tv:// -tv driver=v4l2:device=/dev/video1:alsa=6:adevice=hw.6 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1200:keyint=30 -oac mp3lame -lameopts br=128:cbr:mode=3 -ffourcc divx -endpos 1819 -o /tmp/filerec.avi

---


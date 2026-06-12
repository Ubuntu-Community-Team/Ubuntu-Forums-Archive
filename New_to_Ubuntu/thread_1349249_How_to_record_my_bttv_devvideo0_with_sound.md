---
title: "How to record my bttv /dev/video0 with sound?"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by frenchn00b on 2009-12-08
For the video, I use this but I still do not know how to have the sound to the video

```
#!/bin/sh
# arg1 is minutes and arg2 is format output.avi for instance
streamer -t 0:$1:0 -c /dev/video0 -f rgb24 -r 3  -o  $2
```

```
 $ xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.30-1-686)
looking for available devices
port 65-65
    type : Xvideo, image scaler
    name : NV Video Overlay

port 66-97
    type : Xvideo, image scaler
    name : NV Video Blitter

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : BT878 video (Lifeview FlyVideo 
    flags: overlay capture tuner 

 
```

---

### Post by lovinglinux on 2009-12-08
Have you tried mencoder or transcode?

[http://ubuntuforums.org/showthread.php?t=921233](http://ubuntuforums.org/showthread.php?t=921233)
[http://ubuntuforums.org/showthread.php?t=369653](http://ubuntuforums.org/showthread.php?t=369653) (DVB)

Also take a look at [FoxMediaCenter]("http://fmc.isgreat.org"). I'm not sure it will work with your card tho. I'm currently developing a new version, which will support DVB cards ([Jose Catre-Vandis](http://ubuntuforums.org/member.php?u=78483) is beta testing it). So if you give me some feedback I might include support for your card too.

---


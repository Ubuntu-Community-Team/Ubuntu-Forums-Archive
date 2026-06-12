---
title: "Speed up video to 1.5x and save."
date: 2009-07-03
forum: New to Ubuntu
---

### Post by davidstri on 2009-07-03
Hi, 
is there a GUI or CLI application that can speed up a video to about 1.5x and save it? And if there is, can I have some instructions on how to do it. Thanks.
BTW, I kind of wanted a "chipmunk" effect.

---

### Post by credobyte on 2009-07-03
Haven't tried by myself, but .. you can give it a try :) Tutorial : [http://walter.deback.net/blog/archives/12](http://walter.deback.net/blog/archives/12)

---

### Post by davidstri on 2009-07-03
Thanks for the quick reply.
I tried the tutorial, the command ```
ffmpeg -i input.dv -f yuv4mpegpipe - | yuvfps -s 50:1 -r 50:1  | ffmpeg -f yuv4mpegpipe -i - -b 28800k -y output.avi
```

 works fine, but after it makes the video there is no audio for it and when I try to set the frame rate to 1.5x (37:1) instead of 50:1 it makes a video that is 5.5 kbs that doesn't work.
I am new to Ubuntu so I don't really know how to do this.

---


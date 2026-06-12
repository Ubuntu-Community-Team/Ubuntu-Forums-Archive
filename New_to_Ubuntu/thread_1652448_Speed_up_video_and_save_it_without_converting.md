---
title: "Speed up video and save it without converting"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by kay_rus on 2010-12-24
I have a MOV file and I would like to speed it up up to 16x or 32x. I would like to drop the frames except the keyframes (I suppose my camcoder do so when use x16 speed playback), then save that file without re-encoding. How can I do it?

I have tried the following command:

mencoder -lavdopts skipframe=nonkey -ovc copy video.mov -o new.mp4

But the output file was identical to initial one.

Can anyone help me?

---

### Post by kay_rus on 2010-12-25
bump

---

### Post by amjjawad on 2010-12-26
Not sure if this will help out or not but there are some programs here you may want to have a look at:
[http://ubuntulinuxhelp.com/top-100-of-the-best-useful-opensource-applications/](http://ubuntulinuxhelp.com/top-100-of-the-best-useful-opensource-applications/)

Check Video Applications.

---


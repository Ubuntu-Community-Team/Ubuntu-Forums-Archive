---
title: "Problems with webcam."
date: 2010-01-23
forum: New to Ubuntu
---

### Post by fatleader on 2010-01-23
To start off, ubuntu 9.10 is ******* amazing haha, I have been running it almost flawlessly for 3 weeks already. 

I do seem to have a problem with my integrated webcam though, I have not been able to use it with Camorama, or any other photo taking software. Oddly though, it worked perfectly when I ran it through skype....

I am a complete noob to linux, and have no idea whatsoever where to even start tackling this problem..

I have a Toshiba E105 laptop with a Chicony USB 2.0 webcam. 
Various websites state that it is supported....

Help please?

---

### Post by e-Gee on 2010-01-23
did you try with cheese

---

### Post by fatleader on 2010-01-23
oh wow.
that solved the problem haha. 

but what was the issue exactly?

---

### Post by gradinaruvasile on 2010-01-23
Probably the other programs.
To test a camera if supported OOTB by Ubuntu:
Press alt+f2, type gstreamer-properties, go to the video tab and see if the camera is listed as a device. If it is, press the test button. If it works, it is supported by Ubuntu.

---


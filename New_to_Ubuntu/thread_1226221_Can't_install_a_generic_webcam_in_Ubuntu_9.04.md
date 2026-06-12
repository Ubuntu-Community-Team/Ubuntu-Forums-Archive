---
title: "Can't install a generic webcam in Ubuntu 9.04"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by oxxen29 on 2009-07-29
[SIZE=3]I used to have Windows XP and Ubuntu...but for some mistakes I made, I ended up having Ubuntu in my whole hardrive. Anyway, now I want to install my generic webcam: I've tried to follow some forums' instructions but I don't mostly understand them or simply don't work...I guess, for what i read, that i need a driver (because i installed Cheese and it doesn't detect any camera)...but I don't know where to find it in order to install the camera.
It is a Speed Link Sphere Webcam SL-6820, 350k Pixel.
So, I wonder if I could get some help installing the webcam driver. Thank you.

oxxen29[/SIZE]

---

### Post by halitech on 2009-07-29
with the webcam not plugged in, open a terminal and run```
lsusb
```then plug the camera in, wait 30 seconds and run the command again then post the output here.

---

### Post by llamabr on 2009-07-29
In my experience, you're going about it backward.  By following our advice today, you'll spend the rest of the day fighting with your cam, installing drivers, breaking things, getting frustrated, and maybe ending up with a camera that works.

Or, you could look up a list of supported webcams, spend $20, and plug it in and it will work.  This list is a couple years old, but I'd start somewhere like here:

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

---


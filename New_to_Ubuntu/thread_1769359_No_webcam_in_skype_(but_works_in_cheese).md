---
title: "No webcam in skype (but works in cheese)"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by laffinet on 2011-05-27
Hi !

I'm running Ubuntu Natty 32-bit and skype 2.2.0.25
My webcam is a Logitech Quickcam IM (046d:08a6).

I used to be able to use this combination on previous versions of Ubuntu (skype might have been an earlier version, too), but since a fresh install of Natty the webcam doesn't work in skype anymore.
It shows as a device (dev/video0), but doesn't produce a picture when hitting "test".

It works fine in "cheese"

Anyone got a similar problem ? Any ideas ?

Thanks.

EDIT:

That was quick, found the solution. Need to execute
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
```
before executing skype and all is well

---


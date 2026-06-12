---
title: "just woundering something about my webcam"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by someitalian123 on 2010-08-03
I got my webcam working by installing v4l-dvb, but to get it to work in skype i have to use

LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

I was wondering why exactly do I have to do that, what does it do?

---

### Post by jtarin on 2010-08-03
If your camera doesn't work with skype you should preload v4l2convert. This means that the application is v4l2 compliant but some camera formats are not supported and must be converted first.
 No need to use v4l1_compat, unless you are using a very old version of skype, this is only intended to applications that are v4l1 compliant, and since this has been deprecated for a very long time, most apps (with very few exceptions) have now support for v4l2.

---

### Post by someitalian123 on 2010-08-04
Thanks for the information.

---


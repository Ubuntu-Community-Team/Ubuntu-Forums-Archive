---
title: "Multitouch not working"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by viditgoyal3009 on 2011-01-23
i bought an HP-DV6 laptop which nicely supports multi touch feature in windows. please help me how can i enable the same on ubuntu 10.10

---

### Post by ubudog on 2011-01-23
This may help you, especially the PPA link in it...

[https://wiki.ubuntu.com/Multitouch](https://wiki.ubuntu.com/Multitouch)

---

### Post by lumix on 2011-05-19
It doesn't help.  The Wiki mostly discusses what the Wiki is meant to do, but scarcely adds to that, which makes me grouchy.  Apologies in advance.

What I did get from it is to test using gesture test:

$gesturetest 0 0 0xffffffff


But the output is nothing whatsoever.  As is the Wiki's suggestion at that point:

> If you see output like this, congrats! You're successfully testing the gesture stack with your multi-touch enabled hardware Smile :-)

If not, now is the time to hit up multi-touch support!



Know what that is?  The main Wiki page.


So if I'm getting input response, per mtdev-tools, but no gesture input, per gesturetest, what does one do next?

Thanks.

---


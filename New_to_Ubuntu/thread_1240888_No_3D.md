---
title: "No 3D"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by Pike6 on 2009-08-15
Hi 

I have an ATI Radeon 4670 graphic card 
I have downloaded and installed the latest ATI drivers but I still don't get any 3D .
Games in 3D and Compizfusion 3D effects don't work.

Any possibilities to get 3D with this card or should I change for an Nvidia?

Thanks for your help

Kind regards

Pike6

---

### Post by wojox on 2009-08-15
Did you go into System > Preferences > Appearances 
Click Visual Effects and set it to Normal or Extra?

---

### Post by Pike6 on 2009-08-15
Yes set to To extra

---

### Post by wojox on 2009-08-15
Found this in the forums:

[http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

May help. :P

---

### Post by Pike6 on 2009-08-15
I will try but my card is very recent and I wonder if this could be the problem because also the 3D games don't work...

Thanks anyway :-)

---

### Post by 3rdalbum on 2009-08-15
If you're getting no 3D, then the drivers aren't working.

Please give us the output of this command:

```
cat /etc/X11/xorg.conf | grep "Driver"
```

There should be a line saying:

```
Driver       "fglrx"
```

somewhere in the output. If there's not, then the driver is not enabled and possibly not installed.

---


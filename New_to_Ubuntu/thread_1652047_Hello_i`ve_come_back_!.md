---
title: "Hello i`ve come back !"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by eagle128 on 2010-12-24
Firstly i`d like to wish everyone a Merry Christmas and a Happy New Year, i`ve been mucking about with various distros for a while but i`ve decided to come back and stick with Ubuntu.
i`ve loaded the LTS version 10.04 on my pc i got 2 x 500gb hard drive one has got windows 7 and i put ubuntu on the other

the only question i have at the moment is i talk to my family in the US so i use skype and  a microsoft vx 6000 webcam............. if i could get it all to work on ubuntu i wouldn`t need windows at all

anyone got any advice on what to do

oh the camera works ok on cheese

ttfn 
Tony:D

---

### Post by mastablasta on 2010-12-24
try to run skype through terminal using this command:
 
```

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
 
If it works you can create a launcher (shortcut) with this command later.
 
Also if this doesn't work does the picture also appear in gstreamer?
 
```
 
gstreamer-properties

```
 
under test....

---


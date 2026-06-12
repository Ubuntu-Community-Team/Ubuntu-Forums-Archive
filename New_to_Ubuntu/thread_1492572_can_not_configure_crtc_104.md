---
title: "can not configure crtc 104"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by purdurabo on 2010-05-24
hello, peoples
       its me again. i have posted a couple of time and you guys have been a big help, so maybe we can pull it off again.

here is the problem, a friend of mine just gave me a dell inspiron 2500 labtop. (i know, i know.) i installed 10.04 on it yesterday, and i cant change the resolution setting higher than 800x600. i know, not another one of these right? the funny thing is i wrote a how-to about doing this same thing. i had the same problem on my hp desk-top when i first installed 9.04 on it. i got that one, but this labtop is different for some reason.

on the hp i edited the xorg configuration file and it added 1024x768 to the options on the resolution changer. everything was cool.( for some reason when i updated to 10.04 i didn't need to change anything, even after a reinstall)

now on the dell labtop i can go through the motions and add the 1024x768 mode to the options list,but when i select it and click apply a notification bubble pops up and says,
          "could not configure crtc 104"
when i try to set the mode from the terminal using
```
xrandr --output default --mode 1024x768_60.00
```
 
then the screen flashes and i get:

```
xrandr: Configure crtc 0 failed
```

so if anyone can tell me why this labtop is acting different and what i can do to make it work, please fell free to lend a hand.

---

### Post by cariboo on 2010-05-25
It would help a lot if you told us what graphics chipset your system has.

---

### Post by purdurabo on 2010-05-25
built-in intel 815 chip family

---

### Post by purdurabo on 2010-05-29
well i figured it out and got it fixed. still not sure how. what i did was install 8.10 and use displayconfig-gtk to configure the correct resolution. i installed all the avaible drivers and update. then upgraded to 10.04, and the setting stuck. not sure how this work but it did.

good luck to any on else.

---


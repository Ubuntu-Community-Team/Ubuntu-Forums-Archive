---
title: "Sound in ubuntu 9.04 not working"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by jhk30 on 2009-09-22
I am new to ubuntu so I need really detailed explainations.

I used to be able to hear sound but VERY VERY QUIET! and now i cant hear it at all. I checked and its not muted (top right)

What is wrong? I need help Please!

---

### Post by wojox on 2009-09-22
You can double check by opening a terminal:

```
alsamixer
```

If still nothing try System > Preferences > Sound 

Try to reconfigure your different options in there and test them.

---

### Post by jhk30 on 2009-09-22
> **wojox said:**
> You can double check by opening a terminal:

```
alsamixer
```If still nothing try System > Preferences > Sound 

Try to reconfigure your different options in there and test them.

OKay I did 

```
alsamixer
```

but what am I supposed to check?

---

### Post by cobaltseeker on 2009-09-22
i had this problem on my machine (what are you running btw? just curious..) and i was able to fix it by looking through volume control... there was a SINGLE slider that was only _1_ tab away from max-volume, and this was a WORLD of difference. You need to left (or right?) click your volume button and have a good detailed run through of all your volume settings and make sure everything is on max.

i am running a Dell XPS m1530 and this fixed my problem (i have to have my main-volume slider on half to max to hear anything, but it works fine)

---


---
title: "motorola i425 wireless modem, boost network"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by nemoskull on 2008-03-30
this post is to tell you how i managed to get a wireless modem out of a motorola i425 cell phone on the boost/nextel/sprint network. first off i must say I DID NOT FIGURE THIS OUT ON MY OWN, I SEARCHED AND DID WHAT OTHERS DID AND MADE I WORK FOR ME. that being said, i currently run ubuntu 7.04 64bit on a compaq presario v2000 with a AMD turion 64bit processor. what i did was this:

```
    sudo pppconfig
 
Create 
```

(enter the name you want to call your connection.)
```



Dynamic

PAP

```

(i did not use a login name.)

(i did not use a password.)

(i left it at 115200, windows cannot connect higher than this on the phone anyways, regardless of the settings.)

```


Tone

S=#777

```
(my usb connection was" /dev/ttyACM0", and it only works if ubuntu reads it on startup)
```

Advanced Options

Modeninit 

ATE 1

```
now save it and start it up!

i am not saying that it will work on all system setups, but it did for me.:D

---


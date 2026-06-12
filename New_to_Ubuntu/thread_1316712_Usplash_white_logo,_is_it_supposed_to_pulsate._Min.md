---
title: "Usplash white logo, is it supposed to pulsate. Mine does not."
date: 2009-11-06
forum: New to Ubuntu
---

### Post by philinux on 2009-11-06
It pulsates while loading the livecd but not once installed.

Minor thing but even all through testing karmic it just stayed solid white and still does.

Could be an nVidia thing.

I'm interested if anybody has a pulsating logo.

---

### Post by dragonboss on 2009-11-06
I don't think its just an nVidia thing. I have the same problem on Intel GMA 950. Then again maybe its not supposed to pulsate!?

---

### Post by 3rdalbum on 2009-11-06
Mine stays white and doesn't pulsate. Even on the live CD. Nvidia or Intel.

---

### Post by philinux on 2009-11-06
Well this bug explains why the livecd does indeed pulsate now. Well my livecd does.

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/438762](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/438762)

---

### Post by Bunnybugs on 2009-11-06
Mine didn pulse at the liveCD, but it pulses on start-up, it glows up when the drive is extreme busy:evil:

But, I must say, I've got a crappy laptop:P

---

### Post by jaycee23 on 2009-11-06
I noticed this

LiveCD usplash pulsated but now it's installed no more pulsation.

Got to say any sign of life during boot is reassuring, even watching a line get longer made you feel something was going on.

Thankfully it boots quickly so not been an issue so far

---

### Post by isantop on 2010-01-17
I'm sure most computers are capable of displaying a pulsating usplash logo. If you use
```
sudo usplash --pulse-logo
```
The logo will pulse. It may be a missing parameter from usplash.conf (in /etc/). Anybody know how to add this parameter?

---


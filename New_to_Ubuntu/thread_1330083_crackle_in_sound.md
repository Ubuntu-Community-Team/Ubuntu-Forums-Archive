---
title: "crackle in sound"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by bob58523 on 2009-11-18
Hi All,

I just installed Ubuntu 9.10 x64 on an HP dv9260nr laptop. It has a 2ghz dual core processor with 2gb of ram. (I previously had Ubuntu 9.10 x86 on same machine, with same problem). 

Everything is working great, I installed getlibs for those x86 programs I needed to run. But I am having the same problem that I had with the x86 version of this software, that is, a crackle every time the sound works. I know, I know, its not a big deal, but it is very annoying.

I enabled the desktop sounds and every time there should be a sound for some desktop occurrence, it is always preceded by a distinct crackle, and sometimes there may not even be a sound, just the crackle.

Any ideas that may help me fix this problem would be greatly appreciated. Barring this small problem, I REALLY like this release :-)

thanks,
Bob

---

### Post by 3rdalbum on 2009-11-18
Run the alsamixer program:

```
alsamixer
```

Turn down the "PCM" channel to around 90%.

This often fixes crackle/distortion sound problems.

---

### Post by bob58523 on 2009-11-20
I turned down the pcm, but still have the crackle in the sound. I guess it is something that I can live with, but it grates on you after a while :-)

thanks for the help

---

### Post by Screatch on 2009-11-25
Crackle still annoys me badly, does anyone have a solution?
PCM turning down to 90 or more doesn't helps a lot.

---

### Post by ActualPirate on 2010-08-20
Bump

Also, didn't update my profile, running Karmic. Loving everything except for the crackle sound.

---

### Post by jbev on 2010-08-20
I had this exact same problem; I fixed it by accident really when I turned down/off some extra visual effects I was using. Try turning visual effects off in your appearance settings...may be a hardware problem as well

---

### Post by ActualPirate on 2010-08-22
It could easily be a hardware issue. Thanks for the advice, but I've decided to scrap the whole project completely. The laptop just wasn't worth saving. Thanks again.

---


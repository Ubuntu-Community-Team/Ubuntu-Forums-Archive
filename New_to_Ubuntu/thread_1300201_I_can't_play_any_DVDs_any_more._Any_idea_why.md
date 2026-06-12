---
title: "I can't play any DVDs any more. Any idea why?"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by tahitiwibble on 2009-10-24
The last time I played a DVD was a few months ago (I don't use my computer to watch them often). I just tried to put one in and read it with VLC and almost nothing happens. I have all the codecs installed, does anyone have an idea of what happened?

Thanks a lot for helping me out.

---

### Post by Incendia on 2009-10-24
> **tahitiwibble said:**
> The last time I played a DVD was a few months ago (I don't use my computer to watch them often). I just tried to put one in and read it with VLC and almost nothing happens. I have all the codecs installed, does anyone have an idea of what happened?

Thanks a lot for helping me out.

Does your drive still read other discs, such as: music, general data, games, etc. or is it just films?

---

### Post by NCLI on 2009-10-24
Try: 


```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
``````
sudo apt-get update
``````
sudo apt-get install medibuntu-keyring
``````
sudo apt-get update
``````
sudo apt-get install w32codecs libdvdcss2
```

---

### Post by Yvan300 on 2009-10-24
Most likely, you failed to installed the drivers for Dvd playback, the commands above should fix that.

---

### Post by tahitiwibble on 2009-10-24
**NCLI** & **Yvan300**, that was exactly the solution that was needed. I don't know how you guys do it but thanks a million. And thanks a lot **Incendia** for chipping in.

---


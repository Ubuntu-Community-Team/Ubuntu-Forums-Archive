---
title: "CD stuck in laptop"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by beew on 2011-06-30
Hello,

My friend has a bunch of old CDs (mostly jpegs, some video files and music) which he had not labeled.  He  asked me to mount them for him so he could find out what were in them. One of these didn't mount and I couldn't get it out of the CD rom. I restarted the laptop and couldn't even boot into Ubuntu (got the command line) It just happened that this was  a dual boot so finally I booted into Windows successfully and managed to get the CD out (it couldn't mount in Windows either, but the CD rom did open)

Now I would like to know what might have happened and how I would remove a stuck CD/DVD in Ubuntu.

Thanks.

---

### Post by babybean on 2011-06-30
A lot of the non-slide-in cd/dvd drives have a small hole in them which allows you to push a paper-clip in and manually open the tray. :p

---

### Post by beew on 2011-06-30
> **babybean said:**
> A lot of the non-slide-in cd/dvd drives have a small hole in them which allows you to push a paper-clip in and manually open the tray. :p
  It is a slide in.

---

### Post by TeoBigusGeekus on 2011-06-30
Did you try with the eject command?

---

### Post by RochJer on 2011-06-30
Laptop keyboard should have eject button - did you check to see if there's one available? Try that.

---

### Post by haqking on 2011-06-30
from terminal just type

eject

---

### Post by beew on 2011-06-30
> **TeoBigusGeekus said:**
> Did you try with the eject command?

If the CD is not mounted there is nothing to eject, no?

---

### Post by TeoBigusGeekus on 2011-06-30
Eject should work even if there's no cd/dvd in.
Try with
```
eject /dev/cd
```
Replace cd with whatever applicable: cdrw, dvd, sr0, etc.

---

### Post by haqking on 2011-06-30
> **beew said:**
> If the CD is not mounted there is nothing to eject, no?


well AFAIK eject calls umount anyways, and so makes it unmounted before the eject ?

---

### Post by beew on 2011-06-30
> **TeoBigusGeekus said:**
> Eject should work even if there's no cd/dvd in.
Try with
```
eject /dev/cd
```Replace cd with whatever applicable: cdrw, dvd, sr0, etc.

Thanks. I will remember that for next time. Mean time I don't feel like doing the experiment by asking the guy for the CD again. :) I will try this on an old computer once I make sure the DVD drive actually works. :)

Thanks also to others who have responded.

---

### Post by jtarin on 2011-06-30
Mark as solved.

---

### Post by dFlyer on 2011-06-30
With out some kind of error message, I don't believe someone can determine what caused this other than a bad cd.

---

### Post by quevedo200 on 2011-06-30
the drive could have just gotten jammed 
it happed on my old laptop

---

### Post by beew on 2011-06-30
> **dFlyer said:**
> With out some kind of error message, I don't believe someone can determine what caused this other than a bad cd.

What error message?? The thing got stuck, wouldn't mount and wouldn't come out.

---

### Post by beew on 2011-06-30
> **quevedo200 said:**
> the drive could have just gotten jammed 
it happed on my old laptop

Don't think so. It works with every other CD and in Windows I tried 3 times and just wouldn't mount. I did that in Windows only because I could get it out and I didn't know how in Ubuntu. I will test it in Ububtu again once I get my very old laptop set up. :)

---

### Post by jtarin on 2011-06-30
> **beew said:**
> What error message?? The thing got stuck, wouldn't mount and wouldn't come out.:lolflag: That sounds like an error message to me. Loud and clear!!!:p

---


---
title: "flash videos choppy"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by baltadt on 2010-01-16
I am running 64 bit Ubuntu 9.10. When I watch videos on hulu.com or other such sites the video plays fine but when I expand them to fullscreen the video lags and gets really choppy. The sound works fine. I installed the 64 bit flash player (beta version) from adobe. Is there a fix for my problems or do I just have to be patient until adobe releases a final version?

---

### Post by fancypiper on 2010-01-16
It sounds like a video driver problem.  What is your video card/chipset?

Command **sudo lshw | less** if you don't know.

---

### Post by sandyd on 2010-01-16
what version are you using?
this was a reported problem in the previous version of x64 flash, but i don't see it in the changelog.... or the bug tracker...

---

### Post by baltadt on 2010-01-16
> **fancypiper said:**
> It sounds like a video driver problem.  What is your video card/chipset?

Command **sudo lshw | less** if you don't know.

Nvidia GeForce 8200

---

### Post by baltadt on 2010-01-16
> **carlee said:**
> what version are you using?
this was a reported problem in the previous version of x64 flash, but i don't see it in the changelog.... or the bug tracker...

Get64bitFlash-0.2.2.tar.gz

adobe shockwave test site says 10.0.42.34

---

### Post by MarkC502 on 2010-01-16
If your using Geforce 8200 then which driver are you using for that ? If you are just using whatever driver Ubuntu chose when it was installed then that is probably your problem. If you don't have a recent Nvidia driver via Envyng or manual install then I would start there and install a recent Nvidia driver.


I have the same Flash version installed and mine works just fine. Adobe Flash Tests Reports -> 10,0,42,34 -- So check the Video Driver

---

### Post by baltadt on 2010-01-16
The drivers I installed were the ones Ubuntu installed when I selected extra on the visual effects.

---

### Post by MarkC502 on 2010-01-16
I would still say investigate that due to I am running 9.10 on Nvidia card with same flash version with no issues using Nvidia 190 drivers I got from Nvidia's site and installed by hand. But envy should at least install 185 drivers for you and I would try that. Or go to Nvidia's site and select driver downloads and geforce linux and get the .run file they provide and install it manually.

---

### Post by baltadt on 2010-01-16
I have never installed a video driver manually before. Is there a how to?

---

### Post by baltadt on 2010-01-16
Ok so I checked my hardware drivers and I am using the version 173. So I am now downloading and installing the version 185. I will report back later if this works.

---

### Post by baltadt on 2010-01-16
> **MarkC502 said:**
> I would still say investigate that due to I am running 9.10 on Nvidia card with same flash version with no issues using Nvidia 190 drivers I got from Nvidia's site and installed by hand. But envy should at least install 185 drivers for you and I would try that. Or go to Nvidia's site and select driver downloads and geforce linux and get the .run file they provide and install it manually.


Thank you. That was the problem. it works like a champ now. It was just me being stupid. The version 185 was in my hardware drivers. Guess I should have tried that first.

---

### Post by MarkC502 on 2010-01-16
No problem, I thought a newer driver would be better. 

Glad it worked.

---


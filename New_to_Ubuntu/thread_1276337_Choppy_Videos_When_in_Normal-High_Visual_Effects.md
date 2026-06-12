---
title: "Choppy Videos When in Normal-High Visual Effects"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by rentthedog on 2009-09-26
Hello,

I am very new to Ubuntu. Just installed it yesterday to teach myself through everything. I've gotta tell you, it's been a bit of a headache, but I got most things working now.

Still, my computer is being laggy when using normal or high visual effects. CPU keeps spiking to 100%. Not to mention, it has the common problem of playing choppy videos when visual effects are turned on. Without visual effects, however, videos play fine.

My specs are,
1GB RAM
Intel Pentium 4 CPU 2.00 GHz
ATI Radeon HD 2600 Pro AGP

I've installed the driver from ATI and used the xserver-no-backfill, which helped alot. 
At this point, is it my specs, or is there something else that I can do to make things smoother?

---

### Post by mharrison on 2009-09-30
How much memory does the ATI card have on it?  I searched but that model has several amounts of memory available to it.

Have you tried turning visual effects off and seeing if you still get laggy video?  I had an issue when I first started using Ubuntu with laggy video and it was because the GPU didn't have enough power to run the visual effects and play the video, so it started dumping things off on the processor causing spikes like you described.

Might not be the issue, but it doesn't hurt to check.

---

### Post by wobin77 on 2009-09-30
> **rentthedog said:**
> Hello,

Not to mention, it has the common problem of playing choppy videos when visual effects are turned on. Without visual effects, however, videos play fine.



^^ no problems with visual effects off. 
Are you using Compiz? 
We all know ATI and Ubuntu don't like each other!  ;-)

---

### Post by mharrison on 2009-09-30
> **wobin77 said:**
> ^^ no problems with visual effects off. 
Are you using Compiz? 
We all know ATI and Ubuntu don't like each other!  ;-)

Ooops....didn't see that line, thanks for pointing it out :)

---

### Post by wobin77 on 2009-09-30
No problem... :-)

---

### Post by rentthedog on 2009-09-30
thanks for the replies. no, i am not using compiz, and the memory on the video card is 512MB. more specifically, it is this model: [http://www.amazon.com/VisionTek-Radeon-2600-512MB-Graphics/dp/B000VELC52](http://www.amazon.com/VisionTek-Radeon-2600-512MB-Graphics/dp/B000VELC52)

---

### Post by wobin77 on 2009-09-30
Which effects are on then?

---

### Post by rentthedog on 2009-09-30
just the effects system>preferences>appearance>normal or high
both don't let me play videos

---

### Post by wobin77 on 2009-09-30
well, maybe this helps: 
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Read several comments on problems with this GPU, and this guide seems to help. I know i had some problems with installing my hd3850... It's just that ATI doesn't support binary drivers for linux...

---

### Post by Temposs on 2009-09-30
> **rentthedog said:**
> just the effects system>preferences>appearance>normal or high
both don't let me play videos

Those are the compiz effects :-)

---


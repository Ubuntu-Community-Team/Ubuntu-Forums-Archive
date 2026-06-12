---
title: "Which OS version?"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by username_already_taken on 2009-06-29
Hi! Im new to Linux and was wondering which version to download since it so confusing with so many choices. I have a Intel Core2Duo E4500 2.2Ghz CPU and 2Gb ram. Shall I download the 64bit or 32bit OS?

---

### Post by jimrz on 2009-06-29
> **username_already_taken said:**
> Hi! Im new to Linux and was wondering which version to download since it so confusing with so many choices. I have a Intel Core2Duo E4500 2.2Ghz CPU and 2Gb ram. Shall I download the 64bit or 32bit OS?

take your pick, that machine will run either.

---

### Post by ~sHyLoCk~ on 2009-06-29
Note that: Not all applications are compatible with 64bit OS!

---

### Post by philcamlin on 2009-06-29
id take the 32 bit 9.04 Ubuntu more apps work in 32 bit 

but it can use both :popcorn:

64 bit can recognise more ram

---

### Post by dtoronto on 2009-06-29
I would go with the 32 bit OS, althought the 64 bit can run an excess of 4gb of RAM, you won't have to worry about porting 32 bit software and you'll get a lot more compatibility with applications.  Then again 64 bit is more cutting edge and will probably end up being the default in a few years.

---

### Post by Simian Man on 2009-06-29
What problems are you guys having with 64 bits??  Flash and Java used to be problematic, but even those haven't given me troubles in like a year.

---

### Post by mprentice84 on 2009-06-30
Most of the problems with Java and Flash in 64 bit v 7-8 are non-existent in 9.04 now, so there is no reason not to use 64bit.

---

### Post by raymondh on 2009-06-30
Try the liveCD first (either version 32 or 64-bit).  See how your system works with the distro.

---

### Post by Elep.Repu on 2009-06-30
2gb? use 32 bit, until you have 4 gb.

+

> **philcamlin said:**
> id take the 32 bit 9.04 Ubuntu more apps work in 32 bit 



---

### Post by HotShotDJ on 2009-06-30
If you have a 64 bit processor, run the 64 bit version of Ubuntu -- see: [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)> Unless you have specific reasons to choose 32-bit, we recommend 64-bit. 

---

### Post by Elep.Repu on 2009-06-30
64bit install will take up more room and RAM. 

I suggest upgrading before considering 64bit.

---

### Post by ~sHyLoCk~ on 2009-06-30
That's all very good, but will there be any significant performance boost with 2GB ram?
> **Elep.Repu said:**
> 64bit install will take up more room and RAM. 

I suggest upgrading before considering 64bit.

I'd second this.

---

### Post by Paqman on 2009-06-30
> **~sHyLoCk~ said:**
> Note that: Not all applications are compatible with 64bit OS!

It's very, very rare to find anything that isn't. Certainly nothing in the rrpos will give you trouble. The only thing I can think of that i've found not available for 64-bit is Adobe Air (part of the ongoing 64-bit chain-dragging from Adobe)

---

### Post by Paqman on 2009-06-30
> **~sHyLoCk~ said:**
> That's all very good, but will there be any significant performance boost with 2GB ram?

For computationally intensive tasks like video re-encoding or distributed computing (Seti@home, Folding@home, etc), yes. For other stuff, no.

---

### Post by mikechant on 2009-06-30
> That's all very good, but will there be any significant performance boost with 2GB ram?

> For computationally intensive tasks like video re-encoding or distributed computing (Seti@home, Folding@home, etc), yes. For other stuff, no. 

I did some tests of 32vs64 bit Ubuntu on my Core2Duo with 2GB RAM (very similar to the original poster's machine).
None of my video and audio transcoding tests showed any significant improvement on 64-bit. I used lame for mp3 encoding and whatever DeVeDe uses under the covers (?mencoder) for video transcoding. I used the repository versions so the correct 32 or 64 bit versions should have been picked up.

Is it possible that although these programs compile and run as 64 bit code, they still handle data in 32-bit chunks? Has anyone got any solid examples of getting a decent performance increase for this sort of thing, and if so what applications did they use?

---

### Post by oldos2er on 2009-06-30
> **Elep.Repu said:**
> 2gb? use 32 bit, until you have 4 gb.

+

 Why? I ran 64-bit Ubuntu with 2GB for a long time, with no problems.

---


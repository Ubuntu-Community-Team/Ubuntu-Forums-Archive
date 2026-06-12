---
title: "Is it worth the money and effort?  (Powerbook G4 1.5 running Ubuntu)"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by grey.skylark on 2010-11-15
I recently jumped into using Linux by installing Ubuntu 10.10 on my Powerbook G4 (link to specs below).  I've encountered 2 problems and I'd like some advice on how to deal with them:

1.  If I have more than one program open at a time (especially if one of  them is RhythmBox), CPU usage shoots up to 100% and, as you might  expect, everything slows down to a crawl.   

I already tried powernowd and it exacerbated the slowness problem.  It's  possible that I didn't configure it correctly, although the  documentation I could find suggested that the default settings should  work well on a PBG4.


2.  There's a scraping noise coming from what I fear is the hard drive.   SMART status was verified when I was using OSX, and is still verified  in Ubuntu.  It's a quieter sound than the one I heard from my friend's  failing Powerbook HD.  

 Ubuntu runs faster than OS 10.4.  The case seems to heat up less and the fans don't come on as often as they did with OSX.  I like it better than Mac and Windows, and I don't plan on switching back if I can avoid it.




Any suggestions for diagnosing and fixing these issues?  Terminal commands are fine so long as you tell me where to start.
 

 I'd been thinking of upgrading the memory but I'm not sure if it will improve the situation if it's a CPU/HD issue.  I really like Ubuntu, but I'm open to trying a less resource-intensive sort of Linux if that's needed.  


Specs:
[http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_1.5_12.html](http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_1.5_12.html)


Thanks!

---

### Post by LowSky on 2010-11-15
512 RAM is really your bottleneck. 1GB or even better 2GB would stop the vicious SWAP writings to the hard disk and some of the slow downs.

If your hearing a scraping noise from the hard drive, its time to start thinking of a replacement. SMART can say everything is OK even when its not in some cases.

---

### Post by grey.skylark on 2010-11-15
Thanks for the advice!  

I don't think my PB (it's a 12") can hold more than 1.2GB of RAM, but it's good to know that a RAM upgrade might help with some of the issues.

Is it worth trying to diagnose the HD problem before giving up on it entirely?  A hard drive replacement is likely beyond my capacity.

Could you explain a bit about "vicious SWAP writings to the hard disk"?  Perhaps my google-fu isn't up to par, but I couldn't seem to find any info on what that means.  Thanks!

---

### Post by sandyd on 2010-11-15
> **grey.skylark said:**
> <snip>

Could you explain a bit about "vicious SWAP writings to the hard disk"?  Perhaps my google-fu isn't up to par, but I couldn't seem to find any info on what that means.  Thanks!

Ubuntu has a swap partition, just like windows has a swap file.
When you have lower amount of RAM, and the computer needs more, it uses the swap partition as RAM. However, that increases HD r/w which on some systems may become a constant problem.

---

### Post by grey.skylark on 2010-11-15
Thanks, that makes more sense now.  This might be wishful thinking, but might upgrading the RAM address the HD issue by lowering r/w?

---


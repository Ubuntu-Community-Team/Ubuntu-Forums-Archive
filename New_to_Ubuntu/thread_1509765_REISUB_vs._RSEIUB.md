---
title: "REISUB vs. RSEIUB"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by stoogiebuncho on 2010-06-14
Quick question.  Most of us know the pattern of keys to press to force a restart on an unresponsive computer.  However, I've seen two different orders recommended and I'm curious if there is any difference between the two orders from the computer's standpoint, and if so, which is better.

I learned the "Raising Skinny Elephants Is Utterly Boring" method.  Namely, hold down Alt and SysRq and then press the following patter of letters, leaving a second or two in between: RSEIUB

The pattern I often see on these forums is REISUB.

Which is the best?  Does it matter?

Thanks.

---

### Post by schauerlich on 2010-06-14
[http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html](http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html)

It shouldn't make much of a difference; as long as R is first and UB are last, it should be fine.

---

### Post by sisco311 on 2010-06-14
> **stoogiebuncho said:**
> 
Which is the best?  

REISUB ( "Raising Elephants Is So Utterly Boring", "Reboot Even If System Utterly Broken" )

I'm not an expert, but it sounds safer to sync the mounted filesystems (write any data buffered in memory out to disk) after all processes are terminated/killed. 


See:
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by bobpaul on 2013-03-05
> **stoogiebuncho said:**
> I learned the "Raising Skinny Elephants Is Utterly Boring" method.  Namely, hold down Alt and SysRq and then press the following patter of letters, leaving a second or two in between: RSEIUB

The pattern I often see on these forums is REISUB.

Which is the best?  Does it matter?

The **R** is the acryonym is to switch the input modes. It hasn't been needed in most of 10 years. We're already in that input mode.

**S** is for sync, that is flush the cache buffers to disk. It makes no sense to do this right before E.

**E** is to nicely kill all processes. (kill $pid). **I** is to forcibly kill all processes (kill -9 $pid)

E and I are going to cause a lot of activity on the disk as processes close and do final writes and everything. As you can see, sync before E and I is pointless.

**U** is for forcibly unmount. Unmount implies a sync operation. So now that S is really pointless. In fact, there's no difference between SU and U, so anyone that tells you "Do REISUB, not RSEIUB" is still wrong. U and SU are the same.

**B** means to immediately reboot the system.

So what do you need to type in? *AltGr + Sysreq + EIUB.* That's it. Nothing more. So naturally I type and teach RSEISUB. Why? "Raising Skinny Elephants Is So Utterly Boring" is something I find really easy to remember, and who cares if you're doing extra syncs or switching to an input mode you're already in?

---

### Post by matt_symes on 2013-03-05
Thanks for the input, however, old thread. 

Closed

---


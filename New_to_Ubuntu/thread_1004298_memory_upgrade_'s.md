---
title: "memory upgrade ?'s"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by twiz86 on 2008-12-07
Hey

I upgraded my memory from 2gigs of ddr2 to 4gigs of ddr2 on ubuntu 8.04 64bit.

Well my system monitor says i have 3gib and free in termal says i have 3.09....

I went into kernelcheck to do some playing and saw an option for 3gig/1gig sharing with the kernel and was wondering if that was ram or swap that its talking about. cuz if its swap then i want my damn gig back from wherever it is, if its default to have the kernel secretly take 1 gig of ram for itself then that is totally fine and ill be happy again.
):P
just wondering if that is right.

---

### Post by bumanie on 2008-12-07
32 bit OSes don't recognize any more than that. 64 bit does, but then you need 64 bit processor and the correct OS! If you using 64 bit, I have no idea.

---

### Post by nakama85 on 2008-12-07
> **bumanie said:**
> 32 bit OSes don't recognize any more than that. 64 bit does, but then you need 64 bit processor and the correct OS! If you using 64 bit, I have no idea.

if your using 64bit os (properly) check your bios and see if it all is recognized.

---

### Post by twiz86 on 2008-12-07
I am 100% 64bit. 64bit hardware, 64bit hardy. my full 4gig is recognized in my bios.

---

### Post by nakama85 on 2008-12-07
sorry I am not sure why then... I hope someone else can solve your problem.

---

### Post by bumanie on 2008-12-07
Guess you could run a mem86+ test off the live cd; this checks your ram for faults. New ram sometimes has quality issues.

---

### Post by twiz86 on 2008-12-07
I did run that earlier and the test kept restarting itself, i ran the memory discovery test and it reported errors from 3.3gb to 3.58gb then froze.

what does this mean and is there another memory test program or two that i could use to get somewhat of a second opinion on the state of my ram.

thank you

---

### Post by bumanie on 2008-12-07
That would indicate that some of your ram is bad. Seemingly this only happened since you got the new ram. Take the new ram out and see if mem86+ runs without error with the original ram. If so put in one stick of the new ram and run the test again. Then test the other - it may be that both are no good or that the original sticks have started playing up. You need to do a trial and error sort of test with different combinations (keep track of which is the original and which is the new ram), which is time consuming, unfortunately. I don't know of other ram testing programs, but there probably are some. Could even be a bad DIMM slot - really only way to find out is a methodical trial and error tracking of the problem down.
Hopefully someone else knows a shorter way.

---

### Post by twiz86 on 2008-12-07
Yay, yet another product from Newegg that has failed me.:popcorn:

---


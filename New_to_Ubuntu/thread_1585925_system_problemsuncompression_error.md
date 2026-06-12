---
title: "system problems/uncompression error"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by jrandolph on 2010-10-01
So on one of my boxes i have 9.10 installed along with windows 7
after a update from update manager the system wont boot all i get is "uncompression error -- System halted

I tried to boot to an older kernel version from the grub menu, system restore and also into my windows partition seems that nothing will work

I ran a mem test from grub and get nothing but errors 
can anyone tell me if there is an issue with the grub or is it failing memory  - possibly hard disk?

I am downloading a live cd in an attempt to see if I can run that 

Any help will be greatly appreciated

Jacob

EDIT
Ok so I tried to boot from the live cd and i get the same message
maybe this may shed some more light on it cuz i am totally lost

---

### Post by sikander3786 on 2010-10-01
You mean that you are getting errors with mem test if I understood you correctly.

If thats the case, I fear one of your memory module or even all of them have run out of order. Can you post the exact error messages encountered there?

I have seen Uncompression Error problems before and mostly they related to a bad RAM module. Although there might be some other problems as well but rule out the memory first.

---

### Post by jrandolph on 2010-10-01
> **sikander3786 said:**
> You mean that you are getting errors with mem test if I understood you correctly.

If thats the case, I fear one of your memory module or even all of them have run out of order. Can you post the exact error messages encountered there?

I have seen Uncompression Error problems before and mostly they related to a bad RAM module. Although there might be some other problems as well but rule out the memory first.

Well what I mean is that when the mem test is running there is 0% pass and within the test screen there is an error counter in which the number just gets bigger and bigger ha (sorry i cant help but laugh and poke fun at all my computer issues) - that is what i mean by nothing but errors

---

### Post by mikechant on 2010-10-01
The fact that you can't run from a live CD or the hard drive, and are getting memtest errors makes faulty RAM the prime suspect. How much RAM have you got, and how is it arranged?
If you had (say) 2x1Gb modules you could pull out each in turn and try booting; if one of them is dodgy, the system should run OK with it removed.

If you do try this and you haven't handled RAM before, make sure you ground yourself before touching the RAM modules, only hold them by the ends (try not to touch any chips or metal contacts) and ease them in and out carefully. 
The end clips are used to pop the modules half way out of their sockets so they can be removed easily; when pushing them back in try to do it as evenly as possible and make sure both end clips lock back into place. You may have to exert a little more force to get the modules fully 'locked' back in place.

---

### Post by jrandolph on 2010-10-01
> **mikechant said:**
> The fact that you can't run from a live CD or the hard drive, and are getting memtest errors makes faulty RAM the prime suspect. How much RAM have you got, and how is it arranged?
If you had (say) 2x1Gb modules you could pull out each in turn and try booting; if one of them is dodgy, the system should run OK with it removed.

If you do try this and you haven't handled RAM before, make sure you ground yourself before touching the RAM modules, only hold them by the ends (try not to touch any chips or metal contacts) and ease them in and out carefully. 
The end clips are used to pop the modules half way out of their sockets so they can be removed easily; when pushing them back in try to do it as evenly as possible and make sure both end clips lock back into place. You may have to exert a little more force to get the modules fully 'locked' back in place.

Ok well i was beginning to suspect faulty memory 
The box has 6gb 2x2 and 2x1 i am going to try and see what i can do to test them 
 
** NO HOMO ** People like you are what makes this site so amazing ( considering i forgot to explain my tech level ur easy explanation of what to do it what people need) Seriously thanks not only from me
Ill update when i can

Jacob

---

### Post by jrandolph on 2010-10-04
UPDATE

So after some troubleshooting it seems that I have some bad memory modules 
I removed the 2x2Gb sticks and the box booted perfectly fine - good thing Kingston has a lifetime warranty!

Thanks to all

---


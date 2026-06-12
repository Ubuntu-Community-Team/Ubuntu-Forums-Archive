---
title: "Does this mean my PSU is dead?"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Lateforgym on 2009-04-26
Unfortunately the instructions for my PSU tester didnt spell everything out. 

My PSU shows:

12V good
12v1 good
12v2 "LL" which means not detected or low lever-below tolerance.

The thing my manual isnt saying is what "v#" is. Does that mean rails? Also is it possible that my PSU doesnt have a 12v2(since its 8 years old?) so that is why its not detecting 12v2? On the side of the PSU it only lists -12 and +12. BTW this PSU is an ANTEC and everyting is in spec under the gadgets "load" except for that one "LL". Also this things doesnt have the extra 4 or 8 power thing that most computers today require. Is that "12v2"? 

The Display also shows "PG 230ms" which is not explained or discussed in the 20 word user manual other then to say Display Range  "PG   0MS  990MS".

A net search for "voltage PG 230 MS"
                 "PSU PG 230 MS"
                 "PSU 12v2"

Doesnt tell me anything useful. 


Thanks Coolmax. This $30 gadget is worth $0 is I cant figure out how to use it!

---

### Post by Didius Falco on 2009-04-26
This is really far afield from Ubuntu, but here goes:

the 12v is the (probably 4 pin) power connector
the 12v1 is a rail
the 12v2 is a second rail

On a PSU that old, the 12v2 rail would be designed for connecting things like CD drives or hard drives that have fluctuating power requirements. Basically, it was a way to build them a little cheaper but still have them work.

The "PG 230 ms" is how long it takes for the power to reach the usable level. PG = Power Good.

You'd have been better off to put that 30$ towards a new psu. At 8 years old, it's ready for retirement.

---


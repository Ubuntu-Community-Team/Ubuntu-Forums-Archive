---
title: "REAL battery report?"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by BT1 on 2009-12-16
Okay, this was an issue in Windows but at times the system would not sync right with the battery and it would report faulty "time estimates". Like it would say "2 hours and 30 mins left!" and 30 minutes later with just notepad running, I'd get "Critical battery level, 15 minutes left!"

I want to make sure my *buntu installs are reporting the estimate to the best ability, and in windows you had to resync the battery at times. Does this need to be done in Linux, and if so, how can one go about doing it?

PS Sorry about posting back to back. 30 minute lunch and rushing to get net stuff done ;(

---

### Post by Dark_Stang on 2009-12-16
Well, any battery monitor is going to have to "learn" how your battery works. So make sure it's fully charged, then just unplug it. Let it drain until the laptop dies on it's own, then boot it back up and let it fully charge while it's on. You may have to do this a few times.

---

### Post by tom.swartz07 on 2009-12-16
> **BT1 said:**
> Okay, this was an issue in Windows but at times the system would not sync right with the battery and it would report faulty "time estimates". Like it would say "2 hours and 30 mins left!" and 30 minutes later with just notepad running, I'd get "Critical battery level, 15 minutes left!"

I want to make sure my *buntu installs are reporting the estimate to the best ability, and in windows you had to resync the battery at times. Does this need to be done in Linux, and if so, how can one go about doing it?

PS Sorry about posting back to back. 30 minute lunch and rushing to get net stuff done ;(

sounds like you have a bad battery.
When youre running ubuntu, and on battery power, go to the battery icon at the top, right click, and select 'power history'.
scroll down and see what your capacity is listed as. Mine is currently at 59.1% and I am aware that a cell has shot in my battery.

Its expected that your battery cells will fail over their lifetime, and ubuntu assumes that when the battery reports '100%' charge, its at 100% power. HOWEVER, when your capacity is significantly lower, the real charge is around your capacity.

think of it this way.

[=====================================] full charge, 100% capacity
[----------------------------------------|================] full charge 25% capacity

you actually lose a portion of your battery.


If this is the case, Its probs not the OS that is wrong, its your battery that is starting to fail. 

Hope this helps!

---


---
title: "System Froze, Forced Quit"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by sheepdog9090 on 2010-04-24
I ran SMEM earlier today and when it was done began surfing using Firefox. Saw no issues until I tried to bookmark a webpage. Nothing happened. Tried again, nothing.

Kept browsing and then tried to open Evolution email. It wouldn't come up. Tried twice more and nothing.

Decided to reboot but when it hit restart the box came up with no words. It sat there, much like I did, doing nothing. After a bit I reached to hit the power button and when I did a dialogue box popped up and I restarted.

A disk check upon rebooting and now things are back. 

Any idea what happened? Should I do a clean install if it happens again?

Help appreciated.

---

### Post by P4man on 2010-04-24
is it possible your root partition is full?

---

### Post by rjcroy on 2010-04-24
Is it possible that the filesystem had an error and was remounted read-only?  This happened to me the other day and programs were pretty unusable once the / filesystem is read-only, of course. I am assuming that when you rebooted the filesystem check fixed the problem and then you were ok again. Whether this will cause more problems in the future would depend on what caused the error.

---

### Post by sheepdog9090 on 2010-04-24
> is it possible your root partition is full? 	

How would I check?

> I am assuming that when you rebooted the filesystem check fixed the problem and then you were ok again. Whether this will cause more problems in the future would depend on what caused the error.

There was a check going on when it restarted.

---


---
title: "Resume to Login Screen"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by staf0048 on 2009-01-18
Hi there,

This is a mere preference of mine, but does anyone know how to resume from suspend to the main login screen instead of the default generic black screen and gray box? Additionally, my computer seems to sleep and resume fine, but for some reason I get a notification that there is some problem. How do I investigate further to find out what's causing the error?

Thanks for the help!!

---

### Post by aesis05401 on 2009-01-18
> **staf0048 said:**
> ... Additionally, my computer seems to sleep and resume fine, but for some reason I get a notification that there is some problem.

I am not sure about the screen you see when you resume, but the first step to identifying the problem is to post the exact notification that you see.  If you are not notified of a problem every time you resume then you need to also note what you are attempting to do when the error is thrown.

---

### Post by staf0048 on 2009-01-18
Hmm - well wouldn't you know it - I can't seem to re-create the error now.  The only thing I've changed was to replace my old mouse.  I guess that might have been causing the issue . . .

Is there a log file that I can check to see what was going on?  The error message wasn't very detailed, it just said something along the lines of "Your computer failed to sleep.  Please see the help file for more information on this error."  I didn't really find much information there on the problem, so I came here. 

Again, my computer seemed to sleep just fine, screen went off, fans shut down, and I got a slow blinking amber light.  When I resume, everything comes up just fine in less than 5 seconds - except there is a high pitched squeal for a split second coming from my speakers if I left the volume up.

---

### Post by aesis05401 on 2009-01-18
> **staf0048 said:**
> Is there a log file that I can check to see what was going on?  The error message wasn't very detailed, it just said something along the lines of "Your computer failed to sleep.  Please see the help file for more information on this error."  I didn't really find much information there on the problem, so I came here.

/var/log has all sorts of logs.  Does anyone know which log might contain hibernate/suspend exceptions?

---


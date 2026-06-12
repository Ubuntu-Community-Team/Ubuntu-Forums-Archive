---
title: "Problem with MS bluetooth mouse 5000 on 9.04"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by samsi on 2009-08-17
My Microsoft bluetooth notebook mouse 5000 works fine in XP which I have now set up as a dual boot with Ubuntu 9.04

In Ubuntu the bluetooth wizard found the mouse and told me that it was successfully paired
However the mouse controls do not work at all!

I see from the forums that there were similar problems with an earlier version of Ubuntu but I cannot find a difinitive answer (understandable to me anyhow) to my problem 

I would be grateful for some (simple) pointers on resolving this
Thank you

---

### Post by LowSky on 2009-08-17
you need to repair the mouse. try reseting it or pulling the batteries.

this happens to me, windows and Ubuntu dont pair the mouse to the same coding, so it needs to be reset when switching between the two

---

### Post by samsi on 2009-08-18
Thank you for the speedy reply
Unfortunately I had already tried that

However your advice probably explains why when I boot back into XP I have to re-initialise the bluetooth mouse.

In any case, having to take out batteries etc. each time one changes OS seems a bit much   -  especially in my case as I am just experimenting with Ubuntu (Like it so far) so am changing back and forth several times a day

---

### Post by Schendje on 2009-08-18
We also have this mouse, and man does it have troubles.

However, the buttons worked at our end, until we rebooted or did nothing for a few minutes. In those cases it would disconnect and we had to remove and add it again.

We solved it by following the advice in [this bug comment]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727/comments/10") which also seems to work for other people.

Also, I ran into [this blog post]("http://blog.chinthaka.org/2008/09/getting-microsoft-bluetooth-mouse.html") which may help.

---

### Post by Albertkinng on 2009-08-18
YESSSSSS! It's working!!!!!! thanx

---

### Post by samsi on 2009-08-18
Wonderful!!!
Working as it should

Thanks a lot

regards

---

### Post by Schendje on 2009-08-18
For future visitors to this thread, could you guys tell us which method worked for you?

It'll help other people with the same problem. Glad you guys got it solved. :)

---

### Post by samsi on 2009-08-20
Glad to help 
I used the first suggestion, (install the bluez-compat etc) 

The only ongoing problem is that the mouse takes longer to "wake up" from being idle for a while, compared to time taken to do the same in XP

---

### Post by samsi on 2009-08-22
Update
Since the last post I have re-installed Ubuntu and tried to use the same solution listed above to solve the non-working bluetooth mouse problem
However the bluez-compat package was not available when I tried to get it using the Terminal

A few hours later and now that Ubuntu has downloaded a lot of updates, the package **IS **available, and the mouse now works again

---


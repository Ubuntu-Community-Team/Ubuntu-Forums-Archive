---
title: "Cant boot into ubuntu"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by suncross on 2010-01-05
I am on a new machine on a fresh install.  I recently spent a couple days trying to get my audio online, and I finally got it working to find out I cant use the install anymore (for some reason).

It gives me this error: 

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)..

I can't even boot into a live cd now because its giving me an error (and I have to reboot).  I decided to do a memtest on the live cd, and it is only 10% in and it is showing errors in the thousands.  What does this mean?  I may be a linux newb, but I have built plenty of computers in my time, and I know the hardware to be compatibal and in the right channels.

What does this mean?  (btw, when I first got that error I reinstalled, and now I got the error again so I know there has to be something really wrong).

---

### Post by albert s on 2010-01-05
im pretty new to all this, but have you verified the CD?

---

### Post by Sef on 2010-01-05
1) Instead of booting the Live CD, go down to "Check Disk for Errors" (or something similar.)

2) What are your system specs?

---

### Post by spiderbatdad on 2010-01-05
try editing the grub menu kernel option. Add:```
rootdelay=10 root=/dev/sda3
```Note sda3 is a guess at your ubuntu partition. Hang in there, there are other people on here very capable at helping you solve this issue.

---

### Post by pricetech on 2010-01-05
If memtest is finding errors then maybe the RAM is indeed bad.  I know you said it's a new box, but you might have gotten some defective memory.  I'd do the "reseat" thing first, of course.

---

### Post by audiomick on 2010-01-05
+1 pricetech.
Always check and exclude the simple things first (said he smugly, as he looked for the problem for hours before noticing the cable wasn't plugged in... :) )

At least make sure the RAM is in it's socket properly, particularly on a new machine.

---

### Post by suncross on 2010-01-05
Thank you for the suggestion guys, and I will try all this when I get home. 

> **pricetech said:**
> If memtest is finding errors then maybe the RAM is indeed bad. I know you said it's a new box, but you might have gotten some defective memory. I'd do the "reseat" thing first, of course.

It found errors in the tens of thousands at about 20% in.  However, I know the memory to be good.  I had windows 7 installed for about a week and I was running all kinds of apps and games.  There is no way that the ram would break that fast.  

> **Sef said:**
> 1) Instead of booting the Live CD, go down to "Check Disk for Errors" (or something similar.)

2) What are your system specs?

The disk seems fine.

Intel core2 duo LGA775
4 gigs of ddr2
Asus P5Q Turbo Pro (motherboard)
Ubuntu 9.1

---

### Post by mattbutsko on 2010-01-05
I received this error once when I installed a kernel related application after updating the system BUT before restarting for the updated kernel to take effect.

So, I think what happened was that the installed application was trying to use the old kernel and didn't see the new one, which crashed the OS somehow.

Anyway, whether I am wrong or not, reinstalling a fresh copy of the OS fixed the error.

---


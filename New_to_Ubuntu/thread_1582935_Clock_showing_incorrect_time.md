---
title: "Clock showing incorrect time"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by 10.04newbie on 2010-09-27
For some strange reason, since resizing my hard drive partitions, the desktop clock is showing 1 hour slow.

I have to keep changing the time, otherwise, when I reboot, the bios time is also i hour slow. 

Can anyone suggest how to correct this anomaly ?

---

### Post by julio_cortez on 2010-09-27
I've had something similar (don't know why, but everytime I install Ubuntu it has the clock 2 hours "back" than it should be and it affected also BIOS and Windows 7)..

I usually use a *sudo date -s "DD MMM YY hh:mm:ss"* to set the date.

So, if now it's September 27, 2010 and it's 12:38 PM, I'd just issue a **sudo date -s "27 SEP 10 12:38:00"**

I don't know if this helps you, for me it just gets the work done :)

---

### Post by 10.04newbie on 2010-09-27
Thanks for your reply. Sadly, that solution did not work for me.

This is very frustrating.

---

### Post by 10.04newbie on 2010-09-27
Managed to fix the problem as follows :-

In the terminal sudo time-admin

This brings up a screen with adminisrative rights for changing the time zone - In my case Europe-London

Clock automatically changed according to that time zone (GMT+1)

Now a happy bunny !:)

---


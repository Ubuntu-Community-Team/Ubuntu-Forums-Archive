---
title: "New(ish) to Ubuntu"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by labrat37 on 2008-12-25
Hey all,

I've been using Ubuntu for about a month now, and haven't had too many issues. There are a few things I haven't been able to fix though.

Whenever I log out I get colored flashing lines...they don't last long and I can still log out of the system, but I was wondering if this is something that can be fixed?

The 2nd problem I'm having: When I suspend the computer it locks itself up and I have to restart it. Is there anything I can do to fix this?

Running Ubuntu Intrepid
Processor: AMD Athlon(tm) 64 Processor 3200+
Graphics: ATI Technologies INC Radeon XPRESS 200M 5955 (PCIE)

If you need anymore system info from my end just let me know.

Thanks!

---

### Post by damis648 on 2008-12-25
Did you install the restricted drivers for your graphics card? (System>Administration>Hardware Drivers)

---

### Post by labrat37 on 2008-12-25
Yes, I'm using the FGLRX driver.

---

### Post by nhasian on 2008-12-25
yeah the lines on the screen sounds like a graphics driver issue.  

you can stop your computer from suspending by going to System->Preferences->Power Management Preferences.

note: for suspend to disk to work your swap parititon needs to at least as big as your ram.  most people do 1.5x to 2.0 times the size of their ram.

---

### Post by labrat37 on 2008-12-25
Thanks, I'll turn off suspension and increase my swap space, see if that helps. Guess there's not much I can do about the lines eh?

---

### Post by Scheater5 on 2008-12-25
You don't really need to increase your swap space and turn off suspend.  Increasing the swap space allows Hibernate to function, and Suspend is related to RAM.  So there's no real need do both fixes - turn off Hibernate, or increase your swap space.  But neither will fix Suspend.

---

### Post by labrat37 on 2008-12-25
Oh. O_o

Thanks for your help, both of you. Any other ideas on how to avoid a lock-up after suspension? I've already figured out its not related to X-Windows. :P

---


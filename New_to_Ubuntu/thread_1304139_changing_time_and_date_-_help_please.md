---
title: "changing time and date - help please"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by mjp29 on 2009-10-29
I have an Ubuntu box that I want to change the date and time on.  I am actually able to change the date; however, I can not make it change the time.  It keeps reverting back to the time it thinks it is.

I thought it was doing this because it was connected to the internet.  But I turned my router off, and I could still not get it to accept the time change I entered.  It just kept giving what it thought was the time int he upper right instead of the time I put in.

Any thoughts?

p.s. and if I get the date and time where i want it, then connect it back to the internet, will it synchronize with some atomic clock and time zone and take away my change

---

### Post by lrcaballero on 2009-10-29
Try this:

Once you click on the time/date bar - select Edit - then go to Time Settings and last Set System Time! 

Good luck


Luis

---

### Post by teward on 2009-10-29
you tried setting the time in the system settings (BIOS)?  (ask me if you don't know what I'm talking about)

I don't see anything in the basic time settings (on 9.04 Jaunty Jackalope) that would reset your system time automatically, except maybe your BIOS or (if you dual boot with Windows) your other operating system, or maybe you have some sort of time-syncing package/addon/thing installed on your system (if they even exist).

---

### Post by mjp29 on 2009-10-29
> **lrcaballero said:**
> Try this:

Once you click on the time/date bar - select Edit - then go to Time Settings and last Set System Time! 

Good luck


Luis


Thanks, but I can left click or right click on that time/date on the upper right and don't see any "edit" to select.

???

---

### Post by lrcaballero on 2009-10-29
when you click on it, a partial window opens in the bottom right?? then you'll see Locations on your left hand side go to the right and you will see Edit..... let me know??

---

### Post by sundar22in on 2009-10-29
Problem is related to Time zone you have selected during installation. Did you select the correct time zone for your place? If not, then correct the time zone and try, it might work.

-Sundar

---

### Post by mjp29 on 2009-10-29
ok I got it to work without seeing anything on bottom right.  I right clicked and reset time/date and clicked set system time and it started working.  I guess I wasn't looking around at bottom right.

by the way, is there a way to tell the system to sync to an atomic clock online for my time zone?

---


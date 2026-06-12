---
title: "Orage clock will not sync properly"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by Henrythewound on 2009-06-17
I recently installed Kuki Linux on my Acer Aspire One netbook and most everything works as advertised. However, the Orage Clock will not display the correct time. It gets the date correct but appears to be ~3 hours slow. I have chosen the timezone for my area (America/Phoenix) with no improvement. In fact, choosing another timezone (something in Europe for example) has no effect on the clock. This is not a big deal but I'd sure like to have it corrected.

Thx,
Joe

---

### Post by kerry_s on 2009-06-17
did you select the time zone in orage or the system?

---

### Post by Henrythewound on 2009-06-17
I set it within Orage. I don't know where to set it in the system

---

### Post by kerry_s on 2009-06-17
you know what, do this> **sudo apt-get install ntpdate**
reboot
if you set your time zone right at install, this will sync it with the internet time server, so you should then get the right time.

---

### Post by Henrythewound on 2009-06-18
Installed ntpdate, not sure when or where this is supposed to run. I never saw a setup menu on reboot. Is there a manual way I need to run the ntpdate program? Sorry, I'm sure I'm missing the obvious.

~Joe

---

### Post by Henrythewound on 2009-06-18
Following the ntpdate trend I did some research and ran ntpdate but got a "no servers can be used, exiting" error. I also tried installing ntpd after a bit of googling and got no error but no apparent result either.

EDIT: time appears to be correct after running the ntpd command - thanks for all the help!

---


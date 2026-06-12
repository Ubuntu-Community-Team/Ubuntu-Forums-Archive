---
title: "hostname issues"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by woztron on 2008-07-21
This is probably more of a n00b question but i couldn't start a thread there for some reason.

In my /etc/hosts and /etc/hostname i have different entries for some reason (i think i changed one when i was getting my wireless up on a fresh install).  I know how to change it, thats fine but becsause they're different i can't run any sudo commands from CLI as its the only user account (install is only 1 hour old FGS!)

Any ideas on how i can change either of the files?  The offender is the domain tacked on the end of the user in /etc/hostname  (woztron vs woztron.woznet)

Please?

---

### Post by Bachstelze on 2008-07-21
Use the recovery mode, it will give you a root shell directly so you don't have to use sudo to edit config files.

---

### Post by woztron on 2008-07-21
Thanks!!

---


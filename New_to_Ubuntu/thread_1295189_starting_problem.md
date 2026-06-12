---
title: "starting problem"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by zainflameworker7 on 2009-10-19
hi i just installed ubuntu but i cannot start it get the following error messages:
1: ACPI : aborted because no cpio magic
or
2: aborted because junk in compressed arcvhive
or 
3: aborted because broken padding

every time these messages come i have to restart my PC several times before ubuntu starts

MY System specs:
intel dual core prosser 2.0 ghz
2gb ram
80 gb hard drive


plese help:confused:

---

### Post by cmnorton on 2009-10-19
Please post more information.

Is this a dual boot?

Can you examine the logs once you finally boot (/var/log/messages /var/log/syslog and the output of dmesg)?

This sounds like you have an installation problem of some sort. Ubuntu systems normally boot quite easily and without errors like that.

---

### Post by sandyd on 2009-10-19
> **zainflameworker7 said:**
> hi i just installed ubuntu but i cannot start it get the following error messages:
1: ACPI : aborted because no cpio magic
or
2: aborted because junk in compressed arcvhive
or 
3: aborted because broken padding

every time these messages come i have to restart my PC several times before ubuntu starts

MY System specs:
intel dual core prosser 2.0 ghz
2gb ram
80 gb hard drive


plese help:confused:
did you check the ISO md5 sum?
and burn the cd again, at a slower speed.

p.s. try running memtest56.
you **may** have bad RAM.

---

### Post by Bondy on 2009-10-19
Boot the live cd and run partion editor under system > admin and see if it reports any errors on the drive 

If it does reboot windows and do a chkdsk and select both the options to fix errors

Also try running the install at the option screen press f6 and check the first 3 otions

---

### Post by Bondy on 2009-10-19
need a delete function

Sorry the answer I gave assumed it was a dual boot with windows although after re-reading theres no mention sorry just a habit of assuming

---

### Post by martrn on 2009-10-19
I think you have a broken ubuntu kernel ?

Try:

- Installing a different version of ubuntu (with a different kernel).
- Loading a rescue cd and upgrading (to get latest updates) if you can do that.
- Disable start/suspend/resume in BIOS if you can.

---


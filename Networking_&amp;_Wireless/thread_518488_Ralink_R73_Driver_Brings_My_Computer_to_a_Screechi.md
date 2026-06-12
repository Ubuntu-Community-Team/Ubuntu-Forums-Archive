---
title: "Ralink R73 Driver Brings My Computer to a Screeching Halt."
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by vaskeli on 2007-08-05
I just installed an Edimax 7318usg card on my system, which runs Feisty 7.04 (kernel 2.6.20-15). The card uses the serialmonkey r73 driver, and works perfectly fine for several hours, until the system slows down so much I can barely move the mouse. If I run top at this point, I find that 'r73' is using 98% of the cpu! Forcing a restart fixes everything for a few more hours. Please, somebody help me figure out what's going on!

---

### Post by kevdog on 2007-08-06
Might want to think about upgrading the rt73 serial monkey driver via the cvs version if you havent already done so.  Are you using the built-in drivers or did you compile them yourself.  The builtin drivers have a bug with Feisty.

---

### Post by vaskeli on 2007-08-06
I downloaded the daily cvs tarball and compiled it myself.

---

### Post by kevdog on 2007-08-06
Wow -- dont really know then

If you use the command
```
sudo /etc/init.d/networking restart
```
instead of rebooting, what does top say then.  Just trying to resort to plan B which is to save you from rebooting.

---

### Post by vaskeli on 2007-08-06
If I try to restart networking, it hangs on "reconfiguring network interface." I should mention that I can't even shut down the computer properly for the same reason.

Do you know where the relevant error messages would be logged?

---

### Post by kevdog on 2007-08-06
Here are logs you could check

/var/log/dmesg
/var/log/syslog
/var/log/boot

---


---
title: "suspend problem  help"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by blake7 on 2009-11-09
hi when i try to suspend or hibernate it fails to go though with to whole proses.
what happens is that it close down all operations and then makes the sceen go blank (but you can still see its charge)
then my lcd moon logo starts blinks confirming suspend but that it, it stops at that point with the sceen blank but still with the current going though and i cant reboot my laptop ibm x60s and my only opption at this point is to pull the plug and reboot

please can u helpp 
thank you

---

### Post by jbrown96 on 2009-11-09
Could you post the output of ```
lspci
``` and ```
tail -f 20 /var/log/Xorg.0.log
``` ```
tail -f 20 /var/log/kern.log
``` Does it ever get to suspend (does the moon stay solid)? I've had some trouble lately with a T61p, but only coming out of suspend, not entering. Try right clicking on your network icon and disabling wireless before suspending

---


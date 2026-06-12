---
title: "Install / uninstall issues (Flash Player)"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by cressrt on 2010-11-05
I have had to do a re-installation following a power failure on upgrade.  I tried to install the Flash Player from the Software sources, but this reached 82% and then froze.  I had to manually quit this and since then have nit been able to uninstall or reinstall flash.  Also the Package Manager does not work now.  Help!

Trying to uninstall Flash player it starts with this message and goes no further.
Waiting for other software managers to quit

With the Package Manager the following is returned:
An error occurred. The following details are provided. 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Running the above sudo has not changed anything and the Synaptic Package Manager will not run at all; re-booting makes no difference.

---

### Post by ibizatunes on 2010-11-05
run this in the terminal 
```
sudo dpkg --configure -a
```
that will try to finish the install off
post any error you get

---

### Post by linux18 on 2010-11-05
if you have firefox use the flash-aid extention:
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

made by a UF member, this extention solves *almost* every flash problem on linux

---

### Post by cressrt on 2010-11-05
Thanks for both responses, the first cured the problems with the install issues and I have installed the add on to ensure there are no problems again.

---


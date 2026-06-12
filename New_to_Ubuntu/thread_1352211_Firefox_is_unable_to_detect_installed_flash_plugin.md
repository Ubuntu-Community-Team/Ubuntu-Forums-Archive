---
title: "Firefox is unable to detect installed flash plugin"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by rkakkar on 2009-12-11
I installed the Adobe flash player through Ubuntu software centre, but FF is unable to detect it. The funny thing is, when it pops up the installer to install the plugin, FF says that its already installed!! However when it reloads the page, it still gives the annoying information bar stating the plugin isn't installed.

Any ideas?

---

### Post by pbrane on 2009-12-11
If you are running 64-bit Ubuntu you need to install the 64-bit Flash plugin manually. The deb in the repos installs the 32-bit version.

---

### Post by JohnnyB98604 on 2009-12-11
If the difference between 32 and 64 bit doesn't fix it, try restarting.  I know that sounds REALLY obvious but this is the "Absolute Beginners Talk" forum.

---

### Post by ukripper on 2009-12-11
> **pbrane said:**
> If you are running 64-bit Ubuntu you need to install the 64-bit Flash plugin manually. The deb in the repos installs the 32-bit version.

this is not entirely correct! 32bit flash plugin runs in 64bit ubuntu just fine. 

> **rkakkar said:**
> I installed the Adobe flash player through Ubuntu software centre, but FF is unable to detect it. The funny thing is, when it pops up the installer to install the plugin, FF says that its already installed!! However when it reloads the page, it still gives the annoying information bar stating the plugin isn't installed.

Any ideas?

@OP- Can you go to System-->Administration-->synaptic package manager and then in search field put flashplugin-installer. WHen it shows up make sure it is marked as green box.

---


---
title: "how to upgrade to 10.10"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by art_monu on 2010-12-10
I have a dual boot of windows xp and ubuntu 10.04 LTS desktop edition. I want to update it to 10.10, please tell me how to do it?

---

### Post by sikander3786 on 2010-12-10
First of all, make sure it is not a Wubi install (installed inside Windows) and Ubuntu is installed to its own separate partition. If it is a Wubi install, you need to do follow some more steps so it doesn't break after the upgrade. If that is the case, post back.

Only if it is a proper install (Ubuntu on its separate partition):

[https://help.ubuntu.com/community/MaverickUpgrades#Upgrade%20from%2010.04%20LTS%20to%2010.10](https://help.ubuntu.com/community/MaverickUpgrades#Upgrade%20from%2010.04%20LTS%20to%2010.10)

---

### Post by art_monu on 2011-02-15
I am using Ubuntu 10.04 LTS desktop edition. I installed all the updates from update manager and then clicked on upgrade to upgrade to 10.10 release. After some time I got an error as:

**An unresolvable problem occurred while calculating the upgrade:**
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.


Please tell me what's the solution for this..

---

### Post by Paqman on 2011-02-15
> **art_monu said:**
> 
 * Unofficial software packages not provided by Ubuntu


Your problem is most likely this. Are you connecting to any 3rd party repositories or PPAs? open up the Ubuntu Software Centre and it should show you what you've got installed from what source. Let us know if there's anything from outside the main Ubuntu or Canonical repositories.

---

### Post by art_monu on 2011-02-15
there is nothing installed from outside ubuntu or canonical partners. In fact all the programs provided by ubuntu are only installed.

---

### Post by Paqman on 2011-02-15
> **art_monu said:**
> there is nothing installed from outside ubuntu or canonical partners. In fact all the programs provided by ubuntu are only installed.

Ok, that's weird then. Unless somebody has any bright ideas i'd say that in the short term you should do what the error message suggested:
> **art_monu said:**
> 
If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.


To do this, hit Alt-F2 and type:
```
ubuntu-bug update-manager
```
and it will take you to Launchpad where you can open a bug report and attach the files it asked for.

After that, it looks like the easiest thing to do will be to reinstall using a 10.10 CD instead of doing an upgrade.

---


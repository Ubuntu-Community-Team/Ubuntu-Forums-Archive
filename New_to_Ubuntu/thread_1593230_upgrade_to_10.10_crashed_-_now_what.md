---
title: "upgrade to 10.10 crashed - now what?"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by chilimac02 on 2010-10-11
I have a Asus 1201n. I've used Ubuntu-Linux for a few years now...

When I clicked the distro-upgrade last night, everything was going along smoothly for a while. Then the computer overheated and shut-down. 1) I've never had that happen before, is that possibly a bug of some sort with this upgrade? 2) Now what, the 10.10 upgrade is broken, but the system (when I run an older kernel) thinks it has already upgraded...
How do I re-run the upgrade, so that it can really install?
-Justin

---

### Post by MooPi on 2010-10-11
Try this command in terminal and see if this corrects the problem.

```
sudo dpkg --configure -a
```
This will attempt to fix anything that was downloaded during the upgrade and complete unfinished results.

---

### Post by celticbhoy on 2010-10-11
[http://ubuntuforums.org/showthread.php?t=189520](http://ubuntuforums.org/showthread.php?t=189520)

See if any of the above suggestions will help

---

### Post by chilimac02 on 2010-10-11
thanks for the quick response!! I'll give those a try and then check back later.

---

### Post by bodhi.zazen on 2010-10-11
> **chilimac02 said:**
> I have a Asus 1201n. I've used Ubuntu-Linux for a few years now...

When I clicked the distro-upgrade last night, everything was going along smoothly for a while. Then the computer overheated and shut-down. 1) I've never had that happen before, is that possibly a bug of some sort with this upgrade? 2) Now what, the 10.10 upgrade is broken, but the system (when I run an older kernel) thinks it has already upgraded...
How do I re-run the upgrade, so that it can really install?
-Justin

Interrupted upgrades can sometimes be problematic.

Did you back up your data ?

If ```
sudo dpkg --configure -a
``` does not work, can you describe the problem you are having, error messages, etc ?

It may be easier to re-install and restore from back up.

---

### Post by chilimac02 on 2010-10-12
thanks for the help, everything is fixed now.

---


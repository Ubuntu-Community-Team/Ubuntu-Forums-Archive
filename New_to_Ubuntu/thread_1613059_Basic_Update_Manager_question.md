---
title: "Basic Update Manager question"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by jwalling on 2010-11-04
I finished upgrading from 8.04 to 10.04.1 and when I review updates in Update Manager I see linux updates like this
[INDENT][I]linux-headers-2.6.32-25 (New install)
linux-headers-2.6.32-25-generic (New install)
linux-image-2.6.32-25-generic (New install)[/I][/INDENT]

What is the significance of "**(New install)**"?

How is it different from any other linux update?

Thx

---

### Post by marshmallow1304 on 2010-11-04
Instead of providing a single package with the latest kernel, the repositories provide separate packages for different kernel versions.  There is a [metapackage]("https://help.ubuntu.com/community/MetaPackages") that always depends on the latest kernel.  When the metapackage is updated, the new version will pull in a new kernel (if available) as a set of packages, thus the "New Install" notice.  Old kernels may be safely removed via Synaptic, aptitude, apt-get, etc. but do no harm other than take up some disk space.

---

### Post by garvinrick4 on 2010-11-04
When you update and upgrade your system you get.
New packages-upgraded packages-obsolete packages (to remove).
Open a terminal:
```
sudo aptitude update && sudo aptitude safe-upgrade
```
You might have to install aptitude:
```
sudo apt-get install aptitude
```
Nice to learn about aptitude vs. apt-get

---


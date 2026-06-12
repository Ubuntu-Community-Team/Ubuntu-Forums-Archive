---
title: "4 Blocked Updates"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by Crunchy the Headcrab on 2009-07-08
Hey all.  Trying out KDE.  Kubuntu informs me that I am not allowed to upgrade these:

linux-generic 2.6.28.11.15
linux-headers-generic 2.6.28.11.15
linux-image-generic 2.6.28.11.15
linux-restricted-modules-generic 2.6.28.11.15

Now,  I am going to install the Nvidia proprietary driver from their website.  However I would like to update my kernel before I do that to save problems later.  So why are these blocked?

---

### Post by kandieyman on 2009-07-08
If you run
```
sudo apt-get dist-upgrade
```
from a terminal, do you get an error, or does it let you install?

---

### Post by Crunchy the Headcrab on 2009-07-08
It's doing that right now.  Downloading 2.26.28-13

Is apt-get dist-upgrade the cli command to update the kernel then?

Edit: It appears to have worked.

---

### Post by kandieyman on 2009-07-08
From the manual page for apt-get:

> dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary. So, dist-upgrade command may remove some packages. The /etc/apt/sources.list file contains a list of locations from which to retrieve desired package files. See also apt_preferences(5) for a mechanism for overriding the general settings for individual packages.

That is pretty confusing, but, yes, among other things, it is required to upgrade the kernel.

---

### Post by QIII on 2009-07-08
When you update the kernel, you may or may not get the changes reflected in your menu.lst.

You may have to manually edit menu.lst to be sure that you boot to the new kernel.

---

### Post by kandieyman on 2009-07-08
That is true, but do not worry about that unless you are sure that you are still booting into the old kernel. (Also, the most recent kernel updates are not for a new kernel, they are for an update to an existing kernel, so this doesn't apply in this case.)

---


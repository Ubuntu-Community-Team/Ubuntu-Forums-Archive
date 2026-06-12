---
title: "upgrade problem not being root"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by oleszek on 2011-05-09
Hi!

trying to upgrade from  8.04. (i think i have this version) with apt-get dist-upgrade and getting permission conflict.

lecheque@lecheque-laptop:~$ apt-get dist-upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

please help
leszek

---

### Post by compmodder26 on 2011-05-09
you need to use sudo before that command:

```
sudo apt-get dist-upgrade
```

apt-get needs root privileges to run.  So running as your regular user won't work.  Sudo allows you gain root privileges.

---

### Post by oleszek on 2011-05-09
Thank you!

sudo help, however not much upgrade happening

lecheque@lecheque-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

please advise

---

### Post by TheNerdAL on 2011-05-09
> **oleszek said:**
> Thank you!

sudo help, however not much upgrade happening

lecheque@lecheque-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

please advise

Are you trying to upgrade from 8.04 to 11.04?

---

### Post by coffeecat on 2011-05-09
If you are trying to upgrade to a newer version of Ubuntu, the "dist-upgrade" option for apt-get is not the one you need. This is a common misunderstanding. From man apt-get:

```
dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. So, dist-upgrade
           command may remove some packages. The /etc/apt/sources.list file
           contains a list of locations from which to retrieve desired package
           files. See also apt_preferences(5) for a mechanism for overriding
           the general settings for individual packages.
```In short, dist-upgrade doesn't do a version upgrade. If you want to upgrade from 8.04 to 10.04, have a look here:

[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

---

### Post by oleszek on 2011-05-09
thanks the above been helpful, solved ta ta

---


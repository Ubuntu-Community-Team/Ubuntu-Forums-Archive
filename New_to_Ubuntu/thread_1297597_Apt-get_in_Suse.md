---
title: "Apt-get in Suse?"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by Niko Johnson on 2009-10-21
i know this is the ubuntu forums but i was wondering if there is an equvilate to ubuntus apt-get in Suse.. i tried yum install but that was a no go... is zypper the apt-get alternative in this case?

---

### Post by Bachstelze on 2009-10-21
[http://en.opensuse.org/APT](http://en.opensuse.org/APT)

---

### Post by igknighted on 2009-10-21
You can use zypper (it's actually not bad at all), or use Yum or Apt.  I would stick with zypper, the repo's are optimized for it.  Apt for RPM is old and hasn't seen a lot of love in some time, and I'm not sure all the 3rd party repo's are available for Apt or Yum.

---

### Post by martrn on 2009-10-22
Have you tried asking at the opensuse forums about apt, if you ask there someone their might have some more knowledge their than at the ubuntu forums?
[http://forums.opensuse.org/]("http://forums.opensuse.org/")

---

### Post by OpenGuard on 2009-10-22
zypper is the way to go ( syntax is pretty much the same as for aptitude ) - no need to search for alternatives :)

---

### Post by swerdna on 2009-10-22
If zypper throws you, try the GUI at Yast --> Software --> Softyware management

---

### Post by RichardLinx on 2009-10-22
Zypper is the way to go when it comes to openSUSE. If you want to install something instead of "apt-get install" or "aptitude-get install" you can type "zypper install" or "zypper in". Example:
```
zypper install git
```
```
zypper in git
```
You can also use YaST.

You can search for sofware here: [http://software.opensuse.org/search](http://software.opensuse.org/search)

---


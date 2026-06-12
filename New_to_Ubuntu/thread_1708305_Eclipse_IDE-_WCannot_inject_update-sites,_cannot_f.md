---
title: "Eclipse IDE- W:Cannot inject update-sites, cannot find the correct config"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by gidra on 2011-03-16
When i launch gksudo eclipse it gives me "W:Cannot inject update-sites, cannot find correct config". When i go to install new software and choose galileo it just says pending.... Please help

---

### Post by gsocker on 2011-03-16
Don't run it as root.

Eclipse is intended to be run as your normal user id, even when installing updates, as it stores everything that was not part of the original install in your home directory(usually /home/your_userid/.eclipse). As a result, it does not need write access to the system directories to install/update anything.

---

### Post by gidra on 2011-03-17
Still problem persists :(

---

### Post by lores on 2011-05-18
Same here, has been happening since I installed Eclipse 3.6.0 from [https://launchpad.net/~eclipse-team/+archive/debian-package](https://launchpad.net/~eclipse-team/+archive/debian-package) on 11.04...

---


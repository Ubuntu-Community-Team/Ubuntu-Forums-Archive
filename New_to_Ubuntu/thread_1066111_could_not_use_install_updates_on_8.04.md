---
title: "could not use install updates on 8.04"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by Dinol on 2009-02-10
I'm using system 8.04 LTS, and I was unable to install updates--received the following error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


tried to use terminal with commmand above, but was told:

dpkg: requested operation requires superuser privilege

how to proceed?

---

### Post by taurus on 2009-02-10
Add the sudo in front of the command.

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by avtolle on 2009-02-10
Do```
sudo dpkg --configure -a
```sudo giving "superuser" status.

---

### Post by Dinol on 2009-02-10
Thanks folks--
I guess I sort of knew about sudo, but forgot. The sort of problem you get when our little system gets so user friendly.
Should the error messages contain more detail to help the forgetful somewhat beginner, like me?

---


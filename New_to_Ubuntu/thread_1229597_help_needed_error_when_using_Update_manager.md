---
title: "help needed error when using Update manager"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by Peterfc on 2009-08-02
Hi all

Update manager wants me to install updates but when i try i get the message listed below. Could someone explain what i need to do to get the update manager to install as per usual.

Peter

E: dpkg was interrupted, you must manually run 'sudo dpkg--configure-a' to correct the problem.
e:_cache->() failed, please report

SORRY GUYS I DID NOT READ THE POST FROM INTENSETUX

---

### Post by llamabr on 2009-08-02
Open a terminal, and do this:

```
sudo dpkg --configure -a
```

---

### Post by fooman on 2009-08-02
open a terminal (applications > accessories > terminal) and type, or copy/paste the following:

```
sudo dpkg--configure -a
```then follow it up with:

```
sudo apt-get update && sudo apt-get install -f
```hope that helps.

EDIT:  i am sooo slow,  llamabr beat me to it.

---


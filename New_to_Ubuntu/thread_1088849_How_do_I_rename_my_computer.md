---
title: "How do I rename my computer?"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by earthroamer on 2009-03-06
ubuntu 8.10 running in vmware player
everything is running fine, just want to change the computer name

First, there is no System->Administration->Network in my menu, only System->Administration->Network Tools, so there is no General tab.

I tried Alt-F2, gksu network-admin, supplied the root password, but nothing happens.

---

### Post by taurus on 2009-03-06
If you want to rename your computer, you need to use the same name in /etc/hosts and /etc/hostname or you won't be able to use sudo anymore.  Do that from a recovery mode unless you edit both files at the same time.

---

### Post by kanikilu on 2009-03-06
I think you can manually change that in /etc/hostname and /etc/hosts.

// Edit - Too slow ;)

---

### Post by earthroamer on 2009-03-06
> **taurus said:**
> If you want to rename your computer, you need to use the same name in /etc/hosts and /etc/hostname or you won't be able to use sudo anymore.  Do that from a recovery mode unless you edit both files at the same time.

Would that be

gksudo gedit /etc/hostname /etc/hosts


???

---


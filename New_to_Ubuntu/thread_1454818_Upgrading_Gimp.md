---
title: "Upgrading Gimp"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by furoido on 2010-04-15
I'm trying to upgrade Gimp 2.6.1 to 2.6.8 but get this message:

andrew@andrew-desktop:~$ apt-get install gimp
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Can anyone suggest how I can upghrade my Gimp?

Thanks!

---

### Post by dullard on 2010-04-15
**sudo** apt-get install gimp

should do it.

---

### Post by furoido on 2010-04-15
Thanks!!

---

### Post by Paqman on 2010-04-15
> **furoido said:**
> I'm trying to upgrade Gimp 2.6.1 to 2.6.8 

If you want to update your packages, then you should use:
```
sudo apt-get update && sudo apt-get upgrade
```

Alternatively, open Update Manager and hit "check" (or Synaptic and hit "refresh"). Doing any of these will offer you all the updates that are available for your system.

---


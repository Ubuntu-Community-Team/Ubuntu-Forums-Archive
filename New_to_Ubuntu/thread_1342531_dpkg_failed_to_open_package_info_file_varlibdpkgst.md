---
title: "dpkg failed to open package info file /var/lib/dpkg/status"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by lance bermudez on 2009-11-30
dpkg failed to open package info file ´/var/lib/dpkg/status´ for reading: No such file or directory

HI i need help what does this mean? I look and the computer is right no file called status but every thing else is their leading up to the file. in the dir i have
alternatives
cmethopt
diversions
diversion-old
info
lock
parts
statoveride
statoveride-old
triggers
updates
were do i get a status from? is their a backup someware for the status?

---

### Post by wojox on 2009-12-03
May work may not. Won't hurt if it doesn't.

```
sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/
```

Rename:

```
sudo mv /var/lib/dpkg/dpkg.status.0 /var/lib/dpkg/status
```

---

### Post by Soul-Sing on 2009-12-03
please use nautlus and navigate to the dpkg status content of the file. it is not a directory as dpkg info. ;)

---

### Post by lance bermudez on 2009-12-04
that did not work. Also i do not have a gui. synptic was tring to intall an update for gdm when i lost the system. At the time I was also install a ubuntu driver for my wirless card.

---


---
title: "command line achieve similar function of sata hdd hotswap"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by say2sky on 2009-01-10
too many hdd connect to pc. need to access file in any hdd but don't want to consume power all the time.

I want a command to achieve similar hotswap of any sata hdd by software ie. a command to power off any one hdd and also can power on them again.

---

### Post by handydan918 on 2009-01-10
george not understand.

---

### Post by The-IRS on 2009-01-10
try using understandable sentences

---

### Post by say2sky on 2009-01-10
> **handydan918 said:**
> george not understand.

I want command line to control power to any sata hdd connected to pc.
ie. similar the manually hotswap but not take off hdd physically.

---

### Post by say2sky on 2009-01-10
> **The-IRS said:**
> try using understandable sentences

perhaps hotswap used here is not very good. 

I want to power on/off any hdd/not system hdd connected by linux command.

---

### Post by handydan918 on 2009-01-11
> **say2sky said:**
> I want command line to control power to any sata hdd connected to pc.
ie. similar the manually hotswap but not take off hdd physically.

Dunno. Try man hdparm.

---

### Post by say2sky on 2009-01-11
> **handydan918 said:**
> Dunno. Try man hdparm.

I have tried.

enter sleep mode
```

hdparm -Y /dev/hd* 

```

but some daemon will check the sleep hdd in regular interval.
so I say I need command doing completely poweroff similar to do hotswap manually.

---


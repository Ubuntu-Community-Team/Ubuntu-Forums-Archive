---
title: "Identifying ports"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by grantmcduling on 2011-05-25
Hi, How can I go about identifying which port my usb adapter is plugged into? I need to choose between /dev/ttyS0, S1, USB0, USB1 etc.

Regards
Grant

---

### Post by Grenage on 2011-05-25
Your USB adapter is probably USB0 or USB1, and I'd wager that 1 is a good bet.  I assume that the port doesn't exist *until* you plug in the adapter?

---

### Post by ApOgEEs on 2011-05-25
Normally, it should be /dev/ttyUSB0 or /dev/ttyUSB1

you can check it for sure from this command on terminal:
```
$ dmesg
```

---


---
title: "telinit 1 hanging the pc"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by kalimojo on 2011-07-09
im on 11,04

trying to get into single user mode

tried init 1 and telinit 1

both hang the machine

any ideas folks ?

---

### Post by wojox on 2011-07-09
```
sudo init 3
```

Doesn't work?

---

### Post by matt_symes on 2011-07-09
Hi

If Wojox's suggestion does not work (you do need to be root) then check the log files.

```
tail -fn30 /var/log/syslog
```That would be a good place to start. Run that command in a terminal and then try to change run levels in a different terminal or using screen.

Kind regards

---


---
title: "how to have a machine shut itself down"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by Dave.B on 2010-02-10
is their a wat to have a machine shut itdelf down at a certain time?

please let me know

thanks

---

### Post by thatguruguy on 2010-02-10
Read [this]("http://ubuntuforums.org/showthread.php?t=925450").

---

### Post by Rhubarb on 2010-02-10
You could just use the **shutdown** command like thus:
```
sudo shutdown -h hh:mm
```
Where hh:mm is the time you wish to shutdown your computer in 24 hour format.
So if you wish to shutdown your computer at 5:30pm (this will not shut down at 5:30pm everyday, it will just shutdown the once), you would run:
**sudo shutdown -h 17:30**

---

### Post by switch10 on 2010-02-10
> **Rhubarb said:**
> You could just use the **shutdown** command like thus:
```
sudo shutdown -h hh:mm
```
Where hh:mm is the time you wish to shutdown your computer in 24 hour format.
So if you wish to shutdown your computer at 5:30pm (this will not shut down at 5:30pm everyday, it will just shutdown the once), you would run:
**sudo shutdown -h 17:30**

you can also write a message after, i.e.

```
 sudo shutdown -h 22:30 your computer will shutdown in 10 minutes. 
```

prints "your computer will shutdown in 10 minutes" in the terminal.

---


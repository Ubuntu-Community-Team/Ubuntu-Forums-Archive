---
title: "UserSetup failed with exit code 10"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by Nevyn on 2009-06-09
Trying to install Xubuntu 9.10 via USB stick. Booted live without problems, but when I reached the partitioning step in the installation process I receive a popup error named "UserSetup crashed" that says
```
UserSetup failed with exit code 10. Further information may be found in /var/log/syslog. [...]
```
I then get the option to quit, continue anyway or try again. If I choose try again, the same popup is viewed agin and again.

syslog shows no errors obvious to me, the two last lines that are the ones that look relevant says:
```
[date, time] ubuntu ubiquity[6262]: debconffilter_done: UserSetup (current: UserSetup)
[date, time] ubuntu ubiquity[6262]: dbfilter_handle_status: ('UserSetup', 10)
```

No answers googling or searchinig the forums.
Would really appreciate an answers since I need linux installed to be able to use the computer in a basic linux course.

---

### Post by nairbv on 2009-08-02
I have the same issue attempting to install eeebuntu nbr 3.0.1 on an eee pc 701.

---

### Post by Nevyn on 2009-09-05
I know it was a long time ago, but my solution to the problem was to first format my USB stick to FAT16 using GParted, and then do it all over again (you obviously need to use USB Startup Disk Creator after you've formatted).

---


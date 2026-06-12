---
title: "[SOLVED] System time"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by pradeepbp on 2008-12-09
The system time as shown by ubuntu is always wrong on my laptop. Even if I change it, the next time I boot, the time is shown wrongly.

What could be the reason?

---

### Post by w4ett on 2008-12-09
Low CMOS battery voltage is the primary culprit normally.....also if you dual boot, the other os might be adjusting the time for you.

Also check that you are not displaying UTC instead of Local Time

---

### Post by linux_tech on 2008-12-09
Does bios show correct system time? check this first
If not, then cmos battery may be going and need replacing. But you can correct it and see if it stays or not
If so then adjust time in Ubuntu; make sure timezone is correct

click on clock select locations to adjust timezone 
right click to adjust date&time

---

### Post by pradeepbp on 2008-12-09
I think the alternate OS (winXP) was the culprit in this case. There should not be any problems with the cmos battery as the laptop is hardly 6 months old.

For now the time is correctly shown.

thanx.

---

### Post by iponeverything on 2008-12-09
first set the system to the correct time/TZ

then run:

```
sudo hwclock --systohc
```

---


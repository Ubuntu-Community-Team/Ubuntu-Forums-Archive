---
title: "can't change date?"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by garyed on 2009-11-04
I'm dual booting Hardy 8.04 & also Ubuntu Studio Gusty.
The time of day is hours off between the two.
If I change one to the correct time then when I reboot the other one changes to the wrong time & vise versa.

I do have the same user name & password on both but I can't see why that should be a problem? 
Any ideas?

---

### Post by Old *ix Geek on 2009-11-04
Have you checked to make sure you have the same time zone set on both?

---

### Post by mcduck on 2009-11-04
Sounds like one is configured to consider system time as UTC while the other assumes the system clock to run in local time..

The setting for this is in /etc/default/rcS, just make sure that both have the following section (you can enable or disable it as you wish, as long as both Ubuntu installs have the same setting):
```

# Set UTC=yes if your system clock is set to UTC (GMT)
UTC=no
```

---

### Post by alphaniner on 2009-11-04
The reason 'fixing' one 'breaks' the other is that you are actually changing the clock on the motherboard.  As Old *ix Geek said, check your timezones.

---

### Post by garyed on 2009-11-04
Thanks for the ideas,
I'm sorry i had to leave my computer right after i posted.
I'm checking your suggestions now & I'll post back.

---

### Post by garyed on 2009-11-04
> **mcduck said:**
> Sounds like one is configured to consider system time as UTC while the other assumes the system clock to run in local time..

The setting for this is in /etc/default/rcS, just make sure that both have the following section (you can enable or disable it as you wish, as long as both Ubuntu installs have the same setting):
```

# Set UTC=yes if your system clock is set to UTC (GMT)
UTC=no
```

You were right!
One version had UTC= yes while the other UTC=no
Changing "no" on one to "yes" put them in sync.
They both showed the same time zone EST (New York) before but they still wouldn't sync up until I changed that file.
Thanks again to all for the help.

---


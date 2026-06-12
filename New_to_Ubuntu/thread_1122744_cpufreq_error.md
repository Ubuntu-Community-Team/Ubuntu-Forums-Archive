---
title: "cpufreq error"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by vasiauvi on 2009-04-11
Hello all,
I am getting this error from some time :
```
/etc/rc.local : 13: cannot create /sys/devices/system/cpu/cpu0/cpufreq/phc_controls : Directory nonexistent
```
I don't do anything special when this error appear.And it's appearing on black screen (CLI I think).
Anyone knows what's mean??
Thank you!

---

### Post by PukingPenguin on 2009-04-11
Try
```
cd /sys/devices/system/cpu/cpu0/cpufreq
``` and then ```
ls
```just to see what's there.

---

### Post by vasiauvi on 2009-04-11
This is what i have there:

"affected_cpus     related_cpus                   scaling_governor
cpuinfo_cur_freq  scaling_available_frequencies  scaling_max_freq
cpuinfo_max_freq  scaling_available_governors    scaling_min_freq
cpuinfo_min_freq  scaling_cur_freq               scaling_setspeed
ondemand          scaling_driver                 stats"

---


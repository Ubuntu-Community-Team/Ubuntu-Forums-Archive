---
title: "Core 2 Duo throttling issues"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by B34ST1Y on 2011-07-15
I have a Core 2 Duo and Ubuntu 11.04 and it seems that my CPU is running much slower than it should be. I have an ATI card and everything installed fine there, but I've had trouble in the past with my CPU not being at full throttle & wasn't able to resolve it. In Windows, I use RM Clock to turn of "extended throttling" and C1E but there doesn't seem to be a similar feature in Ubuntu.

Can someone point me in the right direction? Many thanks.

---

### Post by B34ST1Y on 2011-07-15
I've tried installing cpufreq but when I issue ```
lsmod | grep cpufreq
``` it returns nothing.

---

### Post by RoyLongbottom on 2011-07-15
[FONT=Verdana][SIZE=2]I am also a relative newbie and am converting my Windows benchmarks to run under Linux (using Ubuntu):[/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2]http://www.roylongbottom.org.uk/linux benchmarks.htm#anchor13[/SIZE][/FONT][FONT=Verdana] [/FONT][FONT=Verdana] [/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2]I have encountered the same problem using a Core 2 Duo. When only using 1 CPU, it runs at 1.6 GHz instead of 2.4. This might have started after I installed CPU Frequency Scaling Monitor. Anyway, with this added to the panel (top bar), I have to left click and select Performance or 2.4 GHz then right click for Preferences, to select the other CPU, followed by left click to increase the CPU frequency for that core.[/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2]The settings need changing after every power on. See Successes, Burn-In and Reliability Testing Apps in above HTM, reporting three times performance improvement using two cores.[/SIZE][/FONT]
[FONT=Verdana][SIZE=2] [/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Roy[/SIZE][/FONT]

---

### Post by patchwork on 2011-07-15
By default, the processors are throttled to the ondemand setting after one minute from boot.  This is a power saving feature, which still allows the processor to run at full speed when required.

If you want to prevent the throttling, and you have sufficient privileges, you can edit the /etc/init.d/ondemand file from 
```
...for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
    do
        [ -f $CPUFREQ ] || continue
        echo -n ondemand > $CPUFREQ
    done...

```

to 
```
...for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
    do
        [ -f $CPUFREQ ] || continue
        echo -n performance > $CPUFREQ
    done...

```

to prevent the change to ondemand mode after boot.

This shouldn't be necessary, however, as the processor should run at full speed when needed in ondemand mode.

---


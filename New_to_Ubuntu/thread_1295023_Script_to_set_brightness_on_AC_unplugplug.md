---
title: "Script to set brightness on AC unplug/plug"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by humphreybc on 2009-10-19
Hi, i'm trying to work out the command to set the brightness to 0 when the AC is unplugged (on battery), and when the AC is plugged in, set it to 100%.

At the moment, I have a script in /etc/acpi/battery.d called optimizations.sh with the following in it:

```

echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

echo min_power > /sys/class/scsi_host/host0/link_power_management_policy

```

This works well to change those settings. I've looked for something to change brightness, but I think Toshiba laptops change brightness differently to other laptops.

What command should I put in that script to set the brightness to zero?

---


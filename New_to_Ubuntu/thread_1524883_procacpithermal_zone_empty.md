---
title: "/proc/acpi/thermal_zone empty"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by CharlesA on 2010-07-05
Hi,

Trying to figure out why /proc/acpi/thermal_zone is empty on two of the machines I've checked. One has a Gigabyte mobo with E6500 CPU, the other is an Asus mobo with E8500 CPU.

I did check a machine with an Abit mobo running an E2200 CPU and it had stuff in /proc/acpi/thermal_zone.

Is there something special I need to do to get a reading on those other two mobos? (I want to keep an eye on the temps by checking landscape-sysinfo)

Thanks.

---

### Post by cariboo on 2010-07-06
I don't have anything in /proc/acpi/thermal_zone on any of my desktop systems. 

I set up lm-sensors by running in a terminal:

```
sudo sensors-detect
```

then install the sensors-applet, and add the sensors to the top panel.

---

### Post by CharlesA on 2010-07-06
Thanks. That's what I ended up doing as well. If I knew python, I might be able to edit the landscape-sysinfo temperature script to pull the info from lm-sensors, but I've got no idea where to start.

---


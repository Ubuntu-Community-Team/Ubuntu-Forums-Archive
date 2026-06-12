---
title: "no /proc/acpi/battery/BAT0/state :("
date: 2010-10-02
forum: New to Ubuntu
---

### Post by honeybear on 2010-10-02
```
 cat /proc/acpi/battery/BAT0/state
cat: /proc/acpi/battery/BAT0/state: No such file or directory

```

Hello, 

On my laptop there is no info about my battery of notbook. Why? acpi is surely installed but no info :-(
what is it the prob with it? I check to search in /proc and no *bat*

---

### Post by Hippytaff on 2010-10-02
try installing acpi, or using acpi -V if you have it already

To view battery info

---

### Post by honeybear on 2011-09-30
> **Hippytaff said:**
> try installing acpi, or using acpi -V if you have it already

To view battery info

it is an indication, but the /proc/acpi/battery is missing :( 

what does it mean below? 90% of power?

```
:~$ acpi -V
Battery 0: Discharging, 0%, rate information unavailable
Battery 0: design capacity 2400 mAh, last full capacity 2179 mAh = 90%
Adapter 0: off-line
Thermal 0: ok, 43.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 93.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 85.0 degrees C
Cooling 0: Processor 0 of 0
Cooling 1: Processor 0 of 0

```

---


---
title: "eeepc"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by timremy on 2010-07-24
hello

i am using ubuntu netbook edition on a eeepc 1005ha.

is there a way to display the cpu temperature.

please make it simply if possible.

thank you

timremy

---

### Post by kerry_s on 2010-07-24
accessories-> terminal

type: **cat /proc/acpi/thermal_zone/THRM/temperature**

---

### Post by timremy on 2010-07-25
did not work

cat /proc/acpi/thermal_zone/THRM/temperature
cat: /proc/acpi/thermal_zone/THRM/temperature: No such file or directory


timremy

---

### Post by hackerseraph on 2010-07-25
i recommend installing lm-sensors

```
sudo apt-get install lm-sensors sensors-applet
```

then type the following to display your temperature simply

```
sensors
```

taking it a step further, you can put your temperature on your panel by going, because the command i gave you above, installed the sensors-applet.

right click your gnome panel
click on add to panel
search harware
add Hardware Sensors Monitor

Configure it as you need to by right clicking and going to preferences

---

### Post by timremy on 2010-07-25
hello hackerseraph

it worked.

thank you.


timremy



solved

---


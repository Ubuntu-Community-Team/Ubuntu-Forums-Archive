---
title: "Checking CPU Temp"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by Tman5293 on 2009-09-19
Hi,

I think i might be having an overheating problem since my computer keeps turning off at random and i have to pull the power cord out and put it back in to get it to turn back on.

I was wondering if there is a way for me to check my CPU temp??????

Any Help Is Appreciated!

---

### Post by shae on 2009-09-19
try
```
cat /proc/acpi/thermal_zone/THM/temperature
```

---

### Post by earthpigg on 2009-09-19
[Linux-monitoring Sensors]("http://en.wikipedia.org/wiki/Lm-sensors")

to install:
```
sudo apt-get install lm-sensors
```

to configure:
```
sudo sensors-detect
```
(and say yes to everything)

to display as many sensor readouts as your hardware has sensors:
```
sensors
```

---

### Post by mr clark25 on 2009-10-31
i want to check my cpu temp to, and i cant.

i tried the lm-sensors thing mentioned, and then it says thet no sensors were found.....

---

### Post by kemorc on 2009-10-31
same here, no sensors found. fail!

---

### Post by kansasnoob on 2009-10-31
With the Gnome desktop I install "sensors-applet":

```
sudo apt-get install sensors-applet
```

It always pulls in the required dependencies and then I can add it (Hardware Sensors Monitor) to the panel and if you right click it you can change properties.

Not sure if that would work in Studio or KDE though.

---

### Post by rburkartjo on 2009-11-01
kansas tks for the info

---


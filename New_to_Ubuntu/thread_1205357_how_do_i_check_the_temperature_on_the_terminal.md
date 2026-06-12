---
title: "how do i check the temperature on the terminal?"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2009-07-05
how do i check the temperature on the terminal?

---

### Post by earthpigg on 2009-07-05
```
sudo apt-get install lm-sensors
```

then, to configure it:

```
sensors-detect
```

then, to check your processor temp:

```
sensors
```

---

### Post by x33a on 2009-07-05
+1 for earthpigg.

and if you want a gui frontend to lm-sensors, try xsensors
```
sudo aptitude install xsensors
```

---

### Post by tgalati4 on 2009-07-06
sudo apt-get install hddtemp
man hddtemp

/proc/acpi/thermal_zone/THRM$ cat temperature
temperature:             30 C

This is on a Dapper Drake machine.  Location of your temperature file will vary depending on what version of the kernel you are running.

After you have lm-sensors and hddtemp set up, check out the status bar gdesklets to display all of this new found info.

---

### Post by Mark Phelps on 2009-07-06
Couple of additional hints ...

It's been a while, but I believe you have to do "sudo sensors-detect"

Also, when you do "sensors", you should get a long list of sensor names and values.  If you don't, lm-sensors didn't detect any useful sensors on your machine.  Also, it's not unusual to get two sets of different temps for the same CPU(s).  Generally, the set with the higher temps is the one to trust.

---


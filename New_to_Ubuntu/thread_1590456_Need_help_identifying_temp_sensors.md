---
title: "Need help identifying temp sensors"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by Psycho Taffy on 2010-10-07
Hello.  I need help identifying the temp sensors (see attached). I'm running Ubuntu 10.10RC.
 

 I only have a single core processor, so are Core0 and Core1 just reading the same sensor?
 

 What is temp1 and THRM? The temps are always the same and too low to be the CPU. (Too low compared to when I had XP on this computer, the core temp was always in the mid 30's, just like the readings of Core0 and Core1.) So what are the low temps displayed as temp1 and THRM?
 

 Thanks for you help.

---

### Post by andrewthomas on 2010-10-07
post the output of 
 
```
 
sensors

```
 
in the terminal
 
It should show a bit more info

---

### Post by Psycho Taffy on 2010-10-07
I've already done that.  It shows even less information.

---

### Post by andrewthomas on 2010-10-07
the other temps are probably the motherboard temp.
 
What CPU do you have?

---

### Post by Psycho Taffy on 2010-10-07
AMD Athalon 64 3500+

---

### Post by andrewthomas on 2010-10-07
No idea why it is showing two core temps.

---

### Post by Psycho Taffy on 2010-10-07
I'm pretty sure that the core sensors are just reading the core from two different access points.  My main confusion is the temp1 and THRM temperatures. 

If I run this...

```
cat /proc/acpi/thermal_zone/*/temperature
```...it comes up with the low temp shown for tem1 and THRM.

FYI, here is where I originally found the install:
[http://www.lucidtips.com/2009/06/06/monitor-cpu-and-hard-drive-temperatures-on-ubuntu-linux/](http://www.lucidtips.com/2009/06/06/monitor-cpu-and-hard-drive-temperatures-on-ubuntu-linux/)

---

### Post by andrewthomas on 2010-10-07
Which are probably sensors on the motherboard.

---


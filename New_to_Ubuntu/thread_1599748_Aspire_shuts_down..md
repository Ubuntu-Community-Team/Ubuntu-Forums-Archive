---
title: "Aspire shuts down."
date: 2010-10-18
forum: New to Ubuntu
---

### Post by Vege 4wd on 2010-10-18
Hi my laptop has been shutting down lately. Seems mostly when using k9.
  My fan is working but the the lap top feels warm.  

 Is there an application available so I can see the temp?
 Also could there be some conflict with k9?

Any help would be appreciated.

---

### Post by Stephen Morgan on 2010-10-18
acpi -V

That'll tell you the temperature, you should get output like this:

Adapter 0: on-line
Thermal 0: ok, 47.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 92.0 degrees C
Thermal 1: ok, 45.0 degrees C
Thermal 1: trip point 0 switches to mode critical at temperature 92.0 degrees C
Thermal 1: trip point 1 switches to mode passive at temperature 90.0 degrees C
Cooling 0: LCD 7 of 9
Cooling 1: Processor 0 of 3
Cooling 2: Processor 0 of 3

If it isn't installed, sudo apt-get install acpi

---

### Post by Vege 4wd on 2010-10-18
Thank you for the reply. It says my cpu at 49.  the application works well.:)
 Is it possible to change the trip points?

I have a duo core cpu T2350@1.8ghz.   Could k9 be too much to handle?

---


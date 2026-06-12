---
title: "lm-sensors"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by DarinB on 2009-08-23
can some one tell me what all the different temperature readings mean.some i obviously know but other i don't like temp1 vcores and difference between cores and cpu 
like temp1 
vcore1 
vcore2
m/b temp
cpu
core0
core1

---

### Post by Sam Lars on 2009-08-25
You could try looking in your BIOS to see if it shows you any info about sensors.
temp1 - Some other temperature sensor... depends on your motherboard.
vcore1 - CPU core voltage
vcore2 - CPU core voltage
m/b temp - Temp of motherboard
cpu - Temp of CPU
core0 - Not sure... what value is it showing?
core1  - Not sure... what value is it showing?

---

### Post by mcduck on 2009-08-25
> **DarinB said:**
> can some one tell me what all the different temperature readings mean.some i obviously know but other i don't like temp1 vcores and difference between cores and cpu 
like temp1 
vcore1 
vcore2
m/b temp
cpu
core0
core1

vcore1 and vcore2 are processors voltages (one for each core on a dual-core CPU).

m/b temp is the motherboards ambient temperature sensor. Usually kind of pointless as it's location varies between motherboards and thus it's not really useful for telling the motherboards temperature *or* the ambient temperature. :/

CPU temperature is usually the motherboard's CPU temperature sensor, located in the CPU socket.

core0 and core1 temperatures come form the temperature diodes built into the CPU itself. Once again, one for each core. These are the ones that tell the the most accurate CPU temperature.

However all the readings from lm-sensors should be taken with a grain of salt unless you have already compared them to readings from your BIOS or some other source and edited the sensors.conf file to assign all sensor data to correct readings (and adjusted the multipliers and other possibly necessary calculation formulas). Even with the same sensor choip the way how sensors are handles on different motherboards varies, and lm-sensors doesn't take that into account automatically but instead just outputs whatever data the sensors give it, bo matter if it makes any sense or not..

---


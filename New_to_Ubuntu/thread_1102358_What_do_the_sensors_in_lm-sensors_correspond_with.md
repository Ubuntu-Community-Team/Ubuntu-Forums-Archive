---
title: "What do the sensors in lm-sensors correspond with?"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by Bobby505 on 2009-03-21
Hey, I was wondering if anyone could give some info on exactly where the various sensors that lm-sensors uses are and what they are measuring?

I've got an A8V-VM mobo and AMD Athlon 64 3700+ cpu.

I can work out that GPU is measuring the temperature of my graphics chip (but would that be the onboard graphics chip or my 7800GTX pcie card?)

Same goes for 'CPU temp' as that's self explanatory!!

But what about 'Core0 Temp', 'Core1 Temp', 'Sys Temp' and 'AUX Temp'? 

Many thanks,

Bobby

---

### Post by blastus on 2009-03-21
I don't know about Core0 and Core1 in your case because the Athlon 64 3700 is a single core CPU. On a dual-core system these would be the temperatures of each core.

I think "Sys Temp" is the *motherboard temperature*. Someone correct me if I'm wrong but there is usually a temperature sensor on either the NorthBridge or SouthBridge chipset. The system temperature is the reading from that sensor and should correspond to the system temperature shown in the BIOS.

I'm not sure what AUX temperature is. To be honest I've used sensors for a while and still haven't been able to figure everything out.

---


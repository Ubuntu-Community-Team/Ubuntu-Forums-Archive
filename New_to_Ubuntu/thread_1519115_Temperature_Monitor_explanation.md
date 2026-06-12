---
title: "Temperature Monitor explanation"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by venicequeen7706 on 2010-06-27
Hi I recently installed computertemp from synaptic to log my computer temperatures because i think its running hotter than usual. Having done so, I'm not sure what the preference options mean. There are thermal zones 1-4 and there are 3 sensors to choose from ACPI, Kernal i2c sensors, and Kernal 12c sensors (hwmon). I have no idea what any of that means or what i should look at and what to ignore. any help or advice would be great. also it says thermal zone 2 is at 70 degrees c. that seems a lot to me. should i be concerned?

---

### Post by tgalati4 on 2010-06-27
Yes.

Open a terminal and post the output of:

sensors

---

### Post by venicequeen7706 on 2010-06-27
chris@chris-laptop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +46.0°C  (crit = +105.0°C)                  
temp2:       +66.0°C  (crit = +115.0°C)                  
temp3:       +32.9°C  (crit = +105.0°C)                  
temp4:       +45.0°C  (crit = +110.0°C)                  

chris@chris-laptop:~$

---

### Post by tgalati4 on 2010-06-28
You can google your laptop model to find out where the thermal sensors are located.  I would guess 1 is CPU, 2 is GPU, 3 is battery, 4 is charge circuitry.  You want to keep chips below 70C.  100C will burn up a chip quickly.

---


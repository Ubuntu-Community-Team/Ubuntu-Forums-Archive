---
title: "safe cpu temps while doing folding@home"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by steve101101 on 2009-04-26
Hey. My cpu cores are hovering around 67-70 degrees C according to coretemp after about 2 solid days of folding. Is this safe. I have a Q6600 I believe. 

```

steven@steven-desktop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +120.0°C)                  

it8718-isa-0290
Adapter: ISA adapter
in0:         +1.22 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +3.06 V  (min =  +4.06 V, max =  +3.95 V)   ALARM
in2:         +3.36 V  (min =  +0.00 V, max =  +3.54 V)   
in3:         +3.04 V  (min =  +4.06 V, max =  +4.08 V)   ALARM
in4:         +2.98 V  (min =  +3.82 V, max =  +4.02 V)   ALARM
in5:         +0.06 V  (min =  +4.05 V, max =  +2.99 V)   ALARM
in6:         +0.10 V  (min =  +0.00 V, max =  +4.02 V)   
in7:         +2.99 V  (min =  +4.06 V, max =  +4.02 V)   ALARM
in8:         +3.15 V
fan1:       2960 RPM  (min =   27 RPM)
fan2:          0 RPM  (min =   10 RPM)  ALARM
fan3:       2156 RPM  (min =   10 RPM)
temp1:       +87.0°C  (low  =  -1.0°C, high = -65.0°C)  sensor = thermistor
temp2:       +42.0°C  (low  = +126.0°C, high = +127.0°C)  sensor = thermistor
temp3:       -26.0°C  (low  = +126.0°C, high = -18.0°C)  sensor = thermistor
cpu0_vid:   +0.000 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +70.0°C  (high = +84.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +67.0°C  (high = +84.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +66.0°C  (high = +84.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +68.0°C  (high = +84.0°C, crit = +100.0°C)

```

---

### Post by steve101101 on 2009-04-26
bump

---

### Post by nandemonai on 2009-04-26
It's not a dangerous temperature.. yet. Does seem awful high for those processors.

Stock cooling?

Might want to consider using a better heatsink / fan and reapplying thermal paste.

My 8500 C2D never goes above 55 under heavy load (100% CPU) and it's over clocked.

Out of interest.. what is folding?

---


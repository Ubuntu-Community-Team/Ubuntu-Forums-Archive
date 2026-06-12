---
title: "Sensors Output Question"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by radioraheem on 2009-06-24
Posting this in the beginners forum because I just started using the sensors package a few minutes ago and am still reading up on it.  I just installed sensors because it is a very hot day today and I am concerned about my tower.

This is a dual core AMD 64 chip, and I'm not sure which sensor output from the list below is the main one I should be concerned with.

> acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +75.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +66.0°C                                    
Core1 Temp:  +63.0°C                                    

it8716-isa-0290
Adapter: ISA adapter
VCore:       +1.23 V  (min =  +0.00 V, max =  +4.08 V)   
VDDR:        +3.15 V  (min =  +0.00 V, max =  +4.08 V)   
+3.3V:       +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
+5V:         +4.81 V  (min =  +0.00 V, max =  +6.85 V)   
+12V:       +11.46 V  (min =  +0.00 V, max = +16.32 V)   
in5:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in6:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
5VSB:        +4.60 V  (min =  +0.00 V, max =  +6.85 V)   
VBat:        +2.91 V
fan1:       5973 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
temp1:       +68.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermal diode
temp2:       +43.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = transistor
temp3:       +25.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = transistor
cpu0_vid:   +0.450 V



Any insight is appreciated.

Thank you!

---

### Post by Cesaar on 2009-06-24
You're given 5 different readings for temperature. I am assuming that ones from Core0 and Core1 are the most important because they are listed first at the top and because it seems to be referring to the two CPUs or cores. I don't know what the optimal temperature for these should be. Maybe you should look up some manual online or something for the dual-core AMD 64

---

### Post by wpshooter on 2009-06-24
Depends on what your machine is doing.

The 66 & 63 seem a bit high but then your machine is 64bit and mine is only 32bit and your machine is way above my little rinky dink 478 machine.

But here is what mine looks like, I am only working on this forum.

---

### Post by halitech on 2009-06-24
I've got an AMD 64 5200+ and here are my readings

```
daryl@debian:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +60.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +34.0°C                                    
Core0 Temp:  +31.0°C                                    
Core1 Temp:  +21.0°C                                    
Core1 Temp:  +29.0°C                                    

f71872f-isa-0220
Adapter: ISA adapter
in0:         +3.39 V  (min =  +0.00 V, max =  +4.03 V)   
in1:         +1.38 V  (min =  +0.00 V, max =  +2.02 V)   
in2:         +1.26 V  (min =  +0.00 V, max =  +2.02 V)   
in3:         +0.99 V  (min =  +0.00 V, max =  +2.02 V)   
in5:         +1.10 V  (min =  +0.00 V, max =  +2.02 V)   
in6:         +0.97 V  (min =  +0.00 V, max =  +2.02 V)   
in7:         +0.98 V  (min =  +0.00 V, max =  +2.02 V)   
in9:         +3.31 V  (min =  +0.00 V, max =  +4.03 V)   
in10:        +3.23 V  (min =  +0.00 V, max =  +4.03 V)   
fan1:       3496 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
temp1:       +26.0°C  (high = +117.0°C, hyst = +117.0°C)  sensor = thermal diode
temp2:       +41.0°C  (high = +117.0°C, hyst =  +0.0°C)  sensor = thermal diode
temp3:       +28.0°C  (high = +255.0°C, hyst =  +0.0°C)  sensor = thermal diode

daryl@debian:~$ 

```

mid 60's seems high to me and checking google looks like max temp is between 65-70 depending on the chip

---

### Post by fooman on 2009-06-24
> **radioraheem said:**
> 
This is a dual core AMD 64 chip, and I'm not sure which sensor output from the list below is the main one I should be concerned with.


i would be concerned about:```
Core0 Temp:  +66.0°C                                    
Core1 Temp:  +63.0°C
```and:```
 temp1:       +68.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermal diode
```i believe those are the ones pertaining to your cpu.  i also have an amd64 dual-core and here are my readings:```
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +31.0°C                                    
Core1 Temp:  +34.0°C                                    

abituguru-isa-00e0
Adapter: ISA adapter
CPU Core Voltage:       +1.12 V  (min =  +0.00 V, max =  +1.79 V)
DDR Voltage:            +2.67 V  (min =  +2.10 V, max =  +3.19 V)
DDR VTT Voltage:        +1.34 V  (min =  +1.05 V, max =  +1.55 V)
NB Voltage:             +1.51 V  (min =  +1.25 V, max =  +1.85 V)
SB Voltage:             +2.58 V  (min =  +2.00 V, max =  +3.00 V)
HyperTransport Voltage: +1.21 V  (min =  +0.94 V, max =  +1.45 V)
AGP VDDQ Voltage:       +1.59 V  (min =  +1.25 V, max =  +1.85 V)
ATX +5V:                +5.05 V  (min =  +3.97 V, max =  +5.98 V)
ATX +3.3V:              +3.39 V  (min =  +2.63 V, max =  +3.93 V)
Standby Voltage (+5V):  +5.05 V  (min =  +3.97 V, max =  +5.98 V)
3VDual Voltage:         +3.68 V  (min =  +2.87 V, max =  +4.31 V)
CPU FAN Speed:         2400 RPM  (min = 1200 RPM)
NB FAN Speed:          4380 RPM  (min = 1200 RPM)
SYS FAN Speed:            0 RPM  (min = 1200 RPM)
AUX1 FAN Speed:           0 RPM  (min = 1200 RPM)
AUX2 FAN Speed:           0 RPM  (min = 1200 RPM)
CPU Temperature:        +29.0°C  (high = +75.0°C, crit = +85.0°C)  
SYS Temperature:        +36.0°C  (high = +55.0°C, crit = +65.0°C)  
PWM Temperature:        +39.0°C  (high = +80.0°C, crit = +90.0°C) 
```

as was stated already...60's are pretty high.

---


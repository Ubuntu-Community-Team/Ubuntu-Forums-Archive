---
title: "North Bridge temp using terminal?"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by relay_man on 2009-02-03
Hello to all.
I'm new to Linux/Ubuntu and having much fun learning.  
I've found out how to monitor my CPU temps in terminal using the sensors command, but I can't seem to find how get my North bridge and South bridge temps to display.  I just assembled this computer using an Intel Motherboard (DP43TF) and a Core Duo processor (E4600 2.40 GHz) and I'm concerned about temps until I know how things are going.  I've installed GKrellm and lm-sensors so I can monitor graphically, but I've not been able to make them work yet(still reading/learning). Although I don' know much about it yet, I kind of like the command line.

Below is what displays when I run the sensors command:

mike@mike-desktop:~$ sensors
w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +2.04 V  (min =  +2.04 V, max =  +2.04 V)   ALARM
in1:        +13.46 V  (min = +13.46 V, max = +13.46 V)   ALARM
AVCC:        +4.08 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
3VCC:        +4.08 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
in4:         +2.04 V  (min =  +2.04 V, max =  +2.04 V)   ALARM
in5:         +2.04 V  (min =  +2.04 V, max =  +2.04 V)   ALARM
in6:         +6.53 V  (min =  +6.53 V, max =  +6.53 V)   ALARM
VSB:         +4.08 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
VBAT:        +4.08 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
Case Fan:      0 RPM  (min =    0 RPM, div = 128)  ALARM
CPU Fan:       0 RPM  (min =    0 RPM, div = 128)  ALARM
Aux Fan:       0 RPM  (min =    0 RPM, div = 128)  ALARM
fan4:          0 RPM  (min =    0 RPM, div = 128)  ALARM
Sys Temp:     -1.0°C  (high =  -1.0°C, hyst =  -1.0°C)  ALARM  sensor = diode
CPU Temp:     +0.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = diode
AUX Temp:     +0.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = diode
cpu0_vid:   +0.000 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +36.0°C  (high = +86.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +36.0°C  (high = +86.0°C, crit = +100.0°C)  

mike@mike-desktop:~$ 

Is it possible to display the brige temps here (and maybe fan rpm as well) or should I focus my efforts toward getting Gkrellm working?:confused:

Thanks very much
Mike

---

### Post by LowSky on 2009-02-03
For the most part lm-sensors works fine for most people.

Personally I never understood the point of monitoring tempatures and fan speeds as most systems can now handle power management straight from the BIOS. And with Linux there isn't much gaming to do, so overclocking is kinda a moot thing to do. I understand overclocking for getting the most bang for youe buck, but what is the point of it if you have to monitor your temperatues and voltages like a nuclear reactor.

---

### Post by XCan on 2009-08-08
There are a lot more tasks around that require CPU power other than gaming. Tasks that actually depend more on the CPU than on the graphics card so there is nothing wrong with overclocking. Also, the point with overclocking is of course not to get an unstable system that runs 24/7, the careful monitoring is only meaningful in finding the threshold.

---


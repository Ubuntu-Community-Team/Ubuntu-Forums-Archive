---
title: "LM Sensors Alarms and 127.0 C"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by maciej234 on 2011-02-13
Here is the output of LM sensors:

Adapter: ISA adapter
in0:         +0.85 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
in1:         +3.04 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
in2:         +3.34 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
in3:         +3.02 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
in4:         +2.98 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
in5:         +2.14 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
in6:         +2.14 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
in7:         +2.99 V  (min =  +4.08 V, max =  +3.06 V)   ALARM
Vbat:        +3.15 V
fan1:        811 RPM  (min =    0 RPM)
fan2:        925 RPM  (min =    0 RPM)
temp1:      +127.0°C  (low  =  -1.0°C, high =  -1.0°C)  sensor = thermal diode
temp2:       +22.0°C  (low  =  -1.0°C, high =  -1.0°C)  sensor = thermistor
temp3:       -64.0°C  (low  =  -1.0°C, high =  -1.0°C)  sensor = disabled
cpu0_vid:   +0.000 V


im running ubuntu 10.10 from an external drive on a dell xps studio 8100 desktop.  temp1 looks very high and temp 3 is negative.  in0-in7 have ALARM, what is happening here?

---

### Post by mcduck on 2011-02-13
You probably haven't configured lm-sensors properly.

It's not a tool you can usually just install and expect it to give correct values, it's actually rather "stupid" one that simply reads whatever values your motherboard's sensor chip happens to send. The thing is that values from different sensor chips (and even different motherboards using the same chip) might have to be interpreted in a different way.

Usually you'll have to compare the values lm-sensors gives you with data from some other source (if your BIOS shows sensor data, that would be a good reference) and then adjusting the /etc/sensors.conf file so that the sensors are mapped into correct names and readings are calculated correctly. And of course setting sensible min/max limits is also up to you.

edit: assuming your computer isn't half on fire, half frozen, the temp1 sensor value probably needs to be divided by 2, and temp3 looks like you should just disable it completely. Fan speeds look OK, although depending on what kind of fans you actually have either none or both may need a multiplier. And all voltage, RPM & temperature min/max values are of course ridiculous, if not impossible. But this is mostly just guessing, it's really impossible to say for sure without having any reference values and seeing how the values from lm-sensors change and react to computer usage...

---


---
title: "How do I view temps from lm-sensors?"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by Gotaro on 2009-01-30
Okay..  I installed the lm-sensors package, and did "sensors-detect", but how do I view the temps?  I saw something about a sensors-applet Gnome app, but what about for KDE?

---

### Post by Skripka on 2009-01-30
> **Gotaro said:**
> Okay..  I installed the lm-sensors package, and did "sensors-detect", but how do I view the temps?  I saw something about a sensors-applet Gnome app, but what about for KDE?

After detect-you might need a reboot...might.

...then

Fire up terminal, type:

```

sensors

```If you grab System Profile and Benchmark (I think I remember the name right) off Synaptic or Adept-you can view all that data in a GUI format, that is refreshable short of typing.  You can also set up System Monitor to display graphs and live data fron lm-sensors.

---

### Post by Gotaro on 2009-01-30
> **Skripka said:**
> After detect-you might need a reboot...might.

...then

Fire up terminal, type:

```

sensors

```If you grab System Profile and Benchmark (I think I remember the name right) off Synaptic or Adept-you can view all that data in a GUI format, that is refreshable short of typing.  You can also set up System Monitor to display graphs and live data fron lm-sensors.
Thanks!  I checked sensors, but I wasn't sure what I was looking at..  It's hard to tell what temp is what.  I can't find the System Profile and Benchmark app, though..  Hm..

Searching on the list, I found "KTemperature," but it only shows one temp..  I'm hoping to check GPU and both CPU cores.

---

### Post by Gotaro on 2009-01-30
Okay..  So I am using the "System Monitor - Temperature" widget, and have selected to show all sensors, the lm sensors AND the one it comes with.
temp3: 33
temp2: 23
temp1: 127-128
temp1: 37
temp1: 36
temperature (default): 23

Lol I hope whatever frontend I do get will detect what these sensors ARE (GPU/CPU/something else).

---

### Post by Skripka on 2009-01-30
> **Gotaro said:**
> Okay..  So I am using the "System Monitor - Temperature" widget, and have selected to show all sensors, the lm sensors AND the one it comes with.
temp3: 33
temp2: 23
temp1: 127-128
temp1: 37
temp1: 36
temperature (default): 23

Lol I hope whatever frontend I do get will detect what these sensors ARE (GPU/CPU/something else).
It depends on what motherboard and CPU you are using....figuring out what temps are what is a matter of guessing-really

The App I mentioned is called System Profiler and Benchmark in Adept (search for system profiler, and go to the Settings Tab, and it is right there).

Example: my output from sensors

```

:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +31.0°C
Core1 Temp:  +36.0°C

w83627ehf-isa-0a10
Adapter: ISA adapter
VCore:       +1.34 V  (min =  +0.00 V, max =  +1.74 V)
in1:        +12.14 V  (min = +12.78 V, max = +12.94 V)   ALARM
AVCC:        +3.25 V  (min =  +3.06 V, max =  +2.02 V)   ALARM
3VCC:        +3.25 V  (min =  +3.76 V, max =  +0.46 V)   ALARM
in4:         +1.58 V  (min =  +1.58 V, max =  +1.26 V)   ALARM
in5:         +0.10 V  (min =  +0.38 V, max =  +1.40 V)   ALARM
in6:         +0.31 V  (min =  +1.97 V, max =  +6.32 V)   ALARM
VSB:         +3.25 V  (min =  +2.93 V, max =  +3.06 V)   ALARM
VBAT:        +2.96 V  (min =  +1.65 V, max =  +0.53 V)   ALARM
in9:         +0.10 V  (min =  +2.02 V, max =  +2.01 V)   ALARM
Case Fan:   1548 RPM  (min = 1068 RPM, div = 8)
CPU Fan:       0 RPM  (min =  958 RPM, div = 32)  ALARM
Aux Fan:       0 RPM  (min = 1171 RPM, div = 32)  ALARM
fan4:       1383 RPM  (min =    0 RPM, div = 8)
fan5:          0 RPM  (min = 1028 RPM, div = 32)  ALARM
Sys Temp:    +34.0°C  (high = -95.0°C, hyst =  -1.0°C)  ALARM  sensor = thermistor
CPU Temp:    +35.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
AUX Temp:    +46.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +0.375 V


```

My machine specs are in my sig.

---

### Post by Gotaro on 2009-02-02
I can't figure out where in System Profile and Benchmark it tells me my temps?  In the "Sensors" tab, it only shows one temp, "THRM 24°C".  I think I saw somewhere else where it showed that "THRM" as a virtual device or something..  Definitely 24 is neither of my cores, nor my GPU.  It also shows my CPU at 4.1GHz, when it's actually at 3.0?
My sensors output is:
```
gotaro@gotaro-linux:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +23.0°C  (crit = +65.0°C)

it8718-isa-0a10
Adapter: ISA adapter
in0:         +1.18 V  (min =  +0.00 V, max =  +4.08 V)
in1:         +1.28 V  (min =  +0.00 V, max =  +4.08 V)
in2:         +3.28 V  (min =  +0.00 V, max =  +4.08 V)
in3:         +2.96 V  (min =  +0.00 V, max =  +4.08 V)
in4:         +2.96 V  (min =  +0.00 V, max =  +4.08 V)
in5:         +1.95 V  (min =  +0.00 V, max =  +4.08 V)
in6:         +1.25 V  (min =  +0.00 V, max =  +4.08 V)
in7:         +2.90 V  (min =  +0.00 V, max =  +4.08 V)
in8:         +3.63 V
fan1:       1683 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
temp1:      +128.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = disabled
temp2:       +23.0°C  (low  = +127.0°C, high = +65.0°C)  sensor = thermal diode
temp3:       +34.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermal diode
cpu0_vid:   +2.050 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +37.0°C  (high = +76.0°C, crit = +100.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +37.0°C  (high = +76.0°C, crit = +100.0°C)
```
I don't have names on anything like yours!  Also, I question whether that "disabled" sensor is my GPU, since the GPU fan speed is on high at all times in Ubuntu..

---


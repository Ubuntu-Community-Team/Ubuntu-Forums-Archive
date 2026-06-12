---
title: "CPU Temp"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by CradLeRcker on 2009-04-25
if anyone knows how i can monitor this in ubuntu it would be greatly appreciated if they could say how. thanks.

---

### Post by llamabr on 2009-04-25
```
brock@hops:~$ apt-cache search cpu temperature
athcool - tool to enable powersaving mode for Athlon/Duron processors
collectd - statistics collection and monitoring daemon
computertemp - computer temperature monitor applet for GNOME
cpudyn - CPU dynamic frequency control for processors with scaling
emifreq-applet - CPU Frequency Scaling applet
gdesklets-data - Applets for gdesklets
i8kutils - utilities for Dell Inspiron and Latitude laptops
powersaved - power management daemon
set6x86 - Cyrix/IBM 5x86/6x86 CPU configuration tool
shermans-aquarium - Sherman's aquarium applet for GNOME 2
wmgtemp - Temperature sensor dockapp for Window Maker
wmtemp - WM dock applet displaying lm_sensors temperature values
yacpi - ncurses based acpi monitor for text mode
hot-babe - A GTK-based monitoring app
brock@hops:~$ 

```

---

### Post by steve101101 on 2009-04-25
lm-sensors

---

### Post by lovinglinux on 2009-04-25
Use [lm-sensors](http://www.techthrob.com/2009/03/02/enabling-hardware-sensors-in-linux/)

---

### Post by presence1960 on 2009-04-25
> **CradLeRcker said:**
> if anyone knows how i can monitor this in ubuntu it would be greatly appreciated if they could say how. thanks.

you can install sensors-applet in Synaptic. once installed, right click on top or bottom panel and choose Add to Panel. Choose Hardware Sensors Monitor. Click add. It will appear in the panel where you right clicked. Then right click on it on the panel, choose preferences and set it up. It will appear in your panel every time you use Ubuntu.

---

### Post by lovinglinux on 2009-04-25
> **presence1960 said:**
> you can install sensors-applet in Synaptic. once installed, right click on top or bottom panel and choose Add to Panel. Choose Hardware Sensors Monitor. Click add. It will appear in the panel where you right clicked. Then right click on it on the panel, choose preferences and set it up. It will appear in your panel every time you use Ubuntu.

Yes, but it needs lm-sensors on my machine to display stuff, otherwise it will display only the graphics card temperature.

---

### Post by inobe on 2009-04-25
im gets installed along with sensors applet

---

### Post by lovinglinux on 2009-04-25
> **inobe said:**
> im gets installed along with sensors applet

:oops: 

But it still need [some configuration](http://www.techthrob.com/2009/03/02/enabling-hardware-sensors-in-linux/) to work.

---

### Post by presence1960 on 2009-04-25
> **lovinglinux said:**
> :oops: 

But it still need [some configuration](http://www.techthrob.com/2009/03/02/enabling-hardware-sensors-in-linux/) to work.

i have installed hddtemp as well and have my 2 HDDs, both CPU cores and my GPU temps showing. The configuration took all of 2 minutes.

---

### Post by lovinglinux on 2009-04-25
> **presence1960 said:**
> i have installed hddtemp as well and have my 2 HDDs, both CPU cores and my GPU temps showing. The configuration took all of 2 minutes.

Yep, I guess it depends on the hardware. The configuration is very simple, but it was still needed on my machine.

---

### Post by steve101101 on 2009-04-26
for mine it was able to do it automatically.

---

### Post by presence1960 on 2009-04-26
> **lovinglinux said:**
> Yep, I guess it depends on the hardware. The configuration is very simple, but it was still needed on my machine.

I received some updates last night and now my fan speeds are available too.

---


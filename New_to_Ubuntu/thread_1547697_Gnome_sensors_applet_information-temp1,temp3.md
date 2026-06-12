---
title: "Gnome sensors applet information:-temp1,temp3"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by anand_30 on 2010-08-07
Hello,I am using ubuntu 10.04 64 bit(intel i3 core 2.93 Ghz).

I have installed lm-sensors,sensors applet and hddtemp.I have also added this applet to panel but its showing me something like temp1,temp2,temp3.

I was shocked when i saw temp1 is 94 C and temp3 is 127 C.But temp2 is 37 C.Maybe temp1 and temp3 are showing temperatures of something different,but how come they are sooo high?

```

anand@lotus:~$ sensors
w83627dhg-isa-0a10
Adapter: ISA adapter
Vcore:       +0.90 V  (min =  +0.00 V, max =  +1.74 V)   
in1:         +0.75 V  (min =  +0.32 V, max =  +0.04 V)   ALARM
AVCC:        +3.42 V  (min =  +2.98 V, max =  +3.63 V)   
VCC:         +3.42 V  (min =  +2.98 V, max =  +3.63 V)   
in4:         +1.29 V  (min =  +0.11 V, max =  +0.14 V)   ALARM
in5:         +0.76 V  (min =  +1.98 V, max =  +1.42 V)   ALARM
in6:         +1.05 V  (min =  +1.69 V, max =  +0.72 V)   ALARM
3VSB:        +3.34 V  (min =  +2.98 V, max =  +3.63 V)   
Vbat:        +3.31 V  (min =  +2.70 V, max =  +3.30 V)   ALARM
fan1:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
fan2:          0 RPM  (min = 3515 RPM, div = 128)  ALARM
fan3:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
fan5:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
temp1:       +94.0°C  (high = +102.0°C, hyst = +41.0°C)  sensor = thermistor
temp2:       +37.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
temp3:      +127.0°C  (high = +80.0°C, hyst = +75.0°C)  ALARM  sensor = thermistor
cpu0_vid:   +2.050 V

```

I just want to know what temp1 and temp3 are representing,so as to avoid my confusion.

-anand

---

### Post by diablo75 on 2010-08-07
All I can say is I don't know of any computer hardware component (much less a CPU) that can survive 94 degrees or higher.  In fact, I don't think most modern processors can handle anything above 90, and that all have built in "governors" to throttle clock cycles if things get too hot.  You're CPU is most likely to be temp2.

Does your BIOS have a health check section with CPU temperature listed that you could compare these numbers to?

---

### Post by anand_30 on 2010-08-07
> **diablo75 said:**
> All I can say is I don't know of any computer hardware component (much less a CPU) that can survive 94 degrees or higher.  In fact, I don't think most modern processors can handle anything above 90, and that all have built in "governors" to throttle clock cycles if things get too hot.  You're CPU is most likely to be temp2.

Does your BIOS have a health check section with CPU temperature listed that you could compare these numbers to?

Instead of checking into the BIOS i just checked temperature in windows 7(dual boot) using program called Core temp,and it showed 29C and 32C for core#0 and core#2 respectively.

But still don't know what temp1 and temp3 represents..may be scaling parameters are different for them.

I have attached .png file showing window of Core temp..

Thanks for your help Diablo,:D

---

### Post by NewDisciple on 2010-08-07
On my machine the first applet represents the GPU.  The 2nd and third applets are processor cores.  I have no idea what the other three represent though.

---

### Post by duesergirl on 2010-10-22
My readout is similar.  I'm also running 10.04 64-bit on a Core i3 (mine is the 3.2GHz).  My temp1 is 35C and my temp2 is 36C, and both of those actually fluctuate, which makes me think they are working fine.  But my temp3 is showing as 127C, and it never changes.  Is it possible this is an invalid reading and whatever sensor this is supposed to be is not working?  I can't imagine the computer would still be running (it's been on for a couple of hours now since I installed the sensors and first saw the 127C reading) if something were actually running at that high a temp.

Also, it always shows all the fans running at 0rpm, but I can hear them running and feel the airflow.  Why is it not reading the speed of my fans?

---

### Post by daktari81 on 2010-11-28
I have the same issue with temp3.  it shows 95C on average, yet i'm quite sure with the cooling i have, nothing in my system should be running that hot at all.  this is very puzzling to me.

---


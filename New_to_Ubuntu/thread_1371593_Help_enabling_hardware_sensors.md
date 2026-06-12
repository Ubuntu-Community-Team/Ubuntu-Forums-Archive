---
title: "Help enabling hardware sensors"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by Defiant Rat on 2010-01-03
Hi, Im trying to get my hardware sensors working. After googling, i [*found this guide*]("http://www.techthrob.com/2009/03/02/enabling-hardware-sensors-in-linux/") which i have followed.

However, when i run;
```
sensors
```
I get;
```
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

```
So i run sudo sensors-detect, which gives:
```
#----cut here----
# Chip drivers
it87
# no driver for AMD K10 thermal sensors yet
#----cut here----

```

So, it looks like there is no driver for my processor (AMD Athlon II X4 630) :(

Is there any way to get this working, or is that it, no driver exists?


Thanks a lot for any help, I'd really like to get these working if possible

P.S, Im using Karmic

---

### Post by Paqman on 2010-01-03
Try:
```
sudo sensors-detect
```

---

### Post by Defiant Rat on 2010-01-03
> **Paqman said:**
> Try:
```
sudo sensors-detect
```

Sorry, i should have been more clear, thats what i did. Without sudo it just says you need to be root.

---

### Post by Paqman on 2010-01-03
> **Defiant Rat said:**
> Sorry, i should have been more clear, thats what i did. Without sudo it just says you need to be root.

Ah right. Sounds like there's no support for your hardware in the version of lm-sensors that's in Karmic (and probably not in the Lucid one, either)

[It is supposed to be in the pipeline though.]("http://www.phoronix.com/scan.php?page=news_item&px=NjYwMA")

If you're feeling game you could try downloading and compiling the latest version of lm-sensors direct from the project:

[http://www.lm-sensors.org/wiki/Download](http://www.lm-sensors.org/wiki/Download)

---

### Post by Defiant Rat on 2010-01-03
Thanks for your help, i gave it a go and it was a lot easier than i thought. Best of all i now get a reading from my sensors :D

```
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:     +1.34 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:     +3.36 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:       +4.92 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:     +12.22 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:    3125 RPM  (min =  600 RPM)
CHASSIS FAN Speed:1201 RPM  (min =  600 RPM)
POWER FAN Speed:  1315 RPM  (min =  600 RPM)
CPU Temperature:   +45.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:    +33.0°C  (high = +45.0°C, crit = +75.0°C)  

```

Now all i need to do is get them into conky :)

Cheers.

---

### Post by paparozoumis on 2010-01-03
> **Defiant Rat said:**
> 

Now all i need to do is get them into conky :)

Cheers.

There's also a front end you might want to try.. 
It's called ksensors and it gives you quite a few info on your desktop. 
After you install it with synaptic you can see it's icon at the bar.

---


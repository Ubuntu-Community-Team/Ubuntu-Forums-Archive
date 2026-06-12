---
title: "viewing cpu temperatures on socket a amd cpu"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by TrevorRS on 2009-04-11
im still fairly nrew to ubuntu, i have tried it before however this time i have built up a pc out of old bits i had lying around so its just to learn about ubuntu on.

my question is is there any way i can view cpu temps? as i have it overclocked and would like to keep an eye on temperature over time.

im running the latest version 8.10

Thanks
Trevor

---

### Post by Kosimo on 2009-04-11
You can install Im-sensors

Just follow this guide:


[http://www.bradtrupp.com/ubuntu-cpu-temperature.html](http://www.bradtrupp.com/ubuntu-cpu-temperature.html)


Hope it helps!


And welcome to the Ubuntu universe! :D

---

### Post by Kosimo on 2009-04-11
you don't really have to follow all the steps there

after installing sensors just type

```
sensors
```

inside the terminal and it'll say the current temperature

---

### Post by Kosimo on 2009-04-11
This is my output:

> $ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +46.0°C  (crit = +127.0°C)                  
temp2:       +46.0°C  (crit = +90.0°C) 



It tells you the current temperature of each core and also what it would be the critical temperature limit.

---

### Post by quicknetbook on 2009-04-11
how much overclocking is going on?

---

### Post by Kosimo on 2009-04-11
> **quicknetbook said:**
> how much overclocking is going on?

Not overclocking at all, just default values.

---

### Post by Castor68 on 2009-04-11
[COLOR="Blue"]"Recent comments on our community forum indicate that lm-sensors may not working in the current version 8.04 (April 2008)."[/COLOR]

Anyway, I ran the command and I got this:

****@****-desktop:~$ sudo apt-get install Im-sensors
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package Im-sensors

---

### Post by Castor68 on 2009-04-11
oooopss ...

My mistake.

uppercase, lowercase ... mmm ... I got it. 

I installed and it's working fine.

---

### Post by TrevorRS on 2009-04-12
> **quicknetbook said:**
> how much overclocking is going on?

from 1800 clock to 2150 clock speed at the minute, hopefully more after i find some info i found ages ago about a vcore mod.

motherboard only gives upto 6% more vcore.

thanks to those that have helped, ill try and get it working now.

Trevor

---

### Post by TrevorRS on 2009-04-12
just got it installed and working, 38deg at approx 50% cpu load.... loads of room left for omprovement!

---

### Post by Paqman on 2009-04-12
I like sensors-applet [(click to install)](apt:sensors-applet). It use lm-sensors and sits on a panel. After installing it you might need to run:
```

sudo sensors-detect

```
in the terminal to have it configure itself.

---

### Post by TrevorRS on 2009-04-12
thanks,  im trying it ou tnow.

does anyone know of any programs similar to prime 95 for windows that you can load the cpu on to test max working temp?

---

### Post by Paqman on 2009-04-12
Don't know about GUI apps, but there's a command line one called cpuburn.

---


---
title: "I need help understanding the hardware systems monitor app."
date: 2011-06-07
forum: New to Ubuntu
---

### Post by Arazu on 2011-06-07
I'm talking about the one you can add with the 'add to panel menu'.

It's giving me odd readings.

Temp1
Core0
Core0
Core1
Core1
CPU

First off I have no clue what Temp1 is. More importantly I don't understand why I have 2 readings for each core and then another for CPU. All of which show wildly different readings.

It's a Dell 530S.

I really have no idea what to make of this.

---

### Post by doas777 on 2011-06-07
the reason for the duplicate output, is because your PC has two sets of sensors providing data using that same lable. if you look at the applet properties, you will be able to see which value goes with each sensor bank. I would select the most accurate sensor bank for each value you want to display and uncheck the duplicates.

Temp1 is likely your ACPI temp. what is the value, and how does it change in relation to the cores?

---

### Post by Arazu on 2011-06-07
Thanks for the fast reply.

Temp1 hovers around 12°C regardless of what I'm doing.

How can I determine which is the more accurate of the two readings so I can uncheck the others?

While I'm asking newbie questions why would there be a sensor for each core and then a CPU sensor? Also why would they vary so much? Currently the readings are roughly this:

Temp1 12°
Core0 31°
Core0 24°
Core1 38°
Core1 18°
CPU 12°

I don't know hardware very well but the CPU is a single chip right? So why would each core have a sensor and why would they be so much higher than what the CPU sensor is showing?

---

### Post by doas777 on 2011-06-07
go with the 31/38 deg values. the 12C values are bogus (unless you are in a freezer), and as you said they are reasonably static, meaning they are not particularly relevant.

CPU temp is at the outside of the die, whereas the coretemp is interior.

heres more info:
[http://www.computerforum.com/129794-core2duo-core2quad-temperature-guide.html](http://www.computerforum.com/129794-core2duo-core2quad-temperature-guide.html)

This is NOT simple stuff. gives me a headache. 

sensors are problem on any platform. I've had as much trouble getting sensor readings sorted out on windows as I have on linux.

---

### Post by Arazu on 2011-06-07
I wish you hadn't said that because when I play MineCraft both readings jump to the 60's. =\

The CPU temp does go up. It's 'temp1' that doesn't seem to move more than a few degrees.

Thanks for all of your help. I really appreciate it.

Edit: I just saw your edit. Thanks for the link and extra info.

---


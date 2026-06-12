---
title: "My laptop is using 40W of power at idle!!"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by humphreybc on 2009-10-19
Hi, my laptop is using on average 40W at idle, 38.5W is the lowest it gets. I've installed powertop and applied all the recommended settings, I'm using powersave 800mhz governer, and brightness down to the lowest setting. Also, bluetooth is disabled.

How can I further reduce my power usage, to say, 30W or under? From what i've seen on the internet, 40W is a lot of power for a laptop...

---

### Post by Skwerly on 2009-10-19
What type of laptop is it?  Brand name / model.  :)

---

### Post by humphreybc on 2009-10-19
> **Skwerly said:**
> What type of laptop is it?  Brand name / model.  :)

Specs are in my signature :)

---

### Post by kerry_s on 2009-10-19
i can see that according to the specs, it's 35w, so can you do 30w, i don't think so, cause it's not built for that.
[http://en.wikipedia.org/wiki/CPU_power_dissipation#Intel_Core_2_Duo](http://en.wikipedia.org/wiki/CPU_power_dissipation#Intel_Core_2_Duo)

> Core 2 Duo T7500 	Merom (65 nm) 	2.2 GHz 	35 W 	15.91

---

### Post by mcduck on 2009-10-19
> **kerry_s said:**
> i can see that according to the specs, it's 35w, so can you do 30w, i don't think so, cause it's not built for that.
[http://en.wikipedia.org/wiki/CPU_power_dissipation#Intel_Core_2_Duo](http://en.wikipedia.org/wiki/CPU_power_dissipation#Intel_Core_2_Duo)

That's thermal design power, meaning the max heat output from the CPU, used to design appropriate cooling for it. In other words the CPU uses about 35W under full load, so it definitely doesn't mean that it wouldn't be able to use less when idle or under light load. :)

Anyway, most of the power usage on a laptop will come from other things than the CPU. Graphics cards usually use even more power than the CPU does,  and displays are also quite power hungry.. Dropping the backlight level just a few steps can make a huge difference. Another thing worth considering is the hard drives, if the machine in question has two hard drives that will definitely increase the power consumption.

Enabling or disabling Bluetooth won't make much of a difference since Bluetooth devices hardly use any power when they are not actually transmitting anything.

---

### Post by 3rdalbum on 2009-10-19
If you look in Powertop, you might see the kernel being listed as waking up your CPU. It also lists the specific modules that are waking up the CPU; if you "sudo modprobe -r" those modules, you can get fewer wakeups-per-second.

The modules will reload when you reboot, so you might want to set up a script to remove them whenever you start up, once you've determined that your computer works fine without them.

---

### Post by kerry_s on 2009-10-19
> **mcduck said:**
> That's thermal design power, meaning the max heat output from the CPU, used to design appropriate cooling for it. In other words the CPU uses about 35W under full load, so it definitely doesn't mean that it wouldn't be able to use less when idle or under light load. :)

Anyway, most of the power usage on a laptop will come from other things than the CPU. Graphics cards usually use even more power than the CPU does,  and displays are also quite power hungry.. Dropping the backlight level just a few steps can make a huge difference. Another thing worth considering is the hard drives, if the machine in question has two hard drives that will definitely increase the power consumption.

Enabling or disabling Bluetooth won't make much of a difference since Bluetooth devices hardly use any power when they are not actually transmitting anything.

:lolflag:
i think i copied & pasted from the wrong tab, i was reading several pages on it & wasn't even really paying attention, i had a movie going in the corner & was mostly watching that, just reading during the slow parts. 

my bag, just disregard that post, it's just one of those nights where i'm just so bored.
:lolflag:

---


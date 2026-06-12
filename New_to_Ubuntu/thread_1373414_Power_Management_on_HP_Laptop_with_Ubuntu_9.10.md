---
title: "Power Management on HP Laptop with Ubuntu 9.10"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by Andyproctor on 2010-01-05
Dear All,
Whilst not a brand new user, I only occasionally get the time to look under the hood (away from actually using Ubuntu for work) to configure and optimise my set up. 

Ubuntu 9.10 on an HP Pavillion DV6700 (AMD Turion 64 x2) 3GB RAM

I am trying to improve the meagre 2 hour battery life i get when on battery power. (I did achieve double this with Vista, but Vista is not worth using IMHO)

So after time reading forums (various) and web searches it would seem that the laptop-power-tools are the thing to use. I do have the CPU Freq scaling monitor set to OnDemand. This sets the 2GHz proc to 800MHz for normal use.

My usage is mostly on AC power (say 70% of time) but when I am on battery I want it of course to last as long as possible. 

I conclude that I should use the spin down & lcd dim properties of the laptop-mode-tools but I cannot get the mode to enable on its own..have tried setting the acpi-support file entry to TRUE for enable_laptop_mode and reboot performed and so on. 

Manually starting the service by 
"sudo /etc/init.d/laptop-mode start"
gets the service started and I would guess that I can then configure by the laptop-mode for modules & options. 

However applying ac power does not disable the service and thus I need to disable or enable the service manually each time i need to use it. (cannot get it automated)

It is valid therefore to configure the laptop-mode-tools for how the system reacts on battery power and then write a script that i can execute manually (checking for status with cat /var/proc/sys/vm/laptop_mode = 0 or non-0) for ac or battery (depending on my use) to switch the tools on or off?

It may seem a dumb question, but this is the absolute beginner forum :-)

Many thanks in advance

Andy

---

### Post by Andyproctor on 2010-01-06
I did of course mean "checking for status with cat /proc/sys/vm/laptop_mode = 0 or non-0)".
Any thoughts please?

---

### Post by Andyproctor on 2010-01-07
Forum admin please delete this post as I will ask in correct forum now I've found it, thanks :)

---


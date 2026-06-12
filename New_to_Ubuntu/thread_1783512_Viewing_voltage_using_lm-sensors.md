---
title: "Viewing voltage using lm-sensors"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by kjjj11223344 on 2011-06-15
I just successfully installed lm-sensors. How do I view cpu voltages now?

---

### Post by 67GTA on 2011-06-15
You need to set lm-sensors up first by running ```
sudo sensors-detect
``` in a terminal, and just accept the default answers. The last will add any needed modules to a config file to be loaded at boot time. After rebooting, you can run ```
sensors
``` in a terminal to see all relevant info. Depending on your rig/hardware, you may or may not see your CPU voltage. If you just want to see what speed your CPU is running at you can run ```
sudo cat /proc/cpuinfo
``` and look for "cpu MHz".

---

### Post by tgalati4 on 2011-06-15
If you are trying to undervolt then you need a few things:

[https://wiki.archlinux.org/index.php/PHC](https://wiki.archlinux.org/index.php/PHC)

[http://www.linux-phc.org/](http://www.linux-phc.org/)

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

You need to create a correct build environment on your machine.  You need to recompile your kernel with "Activate P-States Voltage Control"

You can then view and change your CPU voltages.

If you know what you are doing, you can create a working build environment in about an hour and it took me 2 hours to compile the Jaunty kernel on my Thinkpad T43p.

Now I can undervolt and see the voltages.  Sensors will give you the motherboard voltages, but the the actual voltages that the CPU is running at.

---


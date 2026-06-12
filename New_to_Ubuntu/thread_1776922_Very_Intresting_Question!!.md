---
title: "Very Intresting Question?!!?"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by Smooth Operator on 2011-06-07
Now something that i noticed when i first used the Linux OS (UBUNTU) was how i did not have to install any drivers at all.. unlike windows every time you start from scratch you have to provide the drivers in order for them to work etc etc.. Now my question is how is or how are the Linux Operating Systems able to detect the drivers automatically and Windows is not?......:confused:

---

### Post by JustinR on 2011-06-07
Both operating systems, Windows + Linux, both have kernels that load drivers - but the difference is that in Linux a lot more drivers are included by default unlike Windows.

Also, most drivers included in the Linux kernel are very generic, eg. one size fits all - while Windows includes very specific drivers for hardware.

---

### Post by doas777 on 2011-06-07
well, each device has plug-n-play hardware, so the device advertises to the system what it is. each device is assigned a global [Device Identification String]("http://www.osronline.com/ddkx/install/idstrings_8tt3.htm"), so the kernel can identify the correct driver and load the associated modules. 

both the windows and linux kernels have driver repositories built in, and they are loaded if no other driver is specified for that device. in the windows world, the device vendors usually provide more hardware-specific driver modules, that are more up-to-date, so its a good idea to download and use them. for linux, most vendors don't have a linux driver, or installing and maintaining proprietary drivers is too much of a pain, so most users don't bother unless a piece of hardware will not work with the bundled drivers.

---


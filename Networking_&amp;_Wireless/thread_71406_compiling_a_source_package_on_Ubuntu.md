---
title: "compiling a source package on Ubuntu"
date: 2005-10-03
forum: Networking &amp; Wireless
---

### Post by kaybel on 2005-10-03
Hello all,
i have a Usb wireless adapter with a zydas(zd1211) chipset. it's working well on my windows xp because the drivers it can with are meant for windows. i however found linux drivers for it at sourceforge.net/project/zd1211, but it is a source package. can any one please tell me how to compile and install this package on my Ubuntu. i'm using Hoary5.04. Besides i understand you must have the compiled source of your kernel before you can compiles this linux driver. does the Ubuntu installation leave its source kernel behind just incase one wants to compile a source package in future. You detailed help will really be appreciated in all the questions. thank you.

---

### Post by s_p_a_r_k_y on 2005-10-03
do this,
```
 uname -a 
```
Mine says 2.6.10-5-686
Now look in synaptic for the kernel headers and source file which match that number.

Install those two packages. Then from the kernel module's directory you will probably type in make, then make install and it'll install the kernel module

---


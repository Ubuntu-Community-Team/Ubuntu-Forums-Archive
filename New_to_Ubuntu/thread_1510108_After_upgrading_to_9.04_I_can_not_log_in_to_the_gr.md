---
title: "After upgrading to 9.04 I can not log in to the graphical user interface anymore."
date: 2010-06-15
forum: New to Ubuntu
---

### Post by lamle on 2010-06-15
Hi,
I am using Ubuntu 8.04 and I did updated it to Ubuntu 9.04 but because  it is an unstable version, after upgrading I can not log in to the  graphical user interface anymore. 
Thinking that it has something to do with my graphic driver (is it  xorg?), I removed xserver-xorg-core and installed it again but it cries  about 1 dependency not found: 
dependency xserver-xorg-input-4 but it is not installale. 
This xserver-xorg-input-4 is a virtual package and I cannot install it  either. It contains xserver-xorg-input-synaptics,  xserver-xorg-input-wacom and 2 others but i dont remember. 
 
Please give me an advice how I can recover my graphic driver? I use ATI card 
Thank you for your help and have a nice day  :-)  
BR,Lam

---

### Post by philinux on 2010-06-15
Moved to ABT forum and own thread.

---

### Post by Peter09 on 2010-06-15
Get into recovery mode and select the configure graphics option in the menu.

---

### Post by Mark Phelps on 2010-06-15
> **lamle said:**
> ... Please give me an advice how I can recover my graphic driver? I use ATI card ...

My guess, is that since you have an ATI card, you were running the proprietary (fglrx) drivers in 8.04 to get decent frame rates.

Unless you have one of the newer HD 3x/4x/5x cards, those driver will not only FAIL in Ubuntu 10.04, there are also no fglrx drivers that will work anymore.

IF you read the link below, it has instructions on how to remove the fglrx drivers:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

Once you do that, when you reboot, Ubuntu should re-detect your video card and automatically install the proper open source drivers.

---


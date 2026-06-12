---
title: "Asus graphics driver"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by PHINCY L PIOUS on 2010-10-05
hi friends one of my friend is having  acomputer with asus board. he got a cd for drivers it includes linux drivers too. but we dont know how to install it in ubuntu 10.04 . it is a .run file to be executed . But it shows one more library file is required to instal the driver and it can be located on the disk itself .is there any method to make this form the cd rather executing the individual file???//?

---

### Post by emoguitarist06 on 2010-10-05
Well if it's just two files one not just install the two files?

for .run cd into the directory and run ./filename.run

---

### Post by Mark Phelps on 2010-10-05
Linux is NOT Windows!!  Don't go hacking around forcing the arbitrary installation of drivers.

If you have some hardware that is NOT working, then it's worth doing some investigation to see if there ARE better drivers for it.

But in Ubuntu, unlike in MS Windows, you don't stick in a driver CD and install stuff.

---

### Post by coffeecat on 2010-10-05
For the motherboard controllers you don't need to install anything. Relevant drivers will already be installed in a default system. If it's for the graphics card (that's what your thread title says) it may be unnecessary to install anything from the motherboard CD.

If you are using Ubuntu, the appropriate open source driver will already be installed and will be activated when you boot up. If the graphics card is ATI or nvidia, you can install the proprietary driver if you so wish, but the easiest way is to go to System > Adminstration > Hardware Drivers and install it from there. But you need an internet connection to be able to do this.

What graphics chipset is it?

---


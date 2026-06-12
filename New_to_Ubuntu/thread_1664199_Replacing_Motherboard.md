---
title: "Replacing Motherboard"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by daniell59 on 2011-01-10
If it becomes necessary for me to replace the motherboard in my PC, is it necessary to re-install Ubuntu?
Please forgive me if this is an inane question.

Thanks

---

### Post by endotherm on 2011-01-10
yes with a but, no with an if...

if your hardware is very simmilar to your old hardware then it may work. 
during install, an OS interrogates teh hardware to determine what is there, and installs the low level drivers to make everything function. many of these drivers are very generic, and will work for many systems, but some have specific configurations that are not portable. 

so, if you install a much newer mobo, yes you will almost certianly have to reinstall. 
personally I would recommend you reinstall just to make sure that nothing is only half working on your new platform.

---

### Post by A_M_S on 2011-01-10
Unless the board is equal i think its a good idea to reinstall Ubuntu. 
You may have problems even with similar boards.

---

### Post by coffeecat on 2011-01-10
> **daniell59 said:**
> If it becomes necessary for me to replace the motherboard in my PC, is it necessary to re-install Ubuntu?

No. Definitely not.

Linux systems probe for hardware on bootup and load appropriate drivers as needed. If you move the installed hard drive to a completely different set of hardware it will work - so long as the hardware is supported.

The one big exception is if you have proprietary video drivers installed. If you have the proprietary nvidia driver installed, for example, and then replace the nvidia card with an ATI one, the system will boot up but the xserver will crash. Ditto if you have the proprietary fglrx driver for ATI installed and try to boot up with a nvidia card. Uninstall the proprietary driver first and you'll be OK because the open-source video drivers are part of a default install and will be loaded as needed.

The other thing to watch for is 32/64 architecture. If you've installed a 64-bit system on a 64-bit motherboard/CPU and try to boot up from the HD on a 32-bit motherboard/CPU it will, of course, fail.

---

### Post by CharlesA on 2011-01-10
You can try to swap it and it'll probably work.

I swapped a Linux install to a completely different machine and the only thing I had to fuss with was the network card not being defined as "eth0" (it was definied as eth1)

---

### Post by coffeecat on 2011-01-10
> **CharlesA said:**
> I swapped a Linux install to a completely different machine and the only thing I had to fuss with was the network card not being defined as "eth0" (it was definied as eth1)

Admittedly on a live USB with persistence, I managed to get ethX up to about eth4 by booting up with it on a number of different machines. :)

I'm sure you know this already, but for the record you can edit /etc/udev/rules.d/70-persistent-net.rules to change eth1 back to eth0 if you want.

---

### Post by CharlesA on 2011-01-10
> **coffeecat said:**
> Admittedly on a live USB with persistence, I managed to get ethX up to about eth4 by booting up with it on a number of different machines. :)

I'm sure you know this already, but for the record you can edit /etc/udev/rules.d/70-persistent-net.rules to change eth1 back to eth0 if you want.
I've seen that around, yep. It's a good thing to know about. :)

---


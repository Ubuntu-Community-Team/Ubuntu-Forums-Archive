---
title: "Virtual Machine trouble"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by mclovin91 on 2009-03-12
I got Sun xVM VirtualBox so i could run windows on a virtual machine and when i finished making a machine it said

FATAL: No bootable medium found! System halted.

Anyone else gotten this before and knows how to fix it?

---

### Post by sandyd on 2009-03-12
have you set your boot sequence correctly?
 
should be (Hard drive, CD/DVD, floppy, network)
 
most likely you haven't. The same thing hapenned to me and it took me 10 minutes to figure out what was wrong........

---

### Post by BDNiner on 2009-03-12
Yes After installing the OS you should change the boot order. Same thing also happened to me.

---

### Post by mclovin91 on 2009-03-12
still getting the error after changing boot order. Now what should I try?

---

### Post by BDNiner on 2009-03-12
Is the error occuring in the VM machine? As in it looks like a windows boot up error message?

---

### Post by mclovin91 on 2009-03-12
yes at boot up it goes to that after showing the Sun Virtual box logo

---

### Post by BDNiner on 2009-03-12
So at this point have you install windows? or have you just installed Virtual Box and are trying to install windows from a CD?

---

### Post by KayakJim on 2009-03-12
It sounds like you haven't installed Windows yet so it just hangs because it has nothing to boot from.

Do you have:

1. the Windows CD in the CD-Rom drive?
2. have the CD-Rom drive enabled for the virtual machine?
3. have the boot order set to Hard drive first and then CD-Rom second?

When you start the virtual machine image you should see a prompt that says "press any key to boot from cd" at which time you need to hit the space bar otherwise it will stop.

---

### Post by mclovin91 on 2009-03-12
didn't have CD enabled, now it works. Thank you all for the help!!

---

### Post by KayakJim on 2009-03-12
If you are going to do this often, rip the Windows CD to an .iso on your system. Then in the CD-Rom settings, set it for a local image and select the .iso file. The install goes *much* faster. ;)

---

### Post by WatchingThePain on 2009-03-12
Mount the iso for the boot disc. It will be in options somewhere.

---


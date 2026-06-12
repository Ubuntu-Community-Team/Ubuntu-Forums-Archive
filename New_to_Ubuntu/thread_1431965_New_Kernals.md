---
title: "New Kernals ?"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by Frogs Hair on 2010-03-17
Can someone please suggest a help link for dealing with new kernels , the  last update 
the new kernel did not work, but I could use an older one to log in . This time I have a black screen and I am facing a complete re-install . All my help links are in Ubuntu, which I can't boot . Thanks !!

---

### Post by caravel on 2010-03-17
If a kernel update produces a black screen, proprietary display drivers are the likely culprit.

Do you have either of the ATI or Nvidia proprietary drivers installed?

---

### Post by spyrule on 2010-03-17
I've had this problem before too, it's definitely video drivers. What are the specs of your computer, and what video card are you using?

---

### Post by Frogs Hair on 2010-03-17
Thanks for your time
 
System: Asus M4N78 pro mobo  Athlon x II  2.8 ghz CPU Mem. 2ghz 1066 DDR2 Gforce 8400 GS 512 mb  WD caviar blus 500 gb hdd  Ultra 750 PSU Pioneer DVG/DVR
Sony monitor.
 
Using the 185 Nvidia driver provided with Ubuntu

---

### Post by caravel on 2010-03-17
> **Frogs Hair said:**
> Thanks for your time
 
System: Asus M4N78 pro mobo  Athlon x II  2.8 ghz CPU Mem. 2ghz 1066 DDR2 Gforce 8400 GS 512 mb  WD caviar blus 500 gb hdd  Ultra 750 PSU Pioneer DVG/DVR
Sony monitor.
 
Using the 185 Nvidia driver provided with Ubuntu

If you can boot in from the previous kernel.  Just go to the Ububntu "hardware drivers" applet, disable the Nvidia proprietary driver and reboot from the new kernel.

Unless you're gaming or you can't live without compiz-fusion, do without the proprietary drivers altogether or you'll likely go through this everytime the kernel or xorg gets updated.

---

### Post by spyrule on 2010-03-17
See if the post helps you at all:

[http://ubuntuforums.org/showthread.php?t=1329932&page=2#15](http://ubuntuforums.org/showthread.php?t=1329932&page=2#15)

---

### Post by coffeecat on 2010-03-17
> **Frogs Hair said:**
>  Gforce 8400 GS 

.....
 
Using the 185 Nvidia driver provided with Ubuntu

I'm posting from Karmic with the latest (2.6.31-20) kernel freshly installed and rebooted, using a nvidia GeForce 8400GS card with the 185 Nvidia driver installed using Hardware Drivers.

So... the same as you, except that everything is working fine.

Which leads me to suspect you are not running the same kernel. What kernel number is the one giving problems and have you enabled the Proposed repository? If you have enabled the Proposed Repository, disable it now.

Proposed packages may break your system. They are intended only for experienced users for testing purposes.

---

### Post by ConDsenXieN on 2010-03-17
If you can get back in at some point and find that the proposed kernel update is breaking it, you can use Synaptic Package Manager to completely remove the buggy kernel(which in turn, updates your GRUB to reflect the changes).

---

### Post by spyrule on 2010-03-17
> **coffeecat said:**
> ... If you have enabled the Proposed Repository, disable it now.

Proposed packages may break your system. They are intended only for experienced users for testing purposes.

You could use this same logic to justify removing Linux from your system and installing Windows ;)

---

### Post by Frogs Hair on 2010-03-17
> **coffeecat said:**
> I'm posting from Karmic with the latest (2.6.31-20) kernel freshly installed and rebooted, using a nvidia GeForce 8400GS card with the 185 Nvidia driver installed using Hardware Drivers.

So... the same as you, except that everything is working fine.

Which leads me to suspect you are not running the same kernel. What kernel number is the one giving problems and have you enabled the Proposed repository? If you have enabled the Proposed Repository, disable it now.

Proposed packages may break your system. They are intended only for experienced users for testing purposes.

The 2.6.31-20 Kernel is the one that came with updates today . I will disable the driver
as Caravel suggested since I was able to get into grub and boot with the -19 kernel.

---

### Post by Frogs Hair on 2010-03-17
Solved !! Thanks for all your suggestions !! and excuse my spelling

This is what I did.

1. removed Nvidia 185 driver 

2. installed new  kernel 

3. rebooted Ubuntu using new kernel

4. installed Nvidiia 1.85 driver

5. rebooted 

6. enjoyed having the problem solved!! :)

---

### Post by ConDsenXieN on 2010-03-17
There you go. :p

Good to hear everything is well. I should keep this in mind for when I have to do an update on my desktop.

---


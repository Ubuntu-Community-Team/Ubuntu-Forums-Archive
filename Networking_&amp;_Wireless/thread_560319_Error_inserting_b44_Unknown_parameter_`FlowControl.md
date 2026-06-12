---
title: "Error inserting b44: Unknown parameter `FlowControl'"
date: 2007-09-26
forum: Networking &amp; Wireless
---

### Post by jabby on 2007-09-26
# modprobe b44
FATAL: Error inserting b44 (/lib/modules/2.6.20-16-386/kernel/drivers/net/b44.ko): Unknown symbol in module, or unknown parameter (see dmesg)
# dmesg | tail -1
b44: Unknown parameter `FlowControl'
# lspci | grep -i eth
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)


This started with the last kernel upgrade (before the one I did yesterday).  Before that, it was working fine.  Now, my ethernet doesn't work (built-in on my Dell Inspiron 1150).

I have been googling this for a while now and haven't seen anyone else with the same problem.  I don't see anything relevant on these forums or on launchpad yet, either.  Anyone else run into this problem?  If so, how do I resolve it or work around it?

Thanks,
J

---

### Post by noob12 on 2007-09-26
What this means is that  the b44 driver module is being loaded with an option "FlowControl" which the current version of the driver does not understand.  

This could be due to having previously set this option on a different version (either newer or older) that was replaced when you  recently updated.

If you set this up yourself, this option is probably going to be in your **/etc/modules** or **/etc/modprobe.d/options** file.

If you find it in /etc/modules, remove the option but leave the **b44**.  If you find it in **/etc/modprobe.d/options**, remove the option and if only **options b44** is left on that line you can  remove the entire line.  (ADDED:  In the current b44 module, the only option that is supported is the b44_debug parameter, so almost certainly you will want to remove the options line if you have one in /etc/modprobe.d/options.)

If you find and remove the option but still have the problem, you may need to rebuild your initrd.
Let's see if any of that helps first.

---

### Post by jabby on 2007-09-26
That was totally the problem.  I don't remember why I put that in there, but I had the following line in /etc/modprobe.d/options:

options b44 FlowControl=0,0

Commenting it out allowed the module to be inserted.

Thanks!
J

---


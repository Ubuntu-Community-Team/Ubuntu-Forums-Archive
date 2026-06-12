---
title: "Network connection problem."
date: 2009-05-10
forum: New to Ubuntu
---

### Post by SG3 on 2009-05-10
Hi,

   I'm using ubuntu 8.10 and windows vista on the same machine, i notice that after a reboot and moving from the win to ubuntu there is no network connection, no matter what i did the connection is back on after shuting down and selecting the ubuntu.Can any1 direct me to a faster way of getting my connection runing : )

---

### Post by wizard10000 on 2009-05-10
This isn't gonna help much but reboots don't reinitialize hardware.  The only way to really cold boot your machine is to unplug it from the wall and let it sit for ten seconds before plugging it back in.

The NIC driver in Ubuntu isn't reinitializing the device - not sure there's a lot you can do about that.

---

### Post by SG3 on 2009-05-10
well i figured something like that : ) 
ty for the opinion

---

### Post by wizard10000 on 2009-05-10
> **SG3 said:**
> well i figured something like that : ) 
ty for the opinion

Yeah, I had that problem once before with a dual-boot Windows and Linux system - never did solve it.  The Windows machine reinitialized the NIC just fine but the Linux box just wouldn't.

The cheapest solution is to just cold-boot the machine when switching between OS - one that's almost as cheap if you've got a spare PCI slot and a spare port on your switch is install a second NIC and use one for Windows and one for Linux  ;)

IMO the best solution?  Get a cheap second PC and a KVM switch so you can use the same mouse and keyboard on both machines.

---

### Post by HereInOz on 2009-05-10
If your machine has decent performance, you can install Virtual Box on the Ubuntu installation, and run Windows in a virtual machine in Ubuntu.  

This removes the need for dual booting, but if you are using the Vista machine for gaming and things like that, you will be disappointed with the video performance.  Otherwise this is a good solution.

Doesn't solve your problem though - just gets around it.

---

### Post by SG3 on 2009-05-10
hey thanks for the ideas : ) will try with a 2nd nic

got already 1 installed : )

---


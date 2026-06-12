---
title: "Black screen during booting of computer"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by soft-e on 2010-02-12
Hello,
 
I've erased the existing windows XP and installed Ubuntu on my Dell 2350.  When I restart my system, I do not see any problems but when I shutdown and then turn  on my desktop, I just get a black screen. So I was forced to reinstall ubuntu and now I once again have ubuntu on my desktop and I haven't shut the desktop down because I'm afraid that it won't reboot again. I've searched this forum and I found that there are mentions of running this command:
sudo nano /etc/X11/xorg.conf
But on my computer, I don't find this file under /etc/X11. Another solution is to force the computer to use the "vesa" driver. How do I do that?
I also see suggestions to run this command:
sudo dpkg-reconfigure xserver-xorg
 
Please tell me how to fix this problem. Is there way to turn off any special graphics. I'm really not interested in any graphics at the moment on this desktop. I'm new to Linux but worked on other Unix flavors.
 
Thank you soft-e

---

### Post by NightwishFan on 2010-02-12
If you use using Ubuntu 9.10, then the Xorg.conf file does not exist by default. Perhaps there is nothing wrong, but it would help if you posted your graphics hardware. You can open a terminal and type this to find it:
```
sudo lshw -C display
```

---

### Post by soft-e on 2010-02-12
Hi NightwishFan,

Thanks for responding. Here are the details after running the command sudo lshw -C display

*-display               
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:e0000000-e7ffffff(prefetchable) memory:ee000000-ee07ffff


Thanks
soft-e

---

### Post by lavinog on 2010-02-12
After you installed the first time, did you apply updates?

Did you try rebooting again after it failed?

---

### Post by soft-e on 2010-02-12
Yes, I applied the updates and rebooted the machine.

---

### Post by Rex Bouwense on 2010-02-12
To answer your question, yes you can turn off the visual graphics.  It is under System->Appearance->Visual Effects.  Just click on None.

---

### Post by soft-e on 2010-02-12
Visual effects is set to "None" by default.

---

### Post by garvinrick4 on 2010-02-12
Do you have more than 1 video card installed?

---


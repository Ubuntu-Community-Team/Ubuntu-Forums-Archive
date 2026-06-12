---
title: "Resolution and Unknown Monitor Issue on Laptop"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by garl on 2011-07-09
I installed Ubuntu 11.04 on my Toshiba Satellite L550-00P laptop and everything was working fine for a day. I turned it on today, and the sides of the screen were black. I adjusted the resolution back to 1600x900 but I noticed it's also detecting an "unknown monitor," which wasn't there before. Now whenever I restart, it changes to the wrong resolution (1024x768). I'm still new to Linux, so I'd appreciate if someone can help and explain in detail what to do.

laura@Satellite:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
laura@Satellite:~$ sudo lshw -C video
[sudo] password for laura: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:f2800000-f2bfffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f2100000-f21fffff

---

### Post by wildmanne39 on 2011-07-09
Hi, you can have a look at this link I think it can help you.
[https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf%20--%20resolution%20lower%20than%20expected](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf%20--%20resolution%20lower%20than%20expected)
This might be a better link to look at.
[http://grenage.com/xorg.html](http://grenage.com/xorg.html)

---


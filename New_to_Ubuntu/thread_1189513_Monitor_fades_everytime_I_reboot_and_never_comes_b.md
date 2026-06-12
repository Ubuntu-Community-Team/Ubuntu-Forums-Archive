---
title: "Monitor fades everytime I reboot and never comes back"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by AkaChan83 on 2009-06-16
I had this same problem on my laptop when I installed Hardy but I just figured my video card had finally died (it was an older laptop). However, I just installed jaunty and i'm having the same problem on my desktop. Help! :(

---

### Post by AkaChan83 on 2009-06-16
here's the output from lshw -C video:

*-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: 82915G/GV/910GL Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82915G Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

---


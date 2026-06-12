---
title: "vaio video drivers and 8.10"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by boeding on 2008-12-12
Hello all,
I have recently upgraded to ubuntu 8.10. In the older versions I could never adjust my screen brightness. Now in 8.10 the fn + f5 and f6 keystrokes work and it brings up the window and it changes the level there but the actual display brightness doesn't work. I think that this is caused due to video drivers incompatibility or not being updated. I was wondering how to update the drivers and\or other ways of fixing the problem.

any help would be great

---

### Post by Michael.Godawski on 2008-12-13
hi boeding, 
would be good to know what graphic card you have.
Please run this in terminal and post the output here:
```
sudo lshw -C display
```

---

### Post by boeding on 2008-12-15
*-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

---


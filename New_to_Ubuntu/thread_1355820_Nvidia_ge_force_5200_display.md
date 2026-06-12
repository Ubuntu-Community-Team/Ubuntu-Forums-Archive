---
title: "Nvidia ge force 5200 display"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by ibbill on 2009-12-15
Have installed the recommended drive 173 and its activated. When I set my resolution to 1024 x 768 and reboot it goes back to 1400x1050 and its reset to auto again in the nvidia display configuration.

When I click on display I get the following message.

It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendors tool instead. I click yes and set it at 1024x768 when I reboot its back to the 1400x1050 again.Attaching the specs of the card. 

Thanks Bill

---

### Post by ibbill on 2009-12-15
> **ibbill said:**
> Have installed the recommended drive 173 and its activated. When I set my resolution to 1024 x 768 and reboot it goes back to 1400x1050 and its reset to auto again in the nvidia display configuration.

When I click on display I get the following message.

It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendors tool instead. I click yes and set it at 1024x768 when I reboot its back to the 1400x1050 again.Attaching the specs of the card. 

Thanks Bill

oops won let me upload the attachment

ill@bill-desktop:~$ sudo lshw -C display
[sudo] password for bill: 
  *-display UNCLAIMED     
       description: Display controller
       product: 82915G/GV/910GL Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: memory:dff80000-dfffffff ioport:ecd8(size=8) memory:b0000000-bfffffff(prefetchable) memory:dff40000-dff7ffff
  *-display
       description: VGA compatible controller
       product: NV34 [GeForce FX 5200]
       vendor: nVidia Corporation
       physical id: 1
       bus info: pci@0000:03:01.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
       resources: irq:17 memory:de000000-deffffff memory:c0000000-cfffffff(prefetchable) memory:df000000-df01ffff(prefetchable)
bill@bill-desktop:~$

---


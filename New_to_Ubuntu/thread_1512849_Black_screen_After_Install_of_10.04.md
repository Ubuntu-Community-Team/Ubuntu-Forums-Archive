---
title: "Black screen After Install of 10.04"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by Foxfire on 2010-06-18
I did a fresh install of ubuntu 10.04 and when i try to log in the screen goes black and nothing happens. any ideas on how to fix this?

---

### Post by nhasian on 2010-06-18
when your at your blank screen can you press Control-Alt-F1 to get to a terminal?  please give us the output of the following terminal command:

```
lshw -C display
```

---

### Post by pk3 on 2010-06-18
> **nhasian said:**
> when your at your blank screen can you press Control-Alt-F1 to get to a terminal?  please give us the output of the following terminal command:

```
lshw -C display
```
not hijacking the thread here, but I have the same problem. ctrl + alt + f1 doesn't work on the blank screen. terminal command:
PCI (sysfs)  
  *-display               
       description: VGA compatible controller
       product: C61 [GeForce 6150SE nForce 430]
       vendor: nVidia Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:21 memory:fb000000-fbffffff memory:e0000000-efffffff(prefetchable) memory:fc000000-fcffffff memory:80000000-8001ffff(prefetchable

---


---
title: "display UNCLAIMED: no driver?"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by mathfreak123 on 2009-11-15
Hey, I looked at my lshw output one day to see this:

```
        *-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:32 memory:f0000000-f00fffff memory:d0000000-dfffffff(prefetchable) ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f0100000-f01fffff
```

The display:1 UNCLAIMED bothered me a bit, and some Googling tells me that it means I don't have a driver for display:1. I'm still not sure what this means, since I have a display:0 that doesn't say UNCLAIMED.

Can someone please explain what this means to me? Should I worry about this at all?

I'm running Ubuntu 9.10 on a Toshiba Satellite M305-S4822.

---

### Post by fancypiper on 2009-11-15
That means you only have one display device connected, so unless you have two connected, just ignore it.

---

### Post by v1nsai on 2009-12-21
Actually, if you look under description you will see that one is VGA and the other is the display adapter.  The VGA adapter is the port used to hook up an external monitor to your laptop, so the display driver doesn't have a module loaded for it.

I've got intel graphics in my Dell too, and apparently the intel drivers have been a mess since jaunty, I can't get either of mine to be 'claimed' so I think we just kind of have to wait.

---


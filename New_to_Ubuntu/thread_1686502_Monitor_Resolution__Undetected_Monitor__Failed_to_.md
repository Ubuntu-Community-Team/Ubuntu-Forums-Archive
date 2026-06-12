---
title: "Monitor Resolution / Undetected Monitor / Failed to get size of gamma"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by tdog32 on 2011-02-12
My monitor resolution is at 1600x1200, and I don't know how to change it. The monitor preferences show that my monitor is unknown. When I type "xrandr" I get the response that it "failed to get size of gamma for output."

I'm using a Dell Dimension 2400. I'm thinking of getting another monitor and seeing if that will do the trick.

I think re-writing the xorg.config file will do the trick, but I'm not getting any traction on how to do that. Any recommendations out there on next steps?

---

### Post by cariboo on 2011-02-12
It would help if you told us what graphics adapter you are using.

---

### Post by tdog32 on 2011-02-12
p { margin-bottom: 0.08in; }a:link {  }  Thank you for the quick response. I think the below is the information on the graphics adapter, right?





FROM lspci

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

FROM lshw

*-display
description: VGA compatible controller
product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
vendor: Intel Corporation
physical id: 2
bus info: [COLOR=#3465a4]pci@0000:00:02.0[/COLOR]
version: 01
width: 32 bits
clock: 33MHz
capabilities: vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:16 memory:e8000000-efffffff memory:feb80000-febfffff

---


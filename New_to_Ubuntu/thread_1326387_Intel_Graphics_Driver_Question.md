---
title: "Intel Graphics Driver Question"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by georgepag on 2009-11-14
I have an HP Pavillion DV6 with the following Intel graphics chip set, running Ubuntu 9.1  Sometimes, the graphics are a little choppy during video or when, say playing a game that has movement,  for example  a tetris-type game. From reading other posts I understand that the Intel graphics drivers are included in Ubuntu so there is really nothing to upgrade.  Is that a true statement?  If not what should I be looking for?  It it is true, are there system adjustments I should try?

George


id:display:0
                description: VGA compatible controller              product: Mobile 4 Series Chipset Integrated Graphics Controller              vendor: Intel Corporation              physical id: 2
              bus info: pci@0000:00:02.0
              version: 07              width: 64 bits              clock: 33MHz              capabilities: msi pm bus_master cap_list rom               configuration: driver=i915 latency=0              resources: irq:31 memory:d0000000-d03fffff memory:c0000000-cfffffff(prefetchable) ioport:7110(size=8)                                                          

id:display:1
                description: Display controller              product: Mobile 4 Series Chipset Integrated Graphics Controller              vendor: Intel Corporation              physical id: 2.1
              bus info: pci@0000:00:02.1
              version: 07              width: 64 bits              clock: 33MHz              capabilities: pm bus_master cap_list               configuration: latency=0
resources: memory:d5400000-d54fffff

---

### Post by Romanrp on 2009-11-14
nevermind

---

### Post by MyR on 2009-11-14
;]

---

### Post by Paqman on 2009-11-14
> **georgepag said:**
> From reading other posts I understand that the Intel graphics drivers are included in Ubuntu so there is really nothing to upgrade.  Is that a true statement?

Indeed it is. An upgrades will be included in kernel updates.

---


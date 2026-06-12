---
title: "ricoh memory stick reader not working"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by avacado on 2009-11-22
Linux desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

DELL inspiron 1520
Intel core 2 duo T8300 2.4GHz 4GBRAM

my multi-card reader is not working.
Doesn't mount or even appear

Not the hugest issue because you can still use the camera and USB cable to act as card reader, but still would be nice if it worked.
The relevant section of dmesg follows (I think)

*-generic:1 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:03:01.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
                resources: memory:f9bfd600-f9bfd6ff

Any clues how to make it work?

---

### Post by sandyd on 2009-11-22
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238208](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238208)
you can get the SD reader working through sd_ricohcs though

---

### Post by Sealbhach on 2009-11-22
EDIT: bug.

---


---
title: "Intel Gigabit Ethernet not claimed"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by qbird on 2007-10-15
Thanks for reading this
I have an Intel Gigabit 82566DC card that works fine in Vista but is not claimed on Ubuntu Feisty.
lshww -C network
*-network UNCLAIMED
description: Ethernet controller
product: Intel Corporation
vendor: Intel Corporation
physical id: 19
bus info: pci@00:19.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0
resources: iomemory:f9ec000-f9edffff iomemory:f9efe000-f9efff ioport:c000-c01f irq:10

I tried installing e100 from intel, but it didn't work (presumably it's already in the distro?)
No probs connecting via USB modem

I'd be grateful for your help, as an honest noob.
Thanks :)

---

### Post by noob12 on 2007-10-15
Check this: [http://ubuntuforums.org/showthread.php?t=551720](http://ubuntuforums.org/showthread.php?t=551720)

---

### Post by qbird on 2007-10-16
Yep, you da man!
Thanks :-)

---


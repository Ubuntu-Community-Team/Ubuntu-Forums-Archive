---
title: "ubuntu doesn't seem to recognize my card"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by benner on 2007-06-28
i just picked up (the only) pci wireless adapter i could find in town.  it is made by a company called Airnet.  it just looks like a pretty generic 802.11g pci card, 54Mbps.  I think the model number is AWD154.  This is the first time I have tried to set up wireless on a ubuntu machine.  i looked at the network settings and saw eth0 but I didn't see any wireless device listed.  Am I out of luck?  the card only came with windows drivers on the disk.

---

### Post by benner on 2007-06-28
after a lot of reading, it turned out to be easy.  i installed ndiswrapper and ndisgtk.  downloaded the windows driver and everything worked.  i tried downloading it from sourceforge onto a flash drive and every time the file wouldn't open.  when i dragged the machine across the house to the router and connected directly, i downloaded the packages using synaptic.

---

### Post by lefthand on 2007-07-29
Benner, do you know if this card works with WPA under Feisty? I'm thinking of picking one up, but haven't been able to find that out. Thanks

---


---
title: "network UNCLAIMED"
date: 2020-10-04
forum: Networking &amp; Wireless
---

### Post by mmulhern on 2020-10-04
Completely new to ubuntu, come from an ms background, just built a computer with my 9 year old son so we can learn about ubuntu/linux together.
When I updated the drivers for the nvidia graphics card our wifi disappeared.  In network settings it says 'No Wi-Fi Adapter' found.

Ubuntu ver = 20.04 lts

sudo lshw -C network:
*-network UNCLAIMED
  description: Ethernet Controller
  product: RT8111/8168/8411 PCI Express Gigabit Ethernet Controlleer

*-network UNCLAIMED
  description: Ethernet Controller
  product: Wireless 8260

I know to fix the problem has something to do with a lack of drivers.  I'm just not sure how to fix or how to install drivers off a stick drive in Ubuntu.  Any help is appreciated.

---

### Post by jeremy31 on 2020-10-04
Moved to Networking & Wireless

What happens if you run this command in terminal ```
sudo modprobe -v iwlwifi
```

---


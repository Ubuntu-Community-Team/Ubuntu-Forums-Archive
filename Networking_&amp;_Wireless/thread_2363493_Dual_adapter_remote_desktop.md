---
title: "Dual adapter remote desktop"
date: 2017-06-10
forum: Networking &amp; Wireless
---

### Post by Maou on 2017-06-10
Okay, so a little bit of a weird setup I would like help with. I've tried a few different solutions but I can't seem to find a solution that fits all my requirements.

I'm running Ubuntu 17.04 with kernel 4.10 on a ryzen 1700x + gtx 1070 workstation for writing/running cuda/openacc/openmp code, and I need to be able to ssh into it from a cheap laptop.
Here's the twist, my only source of internet for the next two months is a wireless mobile hotspot, so I can't ssh over the internet due to data caps. 
I do, however, have two wifi adapters, one netgear usb ac 6100 and one tp ac 1300 pcie network adapter, both of which have drivers installed and are functioning well.
What I need to do, is use one adapter to create a local wireless network for the laptop to remote into the desktop, and at the same time I also need the desktop to connect to the mobile hotspot so I can work directly from my desktop while on my laptop.
I can currently only do one of these at any one time, is there a way to do both? The only similar solution I can find is sharing internet access wlan0 -> wlan1, but it's pretty involved and I don't need to share the access, just remote in on the wireless network while it's connected to the mobile hotspot.

thanks for your time, 

Maou.

---


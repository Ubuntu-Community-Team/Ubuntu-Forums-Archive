---
title: "am i missing something? (ndiswrapper)"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by el_ricardo on 2008-09-23
hi all, I've run into some trouble installing the drivers for my safecom swlpt54108 card. It uses the acx100 chip, and I've had it working numerous times in ubuntu, but this time it's not working, I installed the drivers with the following steps:

```

sudo modprobe -r acx
echo "blacklist acx" | sudo tee -a /etc/modprobe.d/blacklist

sudo niswrapper -i <path to tnet1130.inf>
sudo ndiswrapper -m
sudo ndiswrapper -ma
sudo ndiswrapper -mi

modprobe ndiswrapper

```

I'm sure those steps normally get the job done, the only difference is that I've upgraded to a 64 bit processor and motherboard, and I'm using the 64 bit version of ubuntu (hardy)

the problem is that wlan0 isn't appearing in my network config (if i open up network settings manager wlan0 isn't there). I've checked that ndiswrapper is loaded, and it is, I've rebooted to check it loads at boot, and it does ... I'm guessing i must have missed a step somewhere, hope someone can help!

cheers :)

---

### Post by Idefix82 on 2008-09-23
You can check whether ndiswrapper "claimed" responsibility for your Wifi card by typing in
```
lshw -C network
```
Under "configuration:" you should have something like "...driver=ndiswrapper+<your driver>..."

---

### Post by el_ricardo on 2008-09-23
no it's not been claimed, this is the output:

```

  *-network UNCLAIMED       
description: Network controller
product: ACX 111 54Mbps Wireless Interface
vendor: Texas Instruments
physical id: a
bus info: pci@0000:01:0a.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: latency=32

```

how do i go about "claiming" it?

---

### Post by Steve1961 on 2008-09-23
If you're now running the 64bit version of Ubuntu you need to use 64 bit windows drivers with ndiswrapper - using 32 bit drivers rarely works.  I'd go to the manufacturers website and see if they have 64 bit drivers available.

---

### Post by el_ricardo on 2008-09-23
yeah, you're quite right, and there are no 64bit drivers available for my card! I'm gonna try the opensource linux acx111 driver from [here]("http://acx100.sourceforge.net/") instead, looks complicated :D

thanks

---

### Post by Steve1961 on 2008-09-23
> **el_ricardo said:**
> yeah, you're quite right, and there are no 64bit drivers available for my card! I'm gonna try the opensource linux acx111 driver from [here]("http://acx100.sourceforge.net/") instead, looks complicated :D

thanks

Looks like that might be your best bet :)

---


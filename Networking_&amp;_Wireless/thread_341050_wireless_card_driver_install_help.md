---
title: "wireless card driver install help"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by jamesmorad on 2007-01-18
Hi everyone,

I'm new to Linux and decided to give Xubuntu a try on an old Dell Inspiron 4000 laptop. I purchased a wireless card online(Airnet AWN154) to use with this setup. So far my attempts at installing the driver for it have failed, but at least I am learning more about how this OS works. I've followed the instructional guide here [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

to install the Windows driver with Ndiswrapper, and I've gotten as far as when I type

[B]
ndiswrapper -l[/B]

i get:

[B]mrv8000c     driver present, hardware present
[/B]
then when I try to load the module with;

[B]sudo depmod -a
  sudo modprobe ndiswrapper
[/B]
i get:

**Segmentation fault**

](*,)  I'm thoroughly confused and don't want to give up on this yet. Any help or suggestion offered would be greatly appreciated. Thanks. :)

---

### Post by jamesmorad on 2007-01-18
bump?

anyone have an idea what i should do to get this driver working?

---

### Post by maclenin on 2007-01-18
I would try a couple of things:

1. **sudo lshw -C network** to find the "product" and "logical name" of your card - so that you could use those items as search criteria....

2. I would take a peek at this [howto]("http://ubuntuforums.org/showthread.php?t=192588"), as the card it's installing strikes me a very similar to the one you are trying to install....

Good luck!

---

### Post by jamesmorad on 2007-01-18
here's what I got with the 

```
sudo lshw -C network
```


```
*-network
description: 88W8310 802.11g Cardbus PC Card
product: 83
vendor: Marvell Semiconductor
physical id: 0
version: 01
slot: Socket 0
resources: irq:11
*-network UNCLAIMED
description: Ethernet controller
product: 88w8335 [Libertas] 802.11b/g Wireless
vendor: Marvell Technology Group Ltd.
physical id: 1
bus info: pci@02:00.0
version: 03
width: 32 bits
clock: 66MHz
capabilities: cap_list
resources: iomemory:22000000-2200ffff iomemory:22010000-2201ffff irq:11


```

I've tried the same howto you suggested and I've gotten as far as:

```
Installed ndis drivers:
mrv8000c    driver present, hardware present
```


but when I try:

```
sudo depmod
sudo modprobe ndiswrapper
```

I get:

```
Segmentation fault
```

Does segmentation fault *mean* anything? How can I use this result to fix this driver issue and make the card at least show up on my networking GUI menu?

---

### Post by jamesmorad on 2007-01-19
Okay, well I switched from Edgy Eft to Dapper Drake, and now I've gotten over the hurdle and my card is recognized in the Network configuration. 

Solved, for now i guess.

---


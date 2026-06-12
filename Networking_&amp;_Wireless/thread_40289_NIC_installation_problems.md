---
title: "NIC installation problems"
date: 2005-06-08
forum: Networking &amp; Wireless
---

### Post by Fugee on 2005-06-08
Seems I got the 2 worst and least used NICs in my computer. I have a Netgear EA201 (an old ISA NIC) and a Linksys wireless WMP54G (v2 I think, but will verify when I get home). 

The Linksys NIC I got installed after using ndiswrapper, but I can't seem to get it to connect to the router. I went so far as to disable any encrytion and enabled broadcast of my SSID. I think I may have to change the RadioStates in all my conf files and will try that when I get home.

The Netgear NIC is worse. I can't seem to find the drivers for it. ndiswrapper doesn't work with the drivers I have. I imagine ndiswrapper is only for wireless NICs (I could be wrong). I've read somewhere that this particular NIC uses the Tulip drivers, but haven't been able to find what it is they were talking about.

Any help would be appreciated.

---

### Post by jrhodes on 2005-06-08
This card is a ne2000-compatible NIC, which means it's often a pain. The kernel module you'll want to use is called ne. 

When you load the module, you need to supply it with the card's I/O address, which you can find by looking in the bios. (It might also be listed somewhere in /proc/bus/isa but I don't have an ISA system handy so I can't check.) 

For example:
assuming the card is located at I/O address 0x280
```
$ sudo /sbin/modprobe ne io=0x280
```

Hope this helps.

---

### Post by Fugee on 2005-06-18
[QUOTE=jrhodes]This card is a ne2000-compatible NIC, which means it's often a pain. The kernel module you'll want to use is called ne. 

When you load the module, you need to supply it with the card's I/O address, which you can find by looking in the bios. (It might also be listed somewhere in /proc/bus/isa but I don't have an ISA system handy so I can't check.) 

For example:
assuming the card is located at I/O address 0x280
```
$ sudo /sbin/modprobe ne io=0x280
```

Hope this helps.[/QUOTE]

Tried that and I got a fatal error.

---


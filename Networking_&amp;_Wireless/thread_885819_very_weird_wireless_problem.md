---
title: "very weird wireless problem"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by gseeli on 2008-08-10
I am using a RTL-8185 wireless card. lspci has this to say about the card:
```
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: d0100000-d01fffff
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

```
Now my problem is that on Ubuntu 8.04.1, kernel 2.6.22-14 generic the network manager recognizes the presence of the wireless card and it works just fine for what I've tried to do. But when I boot on Ubuntu 8.04.1, kernel 2.6.24-19, it does not recognize the presence of the wireless card or any way to use it. 
This confuses me because the newer version of Ubuntu is the one that isn't registering the wireless card. So does anyone have any possible fixes? 

Thanks in advance,
Gseeli

---


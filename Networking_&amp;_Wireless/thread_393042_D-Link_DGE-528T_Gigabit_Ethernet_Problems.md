---
title: "D-Link DGE-528T Gigabit Ethernet Problems"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by JonCage on 2007-03-25
I've spent all morning trying to get a D-Link DGE-528T card working on Ubuntu 6.10 server (kernel 2.6.17-10-server) and have failed miserably thus far. I've read that [since 2.6.10 this card should be detected and work automatically](http://www.linuxquestions.org/hcl/showproduct.php?product=2937&cat=133)..but that's not what I've seen!

As far as I can see, the card is detected:

```
/$ lspci -n
01:06.0 0000: 1186:4300

/$ lspci -v
01:06.0 Non-VGA unclassified device: D-Link System Inc DGE-528T Gigabit Ethernet Adapter
        Subsystem: D-Link System Inc DGE-528T Gigabit Ethernet Adapter
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 150
        I/O ports at <ignored>
        I/O ports at 1098 [size=4]
        Memory at de000000 (32-bit, non-prefetchable) [size=16]
        I/O ports at de000010 [size=16]
        I/O ports at <ignored>
        Expansion ROM at <unassigned> [disabled]
        Capabilities: [10] MSI-X: Enable- Mask- TabSize=1
```

I tried loading the module which gives no error:

```
/$ sudo modprobe r8169 eth1
/$
```

Looking at dmesg I can see there's a problem though:

```
[42949388.340000] r8169 Gigabit Ethernet driver 2.2LK loaded
[42949388.340000] r8169: probe of 0000:01:06.0 failed with error -22

```

If anyone has any ideas of even where to start with this I'd be very grateful.

Cheers,
Jon

---


---
title: "Motherboard change, Nvidia nForce not configured"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by lrmall01 on 2006-11-18
I recently did a mobo swap.  After booting up the network card is not configured properly.  It seems that it is detected and the foredeth module is used.  However, ifupdown gives no eth0 configuration.

It is an old mobo, so the chipset should be supported.  Also, I write this from a Xubuntu liveCD, so I know that it will work somehow with Ubuntu.

I'm not sure what files need to possibly be tweaked since I changed the network chipset.  I searched the forum and found something on maybe un-blacklisting the module, but I'm not quite sure how to do that.

Any suggestions greatly appreciated.  Also, below is the lspci -v output in case it helps.

00:04.0 Ethernet controller: nVidia Corporation nForce Ethernet Controller (rev c2)
        Subsystem: Compaq Computer Corporation Unknown device 00a8
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 193
        Memory at f8503000 (32-bit, non-prefetchable) [size=1K]
        I/O ports at 24d0 [size=8]
        Capabilities: <access denied>

---

### Post by MetalMusicAddict on 2006-11-18
On a mobo swap you should do a reinstall.

---


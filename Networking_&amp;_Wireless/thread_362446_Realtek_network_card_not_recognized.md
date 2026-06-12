---
title: "Realtek network card not recognized"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by Roma_emu on 2007-02-15
Hello,

I bought an Encore Realtek ENL832-TX-RENT network card (PCI) today, then I plugged it in the PCI slot, but Linux isn't recognizing it. It doesn't show up as eth1 (I have an on-board network card which is eth0). Here is the output from lspci -vv:

00:13.0 Ethernet controller: Unknown device 1904:8139 (rev 01)
        Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (5000ns min, 10000ns max)
        Interrupt: pin A routed to IRQ 255
        Region 0: Memory at f0800000 (32-bit, non-prefetchable) [disabled] [size=256]
        Region 1: I/O ports at 8800 [disabled] [size=256]
        [virtual] Expansion ROM at 30000000 [disabled] [size=128K]
        Capabilities: <access denied>

The card came with a mini-CD with drivers; the Linux folder had four files (?????.txt, Makefile, readme.txt and sc92031.c). But when I try running make, it complains that config.h is missing (I'm using a compiled 2.6.19.2 kernel because I couldn't install the proper nvidia drivers for my agp card with the default edgy kernel), and indeed, there is no config.h in the /lib/modules/2.6.19.2-nvidiayeah/build/include/linux folder - only a configfs.h.

So... could anyone help me? What should I do? :(

---

### Post by Roma_emu on 2007-02-15
Wow, topics get bumped off really fast in this forum. I'll only push this topic back up once.

I'll go back to the store tomorrow (I have to pick up an HD that wasn't available today), and if I can't get this solved, I'll try returning the card and changing it for something else...

[edit]
I think the 8139too driver might work. But how do I make Ubuntu use it for that card?

---

### Post by dyingsun on 2007-02-26
I am having the same trouble; Ubuntu won't even recognise there is a card there. I tried it originally on Dapper, now Edgy. Don't want to have to revert to XP just so I can get online, which is why I am bumping this thread for my own selfish agenda :)

---


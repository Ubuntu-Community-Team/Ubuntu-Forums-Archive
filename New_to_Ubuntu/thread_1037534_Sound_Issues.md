---
title: "Sound Issues"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by Intercamino on 2009-01-11
I'm having some problems with my sound right now. I'm not getting any sound at all from my speakers. 

When I first installed Xubuntu, I didn't have sound. Then I randomly had sound for a while, and now I don't have sound anymore.

I've gone through my computer, and according to terminal, it recognizes my sound card, and I have the necessary packages installed.

Any suggestions?

---

### Post by hotweiss on 2009-01-11
> **Intercamino said:**
> I'm having some problems with my sound right now. I'm not getting any sound at all from my speakers. 

When I first installed Xubuntu, I didn't have sound. Then I randomly had sound for a while, and now I don't have sound anymore.

I've gone through my computer, and according to terminal, it recognizes my sound card, and I have the necessary packages installed.

Any suggestions?

What computer/soundcard do you have?

---

### Post by Intercamino on 2009-01-11
I have an old Micron computer with a Pentium 3-733 mhz; 256 mb of ram; and an 80gb hard drive. 

My sound card is a motherboard integrated.

---

### Post by hotweiss on 2009-01-12
> **Intercamino said:**
> I have an old Micron computer with a Pentium 3-733 mhz; 256 mb of ram; and an 80gb hard drive. 

My sound card is a motherboard integrated.

Using

    > lspci -v | less

what sound card is identified?

---

### Post by Intercamino on 2009-01-13
This comes up when I put that command into terminal:


00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev 82)
        Flags: bus master, medium devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>
        Kernel driver in use: agpgart-via
        Kernel modules: via-agp

00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: e8000000-e9ffffff
        Prefetchable memory behind bridge: d0000000-dfffffff
        Capabilities: <access denied>
        Kernel modules: shpchp

00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 12)
        Subsystem: VIA Technologies, Inc. Device 0000
        Flags: bus master, stepping, medium devsel, latency 0

00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])


I don't think any of that is my sound card. I know that my sound card is integrated into my motherboard. Do I need a PCI soundcard to get my sound to work?

---


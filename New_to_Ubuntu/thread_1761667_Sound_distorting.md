---
title: "Sound distorting"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by ThRixXx on 2011-05-18
Just installed Ubuntu 10.4 today.  When listening to music or any sound it distorts, unless the volume sliders are really low.

Temp fix: application and system volume sliders ain't merged so I keep the application one at about 25 - if it isn't lower.

Anyways, this is what the system picks up:

```
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
        Subsystem: ASUSTeK Computer Inc. Device 840c
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at ddef4000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
```

But in the booklet I find the following info:

The onboard 8-channel High Definition Audio CODEC enables high-quality 192KHz/24-bit audio output, jack-sensing feature, and multi-streaming technology that blablabla.

And:

Audio	VT1708S High Definition Audio 8-Channel CODEC
*Choose the chassis with HD audio module in front panel to support 8-Channel audio output
- Support S/PDIF out interface
- Support Multi-streaming, Single SPDIF Out, Anti-pop Function 

Motherboard: [http://www.asus.com/Motherboards/AMD_AM3/M4N68TM/#specifications](http://www.asus.com/Motherboards/AMD_AM3/M4N68TM/#specifications)

Thanks, 
Michael

---

### Post by jean noel on 2011-05-18
Hello, do your sound profile match that of your speakers? Check it under system=>preferences=>sound=>hardware. I used to have bad sound until I found out that my sound profile was on analog surround 5.1 whereas I was using creative 4.0 speakers.
Good luck.
Jean Noel

---

### Post by ThRixXx on 2011-05-19
Hi,

Yes I have checked.  I'm just using a basic 2.1 system.  Logitech Z-2300's

---

### Post by jean noel on 2011-05-22
why not use a preset speaker level, and adjust the volume control on the panel.

---


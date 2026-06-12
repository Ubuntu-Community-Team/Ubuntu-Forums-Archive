---
title: "Bar erosion in natty"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by mmasroorali on 2011-08-26
Dear All,
I do not know how to describe this problem. But after I upgraded to natty, the top and bottom bars are being eroded at random. See the image, the top bar has the right part missing. 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=200851&stc=1&d=1314381248[/IMG]

This sometimes happens for the bottom bar, where some part are not displayed and take a Manhattan view. These come back when the mouse is moved over the missing part.

This is happening both for my office and home machines. My home machine has 3 GB RAM, office machine 2 GB. So the problem should not be there.

Any suggestion will be appreciated.

---

### Post by wojox on 2011-08-27
What are you using for video card/chip?

---

### Post by mmasroorali on 2011-08-27
> **wojox said:**
> What are you using for video card/chip?

Thanks for your answer.

lspci -v gives,
```
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
        Subsystem: Dell Device 01ad
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at feb00000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at e898 [size=8]
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Memory at feac0000 (32-bit, non-prefetchable) [size=256K]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: intelfb, i915

```

My home machine (the above one) is a Dell OptiPlex GX620 machine and has been with me since April 2006. This one uses a Intel 945G chipset.

My office machine is very new. One of the latest models from Dell. Before this machine was replaced around two weeks back, I had an HP more than five years old. This one also showed same kind of bar erosion in natty.

---

### Post by LowSky on 2011-08-28
I get the same issue using a Nvidia graphics card and proprietary driver and Ubuntu Classic with no effects.

see attached image, of my lower panel. Appears only after I hover over a thread that displays info, like a Ubuntu Forums link.

I'm surprised it can be caught using print screen.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=200955&d=1314519668[/IMG]

---


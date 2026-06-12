---
title: "Can anyone explain this xorg.log error?"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by migrate from windows on 2011-03-04
Whenever I try to enable compiz the x tries to restar ending with a black screen with this error foun in the xorg.log

[   113.476] (**) intel(0): SwapBuffers wait enabled
[   113.476] (**) intel(0): VideoRam: 131072 KB
[   113.476] (EE) intel(0): Failed to allocate framebuffer.
[   113.476] (EE) intel(0): Couldn't allocate initial framebuffer.
[   113.476] 
Fatal server error:
[   113.476] AddScreen/ScreenInit failed for driver 0


Is there anybody who can explain this???

---

### Post by Hippytaff on 2011-03-04
You graphics card might noy be up to the job

---

### Post by Rubi1200 on 2011-03-04
Please post the specifications for the computer, especially RAM and graphics card.

Thanks.

---

### Post by migrate from windows on 2011-03-04
RAM is 1GB

the graphics card is..

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at e0000000 (32-bit, prefetchable) [size=128M]
    Region 1: Memory at ec100000 (32-bit, non-prefetchable) [size=512K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

---

### Post by Rubi1200 on 2011-03-05
What version of Ubuntu are you running?

Try adding this parameter at boot time and see if it makes a difference:

When you see the GRUB menu and the entry for Ubuntu is highlighted press "e" to edit.

Find the line that ends with quiet splash and add i915.modeset=1

It should look like this:

>  quiet splash  i915.modeset=1

Then "Ctrl" + "x" to boot.

If it helps, we can make this more permanent.

---

### Post by migrate from windows on 2011-03-05
> **Rubi1200 said:**
> What version of Ubuntu are you running?

Try adding this parameter at boot time and see if it makes a difference:

When you see the GRUB menu and the entry for Ubuntu is highlighted press "e" to edit.

Find the line that ends with quiet splash and add i915.modeset=1

It should look like this:



Then "Ctrl" + "x" to boot.




If it helps, we can make this more permanent.

Using Ubuntu 10.10,   and i915.modeset=1 doesn't help

---


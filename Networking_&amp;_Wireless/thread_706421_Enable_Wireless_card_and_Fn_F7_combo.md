---
title: "Enable Wireless card and Fn F7 combo"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by dpatel on 2008-02-24
Hi - I've just bought a new laptop and installed Ubuntu. I'm fairly new to Ubuntu/Linux.

I can't seem to get the wireless card working. It works fine in Vista. You need to press a key combo of Fn+F7 to enable the wireless card. Any ideas how I get Ubuntu to recognise this combo or a way around?

Not sure I have the correct driver. Here is the output of lspci:

```

0a:00.0 Network controller: RaLink Unknown device 0781
        Subsystem: RaLink Unknown device 2790
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at c2000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
```

Ralink to Linux drivers but not sure if mine is supported (and no idea how to install them).

Do I even need new drivers or am I doing something stupid?

Any help much appreciated.

---

### Post by dpatel on 2008-02-25
Ralink do a Windows based driver that is for the 2790 (I think that's the chipset).

Can I use ndiswrapper? I've tried using it but I can't extract the .inf/.sys files (tried cabextract and unshield) - no joy.

Can anyone suggest anything?

---


---
title: "[SOLVED] help connecting with pppoe in Xubuntu"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by Adam590 on 2007-11-15
I just installed Xubuntu 6.06.1-alternate on an old Pentium II machine.

(Background: this machine has an ethernet port and was able to connect to our ADSL via Win98.)

I'm here at the command line and trying to run pppoeconfig. At the first screen, I see "eth0" listed as the only device. At the next screen, the scanning device can't find the Access Concentrator.

**ifconfig** gives me this:

```

eth0        Link encap:Ethernet  HWaddr 00:11:6B:30:DE:33
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 b)   TX bytes:0 (0.0 b)
            Interrupt:11  Base address:0x8f00

lo          Link encap:Local Loopback
            inet addr:127.0.0.1   Mask:255.0.0.0
            UP LOOPBACK RUNNING   MTU:16436   Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 b)   TX bytes:0 (0.0 b)
```


I had a computer running Ubuntu Feisty 7.04 that could connect fine using PPPoE. One difference was that it listed two devices during the pppoeconfig process - eth0 _and_ eth1. Not sure if that's relevant...

Any advice on what to check/modify?

---

### Post by Adam590 on 2007-11-15
Anybody? I'm going to wear out Google on this...

**lspci -v** returns:

```
Ethernet controller: Realtek Semiconductor Co., Ltd. RT8139
Flags: bus master, medium devsel, latency 64, IRQ 11
I/O ports at dc00 [size=256]
Memory at ebfeff00  (32-bit, non-prefetchable) [size=256]
Expansion ROM at ebfd0000 [disabled] [size=64k]
Capabilities: [50] Power Management version 2
```

Is there any way to tell if Xubuntu came with the right drivers for this, or if it's being recognized correctly, etc?

It seems like it's good that **ifconfig** lists eth0 as UP, but from other posts here it looks like I should have an **inet addr:** line for it...?

---

### Post by Adam590 on 2007-11-15
SOLVED!!!

with the pci=noacpi boot flag mentioned in post #5 of [**_[COLOR="Blue"]this thread[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=580773"). Hooray!

---


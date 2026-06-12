---
title: "Ethernet network problem causing /var/log files to fill up all available space"
date: 2016-11-27
forum: Networking &amp; Wireless
---

### Post by astro11 on 2016-11-27
Hello. I've been having a network problem that fills up the files **kern.log** and **syslog** until my SSD doesn't have any space left.

I noticed this problem occurs when I do these steps:
[LIST=1]
[*]Ubuntu is connected to the ethernet.
[*]Disconnect the cable, connect to the wireless network -- move computer to another location.
[*]After a while, move computer back, disconnect the wireless and reconnect the ethernet cable.
[*]Wait a random amount of time (usually hours).
[*]Ubuntu automatically disconnects from ethernet (cable still inserted, router working fine).
[*]Ubuntu automatically connects to the wireless network.
[*]The above mentioned files start to get filled with (almost) the same string: **Nov 27 10:53:01 <computer_name> kernel: [148131.895532] alx 0000:08:00.0 enp8s0: fatal interrupt 0x4019607, resetting**
[/LIST]
Since Ubuntu connects to the wireless, sometimes I don't detect the error and continue browsing/working. One or two days later my SSD has 0 bytes left, sometimes even breaking Ubuntu to the point I can't login and I have to boot into the terminal mode to remove the log files.

Some information that might be useful:

**lsb_release -a**
```
No LSB modules are available.Distributor ID:    Ubuntu
Description:    Ubuntu 16.10
Release:    16.10
Codename:    yakkety
```

**uname -a**
```
Linux <computer_name> 4.8.0-27-generic #29-Ubuntu SMP Thu Oct 20 21:03:13 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

**lspci -v (for my ethernet controller)**
```
08:00.0 Ethernet controller: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller (rev 10)
    Subsystem: Dell Killer E220x Gigabit Ethernet Controller
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at d2400000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 3000 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [c0] MSI: Enable+ Count=1/16 Maskable+ 64bit+
    Capabilities: [d8] MSI-X: Enable- Count=16 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [180] Device Serial Number ff-34-89-1a-ec-f4-bb-ff
    Kernel driver in use: alx
    Kernel modules: alx



```

---

### Post by Hadaka on 2016-11-27
Hi, when the ethernet cable is plugged in it "should" disable the wireless connection.
Your error shows "**fatal interrupt "**
Why it is doing this is at this time unknown. It may be a faulty cable, or connection or router problem.
Further research and testing will be required on your part. ...meantime...
 To avoid the wireless connecting while
the the ethernet cable is attached, uncheck the "Connect Automatically" box in the network
manager under Edit Connections>>Wireless>>your-ssid>>Edit and uncheck the Connect Automatically
box. see attached..
[ATTACH=CONFIG]272423[/ATTACH]

---

### Post by astro11 on 2016-11-30
> **Hadaka said:**
> Hi, when the ethernet cable is plugged in it "should" disable the wireless connection. I've been using Ubuntu on this laptop for a while now, and since 16.04 it doesn't disable the wireless connection automatically. Instead, it stays "connected" on both, at least from the connection information thing on the top taskbar. I'll see if something changes now that I disabled the automatic connection. This has been happening with different routers and cables, so I don't think it's hardware related (well, at least not these hardware).

---


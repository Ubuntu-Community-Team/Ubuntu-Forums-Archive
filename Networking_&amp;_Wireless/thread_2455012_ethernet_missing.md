---
title: "ethernet missing"
date: 2020-12-10
forum: Networking &amp; Wireless
---

### Post by ericayoung on 2020-12-10
.

---

### Post by TheFu on 2020-12-10
There doesn't seem to be any ethernet adapter seen.  That could mean bad hardware, that the hardware was disabled in the BIOS or that the needed driver isn't available.

```
$ lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/' 
```
should show all physical the network adapters.

---

### Post by ericayoung on 2020-12-10
lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/'

does not return anything

---

### Post by TheFu on 2020-12-10
The computer doesn't think there is any wired ethernet adapter.
Something like this is what I see on all my systems, except the single-board computers which don't have any PCI:
```
$ lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/' 
03:00.0 Ethernet controller: Intel Corporation I211 Gigabit Network Connection (rev 03)
        Subsystem: ASUSTeK Computer Inc. I211 Gigabit Network Connection
        Flags: bus master, fast devsel, latency 0, IRQ 29
        Memory at f6600000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at d000 [size=32]
        Memory at f6620000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: igb
        Kernel modules: igb
```

Check the other things mentioned in my other post.

---


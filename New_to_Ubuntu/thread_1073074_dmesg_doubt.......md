---
title: "dmesg doubt......"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by veda87 on 2009-02-17
whenever i typed a dmesg command in the terminal. the following is shown.
from this i wanted to know what these numbers means ( numbers like 33.026565, 33.026571, etc).


[   33.026565] Bluetooth: L2CAP ver 2.8
[   33.026571] Bluetooth: L2CAP socket layer initialized
[   33.079523] Bluetooth: RFCOMM socket layer initialized
[   33.079556] Bluetooth: RFCOMM TTY layer initialized
[   33.079560] Bluetooth: RFCOMM ver 1.8
[   33.940616] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
[   36.092449] [drm] Initialized drm 1.1.0 20060810
[   36.094324] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 18
[   36.095504] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   37.155474] NET: Registered protocol family 17
[   38.969718] NET: Registered protocol family 10
[   38.969817] lo: Disabled Privacy Extensions
[   49.763674] eth0: no IPv6 routers present

---

### Post by unutbu on 2009-02-18
They represent the number of seconds since the machine booted up.

---


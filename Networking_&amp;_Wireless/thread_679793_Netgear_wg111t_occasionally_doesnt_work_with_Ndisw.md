---
title: "Netgear wg111t occasionally doesnt work with Ndiswrapper"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by northyj0e on 2008-01-27
I have compiled and installes ndiswrapper [from tarball] and most of the time i have it working with my netgear wg111t.
However, occasionally the driver fails to initialize.
This is the relevant output from 'sudo dmesg' 

```
[   51.703817] ndiswrapper: driver netwg11t (NETGEAR,09/05/2005,1.5.0.2102) loaded
[   51.704818] ndiswrapper (ZwQueryValueKey:2379): not fully implemented (yet)
[   51.892139] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   51.892154] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 21
[   66.772812] ndiswrapper (NdisWriteErrorLogEntry:192): log: C0001389, count: 4, return_address: f8b0cbbb
[   66.772821] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xdfbdde00
[   66.772826] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x28
[   66.772831] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xf8a98000
[   66.772835] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xf8a98000
[   66.773009] ndiswrapper (mp_init:263): couldn't initialize device: C0000001
[   66.773017] ndiswrapper (pnp_start_device:440): Windows driver couldn't initialize the device (C0000001)
[   66.773032] ndiswrapper (mp_halt:305): device dfbba500 is not initialized - not halting
[   66.773041] ndiswrapper: device eth%d removed
[   66.773062] ndiswrapper: probe of 1-2:1.0 failed with error -22

```

Anyone ideas why this is happening or experiencing similar problems?
I have the latest wg111t driver and the latest ndiswrapper.

Thanks
Joe

---

### Post by northyj0e on 2008-02-02
*bump* any help would be much appreciated guys,..

---

### Post by liquideath on 2008-02-04
I have a similar problem, but for me it fails to work at bootup every time, but I fixed it by removing ndiswrapper module, removing and replacing the usb stick, and starting the module again.

ie:
```

$sudo modprobe -r ndiswrapper
replace usb stick
$sudo modprobe ndiswrapper

```

I'm using the 2.1 wg111t drivers, latest ndiswrapper in repositories, and I have the device id 1385:4251 (there is also a 1385:4250 I believe).

This is what happens during a failure (at startup):
```

Feb  3 12:10:18 matt-desktop kernel: [  201.391083] ndiswrapper version 1.45 loaded (smp=yes)
Feb  3 12:10:18 matt-desktop kernel: [  201.702108] ndiswrapper: driver netwg11t (NETGEAR,09/05/2005,1.5.0.2102) loaded
Feb  3 12:10:33 matt-desktop kernel: [  216.752864] ndiswrapper (mp_init:263): couldn't initialize device: C0000001
Feb  3 12:10:33 matt-desktop kernel: [  216.752869] ndiswrapper (pnp_start_device:440): Windows driver couldn't initialize the device (C0000001)
Feb  3 12:10:33 matt-desktop kernel: [  216.752878] ndiswrapper (mp_halt:305): device eb80b500 is not initialized - not halting
Feb  3 12:10:33 matt-desktop kernel: [  216.754068] ndiswrapper: device eth%%d removed
Feb  3 12:10:33 matt-desktop kernel: [  216.754081] ndiswrapper: probe of 2-1:1.0 failed with error -22

```

After doing the procedure above I get this:

```

Feb  3 16:37:20 matt-desktop kernel: [ 2765.983539] ndiswrapper version 1.45 loaded (smp=yes)
Feb  3 16:37:20 matt-desktop kernel: [ 2766.021659] usbcore: registered new interface driver ndiswrapper
Feb  3 16:37:23 matt-desktop kernel: [ 2769.317436] ndiswrapper: driver netwg11t (NETGEAR,09/05/2005,1.5.0.2102) loaded
Feb  3 16:37:24 matt-desktop kernel: [ 2770.011615] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'

```

---

### Post by northyj0e on 2008-02-10
Thanks a lot, are there any plans for a long-term fix?

---

### Post by liquideath on 2008-02-10
Interestingly enough, the adapter fails to work at startup in windows about half the time. Also, under heavy traffic it eventually gets hot and stops working. I have a netgear router too that has problems - it is my advice to everyone to stay far away from netgear products, not just for linux. They just suck.

---

### Post by northyj0e on 2008-02-11
Yeah I'll keep that in mind next time we're due for a router upgrade.
I have also experienced the failing under load, it's not thrilling

---


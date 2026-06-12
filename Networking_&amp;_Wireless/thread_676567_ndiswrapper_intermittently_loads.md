---
title: "ndiswrapper intermittently loads"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by skibumhoff on 2008-01-23
I have followed the instructions in the post and have successfully enabled my wireless card on a Inspiron 1521 with the 1390 WLAN card using the ndiswrapper driver. 

However, upon restart the wireless card intermittently fails to load. Generally, I have to restart 3-4 times before the ndiswrapper loads and is recognized. 

The command `modprobe ndiswrapper` hangs if I try to to load ndiswrapper after the driver fails to load on startup. 

lspci output:
lspci -v
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
        Subsystem: Dell Unknown device 0007
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fe8fc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

dmesg | grep ndiswrapper
[   29.828740] ndiswrapper version 1.50 loaded (smp=yes, preempt=no)
[   29.918429] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   29.920156] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   29.926499] ndiswrapper (NdisWriteErrorLogEntry:191): log: C000138D, count: 1, return_address: ffffffff8850853e
[   29.926503] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x110
[   29.926521] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[   29.926526] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[   29.926535] ndiswrapper (mp_halt:259): device ffff81006f9ad780 is not initialized - not halting
[   29.926542] ndiswrapper: device eth%d removed
[   29.926563] ndiswrapper: probe of 0000:0b:00.0 failed with error -22
[   29.934107] usbcore: registered new interface driver ndiswrapper

When it does work dmseg looks like
dmesg | grep ndiswrapper
[   34.828260] ndiswrapper version 1.50 loaded (smp=yes, preempt=no)
[   34.917927] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   34.919646] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   34.926780] ndiswrapper: using IRQ 17
[   35.303089] usbcore: registered new interface driver ndiswrapper
[   35.309460] ndiswrapper: changing interface name from 'wlan0' to 'eth1'

---

### Post by wieman01 on 2008-01-24
Strange thing. But I think I have a similar problem from time to time. The problem started to occur a couple of days ago.

Which version of 'ndiswrapper' have you got and what instructions did you follow?

---


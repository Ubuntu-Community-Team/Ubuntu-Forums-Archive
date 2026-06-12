---
title: "Ndiswrapper error -22"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by Staudie on 2007-04-28
Im setting up my WG11t wireless USB this morning and everything is going great. I followed [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
to set up WPA. It works great I can connect with ny troubles. The I reset the machine and wlan0 disappears. I found this in my dmesg:

```
[   24.696000] ndiswrapper version 1.42 loaded (smp=yes)
[   24.916000] usb 2-2: reset high speed USB device using ehci_hcd and address 2
[   25.064000] ndiswrapper: driver netwg11t (NETGEAR,01/07/2005,1.0.1.1007) loaded
[   40.100000] ndiswrapper (NdisWriteErrorLogEntry:191): log: C0001389, count: 4, return_address: f9e2bc6b
[   40.100000] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0xf7e1d7b8
[   40.100000] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x28
[   40.100000] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0xf9db2004
[   40.100000] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0xf9db2004
[   40.100000] ndiswrapper (miniport_init:268): couldn't initialize device: C0000001
[   40.100000] ndiswrapper (pnp_start_device:425): Windows driver couldn't initialize the device (C0000001)
[   40.100000] unregister_netdevice: device eth%d/f7e1d000 never was registered
[   40.100000] ndiswrapper (miniport_halt:332): device f7e1d400 is not initialized - not halting
[   40.100000] ndiswrapper: device eth%d removed
[   40.100000] ndiswrapper: probe of 2-2:1.0 failed with error -22
```Im not sure what the problem might be "ndiswrapper -l" will show the device but its missing from "iwconfig". Im going to check into the ndiswrapper error and see what I find.

Thanks,
-Staudie

---


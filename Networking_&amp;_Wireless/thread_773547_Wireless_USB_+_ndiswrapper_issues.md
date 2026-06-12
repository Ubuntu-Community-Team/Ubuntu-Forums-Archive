---
title: "Wireless USB + ndiswrapper issues"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by bwgoudey on 2008-04-28
Hi all, 
  I've been trying for a while to get my TL-WN620G (Atheros based) USB WiFi adaptor to work. I had it working intermittently but after upgrading to 8.04 I have no luck at all. I'm using the latest windows drivers via ndiswrapper 1.52. The dongle is found but fails to install properly, with dmesg stating that the "Windows driver couldn't initialize the device". I'm somewhat stuck as to what to do. Any suggestions?

Cheers

dmesg | grep ndiswrapper
```

ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
ndiswrapper: driver net5523 (TP-LINK,07/27/2005,1.5.0.102) loaded
ndiswrapper (ZwQueryValueKey:2359): not fully implemented (yet)
ndiswrapper (NdisWriteErrorLogEntry:191): log: C0001389, count: 4, return_address: d8c18bab
ndiswrapper (NdisWriteErrorLogEntry:194): code: 0xd2722200
ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x28
ndiswrapper (NdisWriteErrorLogEntry:194): code: 0xd8b80000
ndiswrapper (NdisWriteErrorLogEntry:194): code: 0xd8b80000
ndiswrapper (mp_init:216): couldn't initialize device: C0000001
ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
ndiswrapper (mp_halt:259): device d2870480 is not initialized - not halting
ndiswrapper: device eth%d removed
ndiswrapper: probe of 1-2.3:1.0 failed with error -22
usbcore: registered new interface driver ndiswrapper

```

ndiswrapper -l
```

athfmwdl : driver installed
		device (0CF3:0002) present
net5523 : driver installed
		device (0CF3:0002) present

```

---

### Post by wernerd on 2008-07-06
Hi did you manage to sort this issue out? I am struggling with the same issue!?!?! Please could you let me know? many thanks in advance!

---

### Post by bwgoudey on 2008-07-06
I never was able to sort this problem out. Like many others I had read about, I simply gave up and bought myself a wireless network card (specifically a TP-Link TL-WN651G). Not only was it supported straight away but it gives me a much better connection.  

Good luck in finding a proper solution. Sorry I couldn't help

---


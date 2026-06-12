---
title: "ndiswrapper fails to initalize at boot time"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by tom_adams on 2006-12-26
ndiswrapper is not loading properly at boot time.  see dmesg output below.

My workaround is to repeatedly run the following until wlan0 shows up in iwconfig output:
  sudo rmmod ndiswrapper
  sudo depmod -a
  sudo modprobe -v ndiswrapper

It usually takes 3-4 manual reloads of ndiswrapper  before iwconfig shows that the wireless has been detected, then everything works.

Any thoughts?
Thanks.



Here is an example of the boot-time failure of ndiswrapper from dmesg

[   40.834915] NET: Registered protocol family 17
[   40.940690] ndiswrapper version 1.31 loaded (preempt=no,smp=yes)
[   41.041038] ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver
[   41.044157] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[   41.045329] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 17
[   41.045340] GSI 21 sharing vector 0xD9 and IRQ 21
[   41.045348] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNK3] -> GSI 17 (level, low) -> IRQ 217
[   41.049488] ndiswrapper (NdisWriteErrorLogEntry:231): log: C000138D, count: 1, return_address: ffffffff8830613e
[   41.049497] ndiswrapper (NdisWriteErrorLogEntry:234): code: 0x114
[   41.049517] ndiswrapper (miniport_init:270): couldn't initialize device: C0000001
[   41.049528] ndiswrapper (pnp_start_device:426): Windows driver couldn't initialize the device (C0000001)
[   41.049545] unregister_netdevice: device eth%d/ffff810047907000 never was registered
[   41.049558] ndiswrapper (miniport_halt:327): device ffff810047907500 is not initialized - not halting
[   41.049574] ndiswrapper: device eth%d removed

---

### Post by Spin Doctor on 2006-12-26
Hi there!

Make sure you have the follwing entry in /etc/modules 

```
ndiswrapper
```Put this on its own row right after anything else you might allready have there.

Hope this helps ya!

---

### Post by tom_adams on 2006-12-29
Thanks, I added ndiswrapper to /etc/modules but nidswrapper still encounters errors at boot time.


FYI ... dmesg reports that ndiswrapper tries to load ... but it encounters an errors such as ...



ndiswrapper (NdisWriteErrorLogEntry:231): log: C000138D, count: 1, return_address: ffffffff8830213e

 ndiswrapper (NdisWriteErrorLogEntry:234): code: 0x114

 ndiswrapper (miniport_init:270): couldn't initialize device: C0000001

---


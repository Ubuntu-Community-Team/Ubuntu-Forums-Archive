---
title: "Wireless not working"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by Naatan on 2008-08-14
I just installed the amd64 version of Ubuntu and am having problems getting wireless working, I previously had the wrong processor version installed but the following steps had worked for me (after setting up ndiswrapper with the correct version)

```
sudo modprobe -r ath_pci
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```Now however it doesn't work, I have no wireless device in ifconfig or iwconfig and when I do ndiswrapper -l it shows the following:

```
net5211 : driver installed
    device (168C:001C) present (alternate driver: ath_pci)
```Even though I added ath_pci to the /etc/modprobe.d/blacklisted file

What's different is that when I install the drivers it gives a lot of the following lines:

```
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64

```I've tried both the 32bit and the 64bit drivers.

edit: just noticed the following errors in dmesg:

```
[25767.722073] ndiswrapper (ntoskernel_exit:2708): object ffff810066a7dc30(2) was not freed, freeing it now
[25769.372320] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[25769.416552] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[25769.418234] ndiswrapper: driver net5211 (,06/21/2007,5.3.0.56) loaded
[25769.418513] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK1E] -> GSI 16 (level, low) -> IRQ 16
[25769.418562] ndiswrapper (ZwClose:2227): closing handle 0x0 not implemented
[25769.418702] PCI: Setting latency timer of device 0000:03:00.0 to 64
[25769.419486] ndiswrapper (NdisWriteErrorLogEntry:191): log: C0001389, count: 4, return_address: ffffffff88d405de
[25769.419493] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x7c946800
[25769.419496] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x28
[25769.419498] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0xa16000
[25769.419501] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0xa16000
[25769.419593] ndiswrapper (mp_init:216): couldn't initialize device: C000009A
[25769.419599] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[25769.419612] ndiswrapper (mp_halt:259): device ffff810054a98700 is not initialized - not halting
[25769.419615] ndiswrapper: device eth%d removed
[25769.419626] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[25769.419642] ndiswrapper: probe of 0000:03:00.0 failed with error -22
[25769.423867] usbcore: registered new interface driver ndiswrapper
[25839.800497] usbcore: deregistering interface driver ndiswrapper
[25839.801035] ndiswrapper (ntoskernel_exit:2708): object ffff810066a7d630(2) was not freed, freeing it now
[26064.206562] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[26064.221401] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[26064.221412] ndiswrapper (load_sys_files:210): couldn't prepare driver 'net5211'
[26064.222237] ndiswrapper (load_wrap_driver:112): couldn't load driver net5211; check system log for messages from 'loadndisdriver'
[26064.224208] usbcore: registered new interface driver ndiswrapper

```

But no idea how to solve it.

can anyone tell me what I might be doing wrong?

---

### Post by Naatan on 2008-08-14
bump

---

### Post by Naatan on 2008-08-14
bump

---

### Post by Naatan on 2008-08-14
Come on! No one knows? :(

---

### Post by Naatan on 2008-08-14
another bump :(

---

### Post by Naatan on 2008-08-14
bump!

---


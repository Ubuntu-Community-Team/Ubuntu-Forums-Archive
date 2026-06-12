---
title: "wifi disappeared after security update"
date: 2015-10-13
forum: Networking &amp; Wireless
---

### Post by dofin on 2015-10-13
Hi

Last week I had the update to kernel 3.13.0-65.106 (previously I had 65.105) and since then my wifi is gone.
It has been back for some time after a reboot, but now it's gone again and rebooting doesn't help.

Do you have any idea how to fix this?

I'm running Ubuntu 14.04.0 LTS, and here is extra info
```
$ uname -a
Linux pierre-laptop 3.13.0-65-generic #106-Ubuntu SMP Fri Oct 2 22:08:27 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
$ lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port [8086:0151] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.3 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 [8086:1e16] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation HM77 Express Chipset LPC Controller [8086:1e57] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
01:00.0 3D controller [0302]: NVIDIA Corporation GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M] [10de:1140] (rev ff)
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)
08:00.1 SD Host controller [0805]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)
$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:644d Microdia 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 045e:0797 Microsoft Corp. 
Bus 003 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
$ rfkill list all
$ iwconfig 
eth0      no wireless extensions.

lo        no wireless extensions.

```

---

### Post by ian-weisser on 2015-10-14
If you reboot into an older kernel at GRUB, does the wifi return and stay?

---

### Post by dofin on 2015-10-14
No, it didn't (I just tried versions -62 and -63).
Then the kernel update would not be the explanation? Anything else to explore?
Thx

---

### Post by ian-weisser on 2015-10-14
I don't see any wifi devices listed in your lspci or lsusb.
Are they there? Did I miss them?

If the kernel used to detect hardware, but now doesn't...then it's time to look at:
1) If lots of other with identical hardware are complaining about the same problem (do some searching), it might be a bug in the most recent kernel.
2) Check your hardware connections. It's no longer physically connected to your system.

If you are really sure that it's not the kernel, and you're really sure that it's properly connected, then your hardware may be physically kaput (broken, dead).

---

### Post by dofin on 2015-10-15
Thanks, Ian.

No, I don't see anything Wi-Fi related either with lsusb and lspci.
But since restoring older kernels didn't solve the problem, doesn't this mean that I have to find another explanation?
I hadn't thought of a physical problem. But I have just been able to use Wi-Fi with windows (the computer is dual boot).
Windows lists 2 wifi adapters: Intel Centrino advanced N-6235 and Realtek PCIe GBE family controller.

So it is certainly not a physical problem, and probably not a problem of kernel upgrade. I couldn't find anyone else with the same symptoms...

Update:
Weird: without doing anything (no package update, no change in the config), my wifi is back. In between, I have booted into windows, it might be related.
I will mark this as solved if everything keeps working for a few days.

---


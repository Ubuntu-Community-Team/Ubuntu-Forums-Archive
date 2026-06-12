---
title: "HP dv9000z Broadcom wireless install"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by eldiosyeldiablo on 2007-07-23
I have been trying to get my Broadcom bcm4310 wireless card working but I seem to have an IRQ conflict. I have gone through the tutorials and other postings but cannot find any information on how to resolve the IRQ problem.

Kernel
```
uname -a
Linux laptop-ubuntu 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux
```

lspci
```
03:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 02)

```

dmesg
```
[   36.313916] PCI: setting IRQ 9 as level-triggered
[   36.313919] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK4E] -> GSI 9 (level, low) -> IRQ 9
[   36.313929] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   36.319969] bcm43xx: Unsupported 80211 core revision 13
[   36.321770] bcm43xx: Invalid PHY Revision 9
[   36.419139] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   36.420308] usbcore: registered new interface driver uvcvideo
[   36.420312] USB Video Class driver (v0.1.0)
[   36.661733] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   36.730493] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   36.761397] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 10
[   36.761402] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 10 (level, low) -> IRQ 10
[   36.761433] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   36.809759] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR

```

Addendium: Things that have have tried are fwcutter and ndiswrapper and verified that the wireless works on my Vista install.

Thank you,
-D

---

### Post by gangolli on 2007-07-24
I've successfully used the windows drivers for the card with ndiswrapper in this setting.  You must blacklist bcm43xx when you do so.

---

### Post by eldiosyeldiablo on 2007-07-25
I have followed the steps listed [here]("http://ubuntuforums.org/showthread.php?t=433881") 

But that did not work as seen here...
```
dwilson@laptop-ubuntu:~$ sudo ifup -aPassword:eth1: ERROR while getting interface flags: No such device
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
There is already a pid file /var/run/dhclient.eth1.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

```

lshw -C network
```
dwilson@laptop-ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4310 UART
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:b6000000-b6003fff irq:255
```

---


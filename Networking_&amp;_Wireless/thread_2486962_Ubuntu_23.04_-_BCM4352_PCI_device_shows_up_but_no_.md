---
title: "Ubuntu 23.04 - BCM4352 PCI device shows up but no WiFi interface (wlan0) is created"
date: 2023-05-17
forum: Networking &amp; Wireless
---

### Post by veleek on 2023-05-17
I have an HP T620 that I have freshly install Lubuntu 23.04 onto. I have found the device in “Additional Drivers” and downloaded the drivers successfully. I have rebooted a number of times but the wireless device (wlan0) never shows up so I'm unable to list available networks.
I have also tried the same steps with an Ubuntu Live Disk (23.04) and I get the same problem, so I don't believe it's Lubuntu related.

I installed net-tools and ran ifconfig wlan0 and I get wlan0: error fetching interface information: Device not found. As far as I can tell the device is available, with a driver, but I’m missing a step here somewhere to get it to show up as a regular device and allow me to select a WiFi network.


I dug around as much as I can, and it seems like most of the existing issues with this device (BCM4253) are related to not being able to install the drivers properly.  I have followed the instructions in the [Broadcom Guide]("https://ubuntuforums.org/showthread.php?t=2214110") and I have the correct driver successfully installed.  There is a _SLIGHT_ deviation in that the listed pci.id doesn't say (rev 03).  


System Info: [https://paste.ubuntu.com/p/qT2jj7brWq/](https://paste.ubuntu.com/p/qT2jj7brWq/)
Wireless Info: [https://paste.ubuntu.com/p/hntgZ92sjX/](https://paste.ubuntu.com/p/hntgZ92sjX/)

Is there anything I can do to get it to create a wireless interface for the device?

---

### Post by veleek on 2023-05-17
Ran ```
sudo dmesg | grep "wl\|bcma"
``` and got:

```
[    4.606489] bcma-pci-bridge 0000:01:00.0: enabling device (0100 -> 0102)
[    4.606677] bcma-pci-bridge 0000:01:00.0: bus0: Found chip with id 0x4352, rev 0x03 and package 0x00
[    4.606722] bcma-pci-bridge 0000:01:00.0: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x2B, class 0x0)
[    4.606750] bcma-pci-bridge 0000:01:00.0: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x2A, class 0x0)
[    4.606795] bcma-pci-bridge 0000:01:00.0: bus0: Core 2 found: ARM CR4 (manuf 0x4BF, id 0x83E, rev 0x02, class 0x0)
[    4.606842] bcma-pci-bridge 0000:01:00.0: bus0: Core 3 found: PCIe Gen2 (manuf 0x4BF, id 0x83C, rev 0x01, class 0x0)
[    4.606868] bcma-pci-bridge 0000:01:00.0: bus0: Core 4 found: USB 2.0 Device (manuf 0x4BF, id 0x81A, rev 0x11, class 0x0)
[    4.668443] bcma-pci-bridge 0000:01:00.0: bus0: Bus registered
[   20.961366] wl: loading out-of-tree module taints kernel.
[   20.961387] wl: module license 'MIXED/Proprietary' taints kernel.
[   20.972092] wl: module verification failed: signature and/or required key missing - tainting kernel

```

Other threads I've found seem to indicate that maybe disabling SecureBoot will workaround this but ```
sudo mokutil --sb-state
``` returns ```
SecureBoot disabled
```, so I'm not sure that's the problem.

---


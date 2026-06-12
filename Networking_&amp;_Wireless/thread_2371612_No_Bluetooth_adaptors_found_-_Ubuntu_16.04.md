---
title: "No Bluetooth adaptors found - Ubuntu 16.04"
date: 2017-09-16
forum: Networking &amp; Wireless
---

### Post by ofondo on 2017-09-16
Hi,
I am trying to use my bluetooth module on Ubuntu 16.04
There appears to be Bluetooth hardware on the machine, as determined by:
> dmesg | grep -i blue[ 6455.088044] Bluetooth: Core ver 2.22
[ 6455.088073] Bluetooth: HCI device and connection manager initialized
[ 6455.088077] Bluetooth: HCI socket layer initialized
[ 6455.088079] Bluetooth: L2CAP socket layer initialized
[ 6455.088086] Bluetooth: SCO socket layer initialized

However, Ubuntu does not seem to recognise it in system settings, and running the following command seems to confirm that it is not recognised. 
>sudo lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 2200 (rev c4)

How can I proceed to get my system to recognise the Bluetooth hardware?

---

### Post by jeremy31 on 2017-09-16
The dmesg output occurs even without bluetooth hardware being present.  The product page at Intel's site for the wireless card shows that it didn't have a bluetooth chipset.
Post results for ```
lsusb
```

---

### Post by praseodym on 2017-09-17
...plus
```

usb-devices
lsmod
```

---


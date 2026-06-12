---
title: "AR5007 - ndiswrapper stopped working after package upgrade"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by precursor on 2008-05-06
Hardy 8.04 32bit
Asus Laptop
AR5007eg

Quick Background - I have had hardy installed and working for the past five days or so. I originally installed madwifi drivers, but they broke the suspend on the laptop. I removed those and installed ndiswrapper 1.52 as well as the net5211 drivers posted around here. It all worked perfectly through reboots, shutdowns, suspends, hibernates, etc.

Tonight, I let Synaptics perform an upgrade on all of the new packages for hardy. Sometime after that completed, I rebooted for some other reason. Low and behold on reboot, I have no more working wireless. The card shows up, but it will not scan for networks. 

I have tried removing the driver from ndiswrapper and redoing it. I have tried modprobe -r and then reinstalling the module. I have rebooted numerous times too. ath_pci and ath_hal are in the blacklist.

Here is the output of some commands:


```

lshw -C network
*-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:15:af:57:c6:4f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.52+,11/15/2006,5.1.1.9 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

```

dmesg
[  478.169402] ndiswrapper: device wlan0 removed
[  478.169425] ACPI: PCI interrupt for device 0000:07:00.0 disabled
[  478.169582] usbcore: deregistering interface driver ndiswrapper
[  482.841021] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  482.863064] ndiswrapper: driver net5211 (,11/15/2006,5.1.1.9) loaded
[  482.865254] ACPI: PCI Interrupt 0000:07:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[  482.865317] ndiswrapper (ZwClose:2227): closing handle 0xf75ba028 not implemented
[  482.865741] PCI: Setting latency timer of device 0000:07:00.0 to 64
[  483.049578] ndiswrapper: using IRQ 19
[  483.139007] wlan0: ethernet device 00:15:af:57:c6:4f using serialized NDIS driver: net5211, version: 0x50001, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[  483.146344] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  483.160154] usbcore: registered new interface driver ndiswrapper
[  483.165802] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

```
ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:15:af:57:c6:4f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Memory:fe9f0000-fea00000 
```


```
ndiswrapper -l
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)
```
```

lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

```

lsmod | grep ndis
ndiswrapper           192920  0 
usbcore               146028  5 ndiswrapper,usbhid,ehci_hcd,ohci_hcd
```

```
iwlist wlan0 scanning
wlan0     No scan results

```


Any help would greatly be appreciated

---


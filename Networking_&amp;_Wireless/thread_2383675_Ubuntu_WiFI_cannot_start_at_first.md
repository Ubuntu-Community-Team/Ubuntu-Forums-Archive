---
title: "Ubuntu WiFI cannot start at first"
date: 2018-01-28
forum: Networking &amp; Wireless
---

### Post by ruwan2 on 2018-01-28
Hi,
I install Ubuntu 16.04 as a dual boot with Windows 10 on dell PC. WiFi works great.
After realizing the ubuntu partition was too small, I shrink PC partition, increasing Ubuntu partition with GParted. After these changes, it was found Ubuntu WiFi did not work. On Network Manager GUI, the WiFi signal shows out of range.

After several trials, I found that WiFi can be brought back in two steps.

First at Network Manager, I select Hot Spot. This will connect WiFi as shown on right top small icon. It is connected, but web page cannot open yet. But when I click the right up small WiFi icon, below it the normal WiFi, even the neighbour's are back now. I click my home WiFi, this time it succeeds.

If the computer sleeps, these two steps are also needed.
It works, but annoying for the two steps.

As shown below terminal commands, it does not looks like a hardware identification problem.

Can you find any solution to make it automatically connects to WiFi?


thanks,










```
XPS-8900:~$ sudo lshw -C network
[sudo] password fff: 
  *-network               
       description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 00
       serial: b0:c0:90:bf:ee:73
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=4.13.0-26-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:16 ioport:d000(size=256) memory:df100000-df103fff
  *-network
       description: Ethernet interface
       product: Ethernet Connection (2) I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 31
       serial: 18:66:da:47:da:aa
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.8-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:124 memory:df200000-df21ffff
```
```
XPS-8900:~$ lspci
00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 07)
00:01.0 PCI bridge: Intel Corporation Sky Lake PCIe Controller (x16) (rev 07)
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-H Thermal subsystem (rev 31)
00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
00:17.0 SATA controller: Intel Corporation Sunrise Point-H SATA controller [AHCI mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #1 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (2) I219-V (rev 31)
01:00.0 VGA compatible controller: NVIDIA Corporation GM107 [GeForce GTX 745] (rev a2)
01:00.1 Audio device: NVIDIA Corporation Device 0fbc (rev a1)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter
```

---

### Post by jeremy31 on 2018-01-28
Hotspot mode is a pain, delete it with
```
sudo rm /etc/NetworkManager/system-connections/Hotspot
```
Reboot

---

### Post by ruwan2 on 2018-01-28
It looks like Ubuntu WiFi is erroneously at Hotspot mode after boot up. Is there something can check, to make its default state is wireless client mode?

Thanks,

---


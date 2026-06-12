---
title: "Intel AX201 wifi not working in Ubuntu Server 20.04, kernel 5.4.0-94-generic"
date: 2022-01-18
forum: Networking &amp; Wireless
---

### Post by Cursed Lemon on 2022-01-18
Yes, it's yet another Intel wifi thread. I bought an Acer Nitro 5 laptop recently and thought I'd get cheeky and dual boot Windows with an Ubuntu Server install that I'll turn into an EmulationStation setup. Unfortunately, I can't get the wifi to work. It didn't connect when I was installing Ubuntu Server and it won't connect now either. 

Here's all the relevant information, can provide more if needed. 

**dmesg**: [https://pastebin.ubuntu.com/p/fmjzjxHcbB/](https://pastebin.ubuntu.com/p/fmjzjxHcbB/)

**drv.c**: [https://pastebin.ubuntu.com/p/pSWSH4bCGG/](https://pastebin.ubuntu.com/p/pSWSH4bCGG/)

**/lib/firmware**: [https://pastebin.ubuntu.com/p/NrW2Dz95cz/](https://pastebin.ubuntu.com/p/NrW2Dz95cz/)

**ip a**

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp7s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:8f:c3:12:2b:0b brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.159/24 brd 192.168.1.255 scope global dynamic enp7s0
       valid_lft 7010sec preferred_lft 7010sec
    inet6 fe80::a8f:c3ff:fe12:2b0b/64 scope link 
       valid_lft forever preferred_lft forever
3: wlp0s20f3: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether a0:e7:0b:0f:e8:8a brd ff:ff:ff:ff:ff:ff

```

**netplan**

```
# This is the network config written by 'subiquity'
network:
  version: 2
  renderer: networkd
  wifis:
    wlp0s20f3:
      access-points:
        "SSID":
           password: PASSWORD
      dhcp4: true

```

**lspci**

```
00:00.0 Host bridge: Intel Corporation 10th Gen Core Processor Host Bridge/DRAM Registers (rev 02)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 02)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics (rev 05)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 02)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
00:12.0 Signal processing controller: Intel Corporation Comet Lake PCH Thermal Controller
00:14.0 USB controller: Intel Corporation Comet Lake USB 3.1 xHCI Host Controller
00:14.2 RAM memory: Intel Corporation Comet Lake PCH Shared SRAM
00:14.3 Network controller: Intel Corporation Wi-Fi 6 AX201
00:15.0 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH Serial IO I2C Controller #0
00:15.1 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH Serial IO I2C Controller #1
00:16.0 Communication controller: Intel Corporation Comet Lake HECI Controller
00:17.0 SATA controller: Intel Corporation Device 06d3
00:1b.0 PCI bridge: Intel Corporation Comet Lake PCI Express Root Port #21 (rev f0)
00:1d.0 PCI bridge: Intel Corporation Device 06b5 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Comet Lake LPC Controller
00:1f.3 Audio device: Intel Corporation Comet Lake PCH cAVS
00:1f.4 SMBus: Intel Corporation Comet Lake PCH SMBus Controller
00:1f.5 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH SPI Controller
01:00.0 VGA compatible controller: NVIDIA Corporation Device 25a5 (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 2291 (rev a1)
06:00.0 Non-Volatile memory controller: Sandisk Corp Device 5009 (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Device 2600 (rev 21)

```

**sudo lshw -C network**

```
  *-network
       description: Wireless interface
       product: Wi-Fi 6 AX201
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       logical name: wlp0s20f3
       version: 00
       serial: a0:e7:0b:0f:e8:8a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.4.0-94-generic firmware=50.3e391d3e.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: iomemory:610-60f irq:16 memory:610310c000-610310ffff
  *-network
       description: Ethernet interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: enp7s0
       version: 21
       serial: 08:8f:c3:12:2b:0b
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=192.168.1.159 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:17 ioport:3000(size=256) memory:a1104000-a1104fff memory:a1100000-a1103fff

```

---

### Post by chili555 on 2022-01-18
Are net-tools and wpasupplicant installed?

```
sudo dpkg -s net-tools | grep Status
sudo dpkg -s wpasupplicant | grep Status
```

Please see: ```
cat /usr/share/doc/netplan/examples/wireless.yaml

```It appears that you have a slight indentation misplacement in the password. As well, in the example, the password in enclosed in quotes ". Please correct these items and follow with:

```
sudo netplan generate
sudo netplan apply
```Next, show us:

```
sudo dmesg | grep wlp
iwconfig
```

---

### Post by Cursed Lemon on 2022-01-18
> **chili555 said:**
> Are net-tools and wpasupplicant installed?

```
sudo dpkg -s net-tools | grep Status
sudo dpkg -s wpasupplicant | grep Status
```

Please see: ```
cat /usr/share/doc/netplan/examples/wireless.yaml

```It appears that you have a slight indentation misplacement in the password. As well, in the example, the password in enclosed in quotes ". Please correct these items and follow with:

```
sudo netplan generate
sudo netplan apply
```Next, show us:

```
sudo dmesg | grep wlp
iwconfig
```

I actually figured it out! I was attempting to connect to a hidden SSID and apparently you have to specify "hidden: true" in the netplan config, which I wasn't aware of. Made that tweak and now I've got a connection.

---

### Post by chili555 on 2022-01-18
Awesome! Please use thread tools to mark Solved. The searchers will appreciate it.

---


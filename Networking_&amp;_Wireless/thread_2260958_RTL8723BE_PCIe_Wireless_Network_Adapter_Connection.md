---
title: "RTL8723BE PCIe Wireless Network Adapter Connection dropping in Ubuntu 14.04"
date: 2015-01-15
forum: Networking &amp; Wireless
---

### Post by rakesh343 on 2015-01-15
I have just bought Lenovo G50-70 Series laptop. Its wireless connection is dropping after about 1/2 an hour - 1 hour from starting the computer. I'm using Ubuntu 14.04 LTS distro. The relevant information is the following:

1. The results of running the wireless script is attached in the file.

2. Results of running the commands is given below:

```
lspci
```

00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter


```
pkexec kill -9 'pidoff NetworkManager'
```

kill: failed to parse argument: 'pidoff NetworkManager'

```
sudo service network-manager restart
```

[sudo] password for yayavar:
network-manager stop/waiting
network-manager start/running, process 4008

```
sudo rmmod rtl8723be && modprobe rtl8723be
```

modprobe: ERROR: could not insert 'rtl8723be': Operation not permitted

```
sudo modprobe-r rtl8723be && modprobe rtl8723be
```

sudo: modprobe-r: command not found


Please help. I need to reesolve this issue soon, or else I have to return my laptop soon. Please help.:mad:

---


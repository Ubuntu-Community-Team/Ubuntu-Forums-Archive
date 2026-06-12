---
title: "Ethernet does not work, but wifi does"
date: 2015-12-21
forum: Networking &amp; Wireless
---

### Post by myelemes on 2015-12-21
Hello everyone,

I am running Ubuntu 14.04 LTS

I have a problem, my ethernet does not work, but my wifi does. My work depends on a very reliable connection, thus I need the ethernet to work.
I use a USB 3.0 Gigabit Ethernet Adapter with my laptop. Everything worked before very well.

I read previous threads concerning my problem, but they did not help to solve my problem. Here are some of the outputs from my terminal

```
**~$ sudo ifconfig -a**
eth1      Link encap:Ethernet  HWaddr 00:e0:4c:68:01:0f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:36881 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36881 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23524180 (23.5 MB)  TX bytes:23524180 (23.5 MB)


wlan0     Link encap:Ethernet  HWaddr 30:3a:64:96:cf:cb  
          inet addr:146.95.217.81  Bcast:146.95.219.255  Mask:255.255.252.0
          inet6 addr: fe80::323a:64ff:fe96:cfcb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:208213 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9798 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32661097 (32.6 MB)  TX bytes:2082592 (2.0 MB)
```

```
**~$ lspci**
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.1 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 2 (rev e4)
00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1c.4 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 5 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5249 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
04:00.0 Network controller: Intel Corporation Wireless 3160 (rev 93)
05:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Venus XTX [Radeon HD 8890M] (rev ff)
```

```
**~$ sudo ifup eth0**
Ignoring unknown interface eth0=eth0.
```

```
**~$ cat /etc/network/interfaces**
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

```
**~$ dmesg | grep -e eth0 -e bcm**
[   14.319393] r8152 2-1:1.0 eth0: v1.07.0 (2014/10/09)
[   14.320167] r8152 2-1:1.0 eth1: renamed from eth0
[   14.337601] systemd-udevd[364]: renamed network interface eth0 to eth1
[10865.809682] r8152 2-1:1.0 eth0: v1.07.0 (2014/10/09)
[10866.345659] r8152 2-1:1.0 eth1: renamed from eth0
[10866.363976] systemd-udevd[4095]: renamed network interface eth0 to eth1
```


```
**~$ sudo lshw -C Network**
  *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0
       resources: ioport:4000(size=256) memory:c0604000-c0604fff memory:c0600000-c0603fff
  *-network
       description: Wireless interface
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 93
       serial: 30:3a:64:96:cf:cb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.19.0-42-generic firmware=25.17.12.0 ip=146.95.217.81 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:49 memory:c0500000-c0501fff
  *-network
       description: Ethernet interface
       physical id: 3
       logical name: eth1
       serial: 00:e0:4c:68:01:0f
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.07.0 (2014/10/09) duplex=full link=no multicast=yes port=MII speed=1Gbit/s
```


```
**~$ lspci -nn**
00:00.0 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 0b)
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 0b)
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 0b)
00:14.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB xHCI HC [8086:9c31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation Lynx Point-LP HECI #0 [8086:9c3a] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Lynx Point-LP HD Audio Controller [8086:9c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 1 [8086:9c10] (rev e4)
00:1c.1 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 2 [8086:9c12] (rev e4)
00:1c.2 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 3 [8086:9c14] (rev e4)
00:1c.3 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 4 [8086:9c16] (rev e4)
00:1c.4 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 5 [8086:9c18] (rev e4)
00:1d.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB EHCI #1 [8086:9c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Lynx Point-LP LPC Controller [8086:9c43] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] [8086:9c03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Lynx Point-LP SMBus Controller [8086:9c22] (rev 04)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5249] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
04:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b4] (rev 93)
05:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Venus XTX [Radeon HD 8890M] [1002:6820] (rev ff)
```

---

### Post by praseodym on 2015-12-21
For the internal LAN-PCI card install the right driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget https://media-cdn.ubuntu-de.org/forum/attachments/04/50/3005217-r8168-dkms-8.041.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.041.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.041.00
sudo dkms build -m r8168-dkms -v 8.041.00
sudo dkms install -m r8168-dkms -v 8.041.00
sudo depmod -a
sudo update-initramfs -u
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot

---

### Post by myelemes on 2016-01-04
Hi, I followed all of the above mentioned instructions, but I still can't connect to the internet via ethernet.

here is some more

02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5249 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
04:00.0 Network controller: Intel Corporation Wireless 3160 (rev 93)

---

### Post by myelemes on 2016-01-10
reinstalled ubuntu, could not wait longer

---


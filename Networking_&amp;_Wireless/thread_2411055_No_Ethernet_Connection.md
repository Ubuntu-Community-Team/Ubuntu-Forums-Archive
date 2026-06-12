---
title: "No Ethernet Connection"
date: 2019-01-24
forum: Networking &amp; Wireless
---

### Post by phh on 2019-01-24
We have Ubuntu 18.04 with Budgie Desktop installed on a PC.

Until very recently we have had an active wired connection to the Internet.

Now, suddenly, our Ethernet connection is gone.

ifconfig does not even see an Ethernet device.

Currently, we are using a usb wifi adaptor for Internet connection.

Anyone know what our problem is?

---

### Post by TheFu on 2019-01-24
Facts needed please.  Run commands and post both the exact command run and the output, using _code tags_, so things line up correctly.
```

$ ip a
$ route -n
$ sudo lshw -C network
```

That should get us some basic facts.

---

### Post by phh on 2019-01-25
See code below as requested:

```
~$ **ip a**
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: wlxec086b1ce75c: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether ec:08:6b:1c:e7:5c brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.117/24 brd 192.168.1.255 scope global dynamic noprefixroute wlxec086b1ce75c
       valid_lft 85762sec preferred_lft 85762sec
    inet6 fe80::2f80:c112:b41:d2f3/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

~$ **route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlxec086b1ce75c
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlxec086b1ce75c

~$ **sudo lshw -C network**
[sudo] password for *******: 
  *-network                 
       description: Wireless interface
       physical id: 2
       bus info: usb@3:5.2
       logical name: wlxec086b1ce75c
       serial: ec:08:6b:1c:e7:5c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8188eu ip=192.168.1.117 multicast=yes wireless=IEEE 802.11bgn

```

---

### Post by TheFu on 2019-01-25
What all that tells me is that the wired ethernet device isn't recognized at all. It is either broken, disabled, or no drivers exist. 

 If it worked previously, I'd say it is fried.  Time to go into the BIOS and disable it (or check that it isn't disabled already), and buy an addon card from Intel for $25.

---

### Post by praseodym on 2019-01-25
Please show the output of
```

lspci -nnk
```

---

### Post by phh on 2019-01-29
**~$ lspci -nnk**
```

00:00.0 Host bridge [0600]: Intel Corporation 4th Gen Core Processor DRAM Controller [8086:0c00] (rev 06)
	Subsystem: Gigabyte Technology Co., Ltd 4th Gen Core Processor DRAM Controller [1458:5000]
	Kernel driver in use: hsw_uncore
00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Generation Core Processor Family Integrated Graphics Controller [8086:041e] (rev 06)
	Subsystem: Gigabyte Technology Co., Ltd 4th Generation Core Processor Family Integrated Graphics Controller [1458:d000]
	Kernel driver in use: i915
	Kernel modules: i915
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
	Subsystem: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:2010]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
00:14.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI [8086:8c31] (rev 05)
	Subsystem: Gigabyte Technology Co., Ltd 8 Series/C220 Series Chipset Family USB xHCI [1458:5007]
	Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 [8086:8c3a] (rev 04)
	Subsystem: Gigabyte Technology Co., Ltd 8 Series/C220 Series Chipset Family MEI Controller [1458:1c3a]
	Kernel driver in use: mei_me
	Kernel modules: mei_me
00:1a.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 [8086:8c2d] (rev 05)
	Subsystem: Gigabyte Technology Co., Ltd 8 Series/C220 Series Chipset Family USB EHCI [1458:5006]
	Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller [8086:8c20] (rev 05)
	Subsystem: Gigabyte Technology Co., Ltd 8 Series/C220 Series Chipset High Definition Audio Controller [1458:a002]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 [8086:8c10] (rev d5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 [8086:8c14] (rev d5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 [8086:8c16] (rev d5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 [8086:8c26] (rev 05)
	Subsystem: Gigabyte Technology Co., Ltd 8 Series/C220 Series Chipset Family USB EHCI [1458:5006]
	Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation C220 Series Chipset Family H81 Express LPC Controller [8086:8c5c] (rev 05)
	Subsystem: Gigabyte Technology Co., Ltd C220 Series Chipset Family H81 Express LPC Controller [1458:5001]
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] [8086:8c02] (rev 05)
	Subsystem: Gigabyte Technology Co., Ltd 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] [1458:b005]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller [8086:8c22] (rev 05)
	Subsystem: Gigabyte Technology Co., Ltd 8 Series/C220 Series Chipset Family SMBus Controller [1458:5001]
	Kernel driver in use: i801_smbus
	Kernel modules: i2c_i801
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet [1458:e000]
	Kernel driver in use: r8169
	Kernel modules: r8169
03:00.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 41)
```

---

### Post by phh on 2019-01-29
Kernel driver in use r8169?

Shouldn't this be r8168?

---

### Post by TheFu on 2019-01-29
For some r8168 NICs, the r8168 driver works better.  For others, the r8169 work better.
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1782608](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1782608) shows that disagreement.

If you search these forums for **RTL8111/8168/8411 driver** you'll find multiple other threads which walked people through fixing it.

The short answer is  to **blacklist  r8169** module and 
```
sudo apt-get install r8168-dkms
```

---

### Post by phh on 2019-01-30
Thank you all for your interest in my problem.

TheFu's solution worked. I did the blacklist, installed the old r8168 driver, wired connection is now back again.

Many thanks again.

---

### Post by praseodym on 2019-01-30
BTW: r8168 is not old. Realtek meanwhile provides yearly updates on it

[https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software](https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software)

---


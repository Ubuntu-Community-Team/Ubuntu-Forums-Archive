---
title: "Ubuntu 15.10 on HP ProBook 470 G1 wifi won't work"
date: 2016-03-08
forum: Networking &amp; Wireless
---

### Post by pikulskiy on 2016-03-08
Hi there!
I've recently installed Ubuntu 15.10 on my HP notebook and I can't get my wi-fi working. Can someone help me to fix the problem?
After running **_ifconfig_** :
```

enp3s0    Link encap:Ethernet  HWaddr a0:1d:48:ac:da:c2  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a21d:48ff:feac:dac2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5000 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7082263 (7.0 MB)  TX bytes:543403 (543.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1045 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1045 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:99806 (99.8 KB)  TX bytes:99806 (99.8 KB)


```

---

### Post by jeremy31 on 2016-03-08
Post ```
lspci -nnk | grep -iA2 net; lsusb; lshw -c net
```

---

### Post by pikulskiy on 2016-03-08
The results are:[U][B]
lspci -nnk | grep -iA2 net
[/B][/U]```

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Hewlett-Packard Company Device [103c:1944]
    Kernel driver in use: r8169
04:00.0 Network controller [0280]: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter [14c3:7630]
    DeviceName: WLAN
    Subsystem: Hewlett-Packard Company Device [103c:197c]

```[U][B]
lsusb
[/B][/U]```

Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b3c8 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 138a:003f Validity Sensors, Inc. VFS495 Fingerprint Reader
Bus 001 Device 004: ID 0e8d:763e MediaTek Inc. MT7630e Bluetooth Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
[U][B]lshw -c net
[/B][/U]```

 *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 0c
       serial: a0:1d:48:ac:da:c2
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.0.100 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:32 ioport:3000(size=256) memory:b0700000-b0700fff memory:b0400000-b0403fff
  *-network UNCLAIMED
       description: Network controller
       product: MT7630e 802.11bgn Wireless Network Adapter
       vendor: MEDIATEK Corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:b0600000-b06fffff

```

---

### Post by jeremy31 on 2016-03-08
This should work
```
sudo apt-get install --reinstall git linux-headers-$(uname -r) build-essential dkms
git clone https://github.com/neurobin/MT7630E/
cd MT7630E/
make
sudo make install
```

Reboot

[http://ubuntuforums.org/showthread.php?t=2300107](http://ubuntuforums.org/showthread.php?t=2300107)

It has dkms so you could do it that way and not have to recompile after every kernel update
```
sudo apt-get install --reinstall git linux-headers-$(uname -r) build-essential dkms
git clone https://github.com/neurobin/MT7630E/
sudo dkms add ./MT7630E
sudo dkms install mt7630e/2.0.3
```

Reboot

---

### Post by pikulskiy on 2016-03-08
Thanks, everything works great! :)

---

### Post by jeremy31 on 2016-03-08
If you used the first option instead of the second option, you will lose wireless after a kernel update and need to
```
cd MT7630E/
make clean
make
sudo make install
```

Reboot

If you used the sudo dkms commands, it will update when the new kernel is installing

---


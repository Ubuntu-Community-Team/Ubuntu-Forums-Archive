---
title: "TP-LINK TG-3269 installation woes"
date: 2017-07-16
forum: Networking &amp; Wireless
---

### Post by AtomicPenguin on 2017-07-16
I'm trying to install this gigabit NIC on a PC running Ubuntu Server 16.04.2.  The machine currently has a 10/100 NIC in it.   I've copied the driver fold/files into my home folder but I'm getting errors when trying to run the first command as detailed in the README file.

The README file states...

```
If you are running the target kernel, then you should be
  able to do :

        make clean modules      (as root or with sudo)
        make install
        depmod -a
```
However when I run the first command as sudo I get...
```

make -C src/ clean
make[1]: Entering directory '/home/jason/downloads/driver/src'
Makefile:28: /src/Makefile_linux26x: No such file or directory
make[1]: *** No rule to make target '/src/Makefile_linux26x'.  Stop.
make[1]: Leaving directory '/home/jason/downloads/driver/src'
Makefile:11: recipe for target 'clean' failed
make: *** [clean] Error 2

```

I've done quite a bit of searches directly here and through google and unfortunately haven't been able to get very far.  I'm working via CLI only.

My output of 'lspci' shows...

```

01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller (rev 10)

```

---

### Post by praseodym on 2017-07-16
Maybe that driver is too old? Module r8169 is already part of the package "linux-image-extra" to the respective kernel
```

modinfo r8169
```

---

### Post by AtomicPenguin on 2017-07-16
I tried downloading the driver from TP-LINK's site but I get the same thing.  Also from the date/time stamps and file sizes it appears to be the same files inside the archive.

```

ifconfig -a

```

...gives me...

```

enp0s7    Link encap:Ethernet  HWaddr 00:1f:d0:df:b7:5b
          inet addr:192.168.1.135  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fdca:8b83:8fac:0:21f:d0ff:fedf:b75b/64 Scope:Global
          inet6 addr: fe80::21f:d0ff:fedf:b75b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13470466 (13.4 MB)  TX bytes:14594862 (14.5 MB)

enp1s6    Link encap:Ethernet  HWaddr d4:6e:0e:00:8e:1a
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

The first one 'enp0s7' is my 10/100 card which is currently being used.  Without the '-a' option on 'ifconfig' I don't get the listing for 'enp1s6'.

---

### Post by praseodym on 2017-07-17
Lets check
```

lspci -nnk
lsusb
lsmod
```

---

### Post by AtomicPenguin on 2017-07-17
lspci -nnk
```

00:00.0 RAM memory [0500]: NVIDIA Corporation MCP61 Memory Controller [10de:03ea] (rev a1)
        Subsystem: Gigabyte Technology Co., Ltd MCP61 Memory Controller [1458:5001]
00:01.0 ISA bridge [0601]: NVIDIA Corporation MCP61 LPC Bridge [10de:03e0] (rev a2)
        Subsystem: Gigabyte Technology Co., Ltd MCP61 LPC Bridge [1458:0c11]
00:01.1 SMBus [0c05]: NVIDIA Corporation MCP61 SMBus [10de:03eb] (rev a2)
        Subsystem: Gigabyte Technology Co., Ltd MCP61 SMBus [1458:0c11]
        Kernel driver in use: nForce2_smbus
        Kernel modules: i2c_nforce2
00:01.2 RAM memory [0500]: NVIDIA Corporation MCP61 Memory Controller [10de:03f5] (rev a2)
        Subsystem: Gigabyte Technology Co., Ltd MCP61 Memory Controller [1458:0c11]
00:02.0 USB controller [0c03]: NVIDIA Corporation MCP61 USB 1.1 Controller [10de:03f1] (rev a3)
        Subsystem: Gigabyte Technology Co., Ltd MCP61 USB 1.1 Controller [1458:5004]
        Kernel driver in use: ohci-pci
00:02.1 USB controller [0c03]: NVIDIA Corporation MCP61 USB 2.0 Controller [10de:03f2] (rev a3)
        Subsystem: Gigabyte Technology Co., Ltd MCP61 USB 2.0 Controller [1458:5004]
        Kernel driver in use: ehci-pci
00:04.0 PCI bridge [0604]: NVIDIA Corporation MCP61 PCI bridge [10de:03f3] (rev a1)
00:06.0 IDE interface [0101]: NVIDIA Corporation MCP61 IDE [10de:03ec] (rev a2)
        Subsystem: Gigabyte Technology Co., Ltd MCP61 IDE [1458:5002]
        Kernel driver in use: pata_amd
        Kernel modules: pata_amd, pata_acpi
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
        Subsystem: Gigabyte Technology Co., Ltd MCP61 Ethernet [1458:e000]
        Kernel driver in use: forcedeth
        Kernel modules: forcedeth
00:08.0 IDE interface [0101]: NVIDIA Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
        Subsystem: Gigabyte Technology Co., Ltd MCP61 SATA Controller [1458:b002]
        Kernel driver in use: sata_nv
        Kernel modules: sata_nv, pata_acpi
00:0d.0 VGA compatible controller [0300]: NVIDIA Corporation C61 [GeForce 6150SE nForce 430] [10de:03d0] (rev a2)
        Subsystem: Gigabyte Technology Co., Ltd C61 [GeForce 6150SE nForce 430] [1458:d000]
        Kernel driver in use: nouveau
        Kernel modules: nvidiafb, nouveau
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
        Kernel modules: amd64_edac_mod
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
        Kernel driver in use: k8temp
        Kernel modules: k8temp
01:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller [10ec:8169] (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL8169/8110 Family PCI Gigabit Ethernet NIC [10ec:8169]
        Kernel driver in use: r8169
        Kernel modules: r8169

```

lsusb
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

lsmod

```

Module                  Size  Used by
ppdev                  20480  0
kvm                   544768  0
irqbypass              16384  1 kvm
serio_raw              16384  0
k8temp                 16384  0
edac_mce_amd           24576  0
edac_core              53248  0
8250_fintek            16384  0
i2c_nforce2            16384  0
parport_pc             32768  0
parport                49152  2 ppdev,parport_pc
mac_hid                16384  0
ib_iser                49152  0
rdma_cm                49152  1 ib_iser
iw_cm                  45056  1 rdma_cm
ib_cm                  45056  1 rdma_cm
ib_sa                  36864  2 rdma_cm,ib_cm
ib_mad                 49152  2 ib_cm,ib_sa
ib_core               106496  6 rdma_cm,ib_cm,ib_sa,iw_cm,ib_mad,ib_iser
ib_addr                16384  2 rdma_cm,ib_core
iscsi_tcp              20480  0
libiscsi_tcp           24576  1 iscsi_tcp
libiscsi               53248  3 libiscsi_tcp,iscsi_tcp,ib_iser
scsi_transport_iscsi    98304  4 iscsi_tcp,ib_iser,libiscsi
autofs4                40960  2
btrfs                 987136  0
raid10                 49152  0
raid456               110592  0
async_raid6_recov      20480  1 raid456
async_memcpy           16384  2 raid456,async_raid6_recov
async_pq               16384  2 raid456,async_raid6_recov
async_xor              16384  3 async_pq,raid456,async_raid6_recov
async_tx               16384  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
xor                    24576  2 btrfs,async_xor
raid6_pq              102400  4 async_pq,raid456,btrfs,async_raid6_recov
libcrc32c              16384  1 raid456
raid1                  36864  0
raid0                  20480  0
multipath              16384  0
linear                 16384  0
pata_acpi              16384  0
nouveau              1495040  1
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau
video                  40960  1 nouveau
i2c_algo_bit           16384  1 nouveau
ttm                    98304  1 nouveau
drm_kms_helper        155648  1 nouveau
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   364544  4 ttm,drm_kms_helper,nouveau
r8169                  81920  0
psmouse               131072  0
sata_nv                32768  3
pata_amd               20480  0
forcedeth              69632  0
mii                    16384  1 r8169
fjes                   28672  0

```

---

### Post by praseodym on 2017-07-17
Drivers are there, r8169 for the Realtek NIC and forcedeth for the NVIDIA NIC. Please check
```

ifconfig -a
sudo apt-get install ethtool
```
Check also
```

sudo ethtool -s $NIC-Name #with both $NIC-name being shown in 'ifconfig -a'
```

---

### Post by AtomicPenguin on 2017-07-17
ifconfig -a
```

enp0s7    Link encap:Ethernet  HWaddr 00:1f:d0:df:b7:5b
          inet addr:192.168.1.135  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fdca:8b83:8fac:0:21f:d0ff:fedf:b75b/64 Scope:Global
          inet6 addr: fe80::21f:d0ff:fedf:b75b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1302998 errors:0 dropped:0 overruns:0 frame:0
          TX packets:846464 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1556408054 (1.5 GB)  TX bytes:164001871 (164.0 MB)

enp1s6    Link encap:Ethernet  HWaddr d4:6e:0e:00:8e:1a
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:226751 errors:0 dropped:0 overruns:0 frame:0
          TX packets:226751 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:179098009 (179.0 MB)  TX bytes:179098009 (179.0 MB)

```

I get no message when running the 'ethtool' command on either NIC.

---

### Post by chili555 on 2017-07-17
If you switch the ethernet cable to the other port, presumably the Realtek, and then do:```
sudo dhclient -v enp1s6
```What is the exact result?

---

### Post by BenginM on 2017-07-17
Chea! as praseodym said , the kernel driver module is loaded .. i wounder if the firmware is missing , or..!

what is the base kernel current;y in use , #see $ uname -a

what does 

dmesg | grep r8169 

returns!

in my dekstop i get :

```


[COLOR=#000080]sm@tru:~$ dmesg | grep r8169
[    3.083803] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.083824] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    3.087016] r8169 0000:03:00.0 eth0: RTL8105e at 0xffffc9000066d000, e8:9a:8f:9c:fd:9a, XID 00a00000 IRQ 24
[    3.165153] r8169 0000:03:00.0 enp3s0: renamed from eth0
[   27.337699] r8169 0000:03:00.0 enp3s0: link down
sm@tru:~$ [/COLOR]


```

---

### Post by AtomicPenguin on 2017-07-17
sudo dhclient -v enp1s6

It grabbed an IP from the router.

```

Internet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/enp1s6/d4:6e:0e:00:8e:1a
Sending on   LPF/enp1s6/d4:6e:0e:00:8e:1a
Sending on   Socket/fallback
DHCPDISCOVER on enp1s6 to 255.255.255.255 port 67 interval 3 (xid=0x8057491a)
DHCPDISCOVER on enp1s6 to 255.255.255.255 port 67 interval 8 (xid=0x8057491a)
DHCPREQUEST of 192.168.1.102 on enp1s6 to 255.255.255.255 port 67 (xid=0x1a495780)
DHCPOFFER of 192.168.1.102 from 192.168.1.1
DHCPACK of 192.168.1.102 from 192.168.1.1
bound to 192.168.1.102 -- renewal in 38105 seconds.

```

ifconfig

```

enp0s7    Link encap:Ethernet  HWaddr 00:1f:d0:df:b7:5b
          inet addr:192.168.1.135  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fdca:8b83:8fac:0:21f:d0ff:fedf:b75b/64 Scope:Global
          inet6 addr: fe80::21f:d0ff:fedf:b75b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1309632 errors:0 dropped:0 overruns:0 frame:0
          TX packets:849703 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1558698911 (1.5 GB)  TX bytes:164511287 (164.5 MB)

enp1s6    Link encap:Ethernet  HWaddr d4:6e:0e:00:8e:1a
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d66e:eff:fe00:8e1a/64 Scope:Link
          inet6 addr: fdca:8b83:8fac:0:d66e:eff:fe00:8e1a/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5854 (5.8 KB)  TX bytes:9003 (9.0 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:232416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:232416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:180922972 (180.9 MB)  TX bytes:180922972 (180.9 MB)

```

---

### Post by AtomicPenguin on 2017-07-17
After it grabbed an IP, I rebooted the system and upon reboot it did not have an IP address and the interface was once again unavailable.


dmesg | grep r8169 

```

[    1.344283] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.347141] r8169 0000:01:06.0 (unnamed net_device) (uninitialized): not PCI Express
[    1.350140] r8169 0000:01:06.0 eth0: RTL8169sb/8110sb at 0xffffc90000006000, d4:6e:0e:00:8e:1a, XID 10000000 IRQ 16
[    1.352470] r8169 0000:01:06.0 eth0: jumbo features [frames: 7152 bytes, tx checksumming: ok]
[    1.455430] r8169 0000:01:06.0 enp1s6: renamed from eth0

```

---

### Post by chili555 on 2017-07-17
> Listening on LPF/enp1s6/d4:6e:0e:00:8e:1a
Sending on   LPF/enp1s6/d4:6e:0e:00:8e:1a
Sending on   Socket/fallback
DHCPDISCOVER on enp1s6 to 255.255.255.255 port 67 interval 3 (xid=0x8057491a)
DHCPDISCOVER on enp1s6 to 255.255.255.255 port 67 interval 8 (xid=0x8057491a)
DHCPREQUEST of 192.168.1.102 on enp1s6 to 255.255.255.255 port 67 (xid=0x1a495780)
DHCPOFFER of 192.168.1.102 from 192.168.1.1
DHCPACK of 192.168.1.102 from 192.168.1.1
bound to 192.168.1.102 -- renewal in 38105 seconds.So it's working perfectly well. All you need do next is decide which you want to use, configure it in /etc/network/interfaces and enjoy.

Post back if you need additional guidance.

---

### Post by AtomicPenguin on 2017-07-17
This is what's currently in the 'interfaces' file.

```



# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo enp0s7
iface lo inet loopback

# The primary network interface
iface enp0s7 inet dhcp
# This is an autoconfigured IPv6 interface

```

Do I just change the NIC name to the new NIC's name I'm trying to use?

---

### Post by chili555 on 2017-07-17
> Do I just change the NIC name to the new NIC's name I'm trying to use?No. I recommend a static IP address for a server so that you can ssh and ftp into it. If you use DHCP, the address is likely to change from time to time.

I suggest the following, adjusted, of course to suit your network:

```
auto lo
iface lo inet loopback

auto enp1s6
iface enp1s6 inet static
address 192.168.1.150
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1
```
Save the file and quit vim or nano or your favorite text editor. Be sure to use an IP address outside the range of the DHCP pool in the router so as to avoid collisions. Get the system to read and use the changes:

```
sudo ifdown enp1s6 && sudo ifup -v enp1s6
```
Check:

```
ping -c3 www.google.com
```
If you get ping returns, you are all set.

---

### Post by AtomicPenguin on 2017-07-17
Working like a charm now!  Thanks everyone for the help!

---

### Post by chili555 on 2017-07-17
> **AtomicPenguin said:**
> Working like a charm now!  Thanks everyone for the help!Wonderful! Please use thread tools at the top to slap a big old 'Solved' on the thread. The searchers will appreciate it.

---

### Post by AtomicPenguin on 2017-07-17
Got it!

---


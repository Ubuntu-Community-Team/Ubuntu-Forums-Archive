---
title: "Ethernet connection says &quot;cable unplugged&quot;, new installation of Ubuntu 20.04?"
date: 2020-11-18
forum: Networking &amp; Wireless
---

### Post by mysteriousmonkey29 on 2020-11-18
Hello, I recently installed ubuntu 20.04 on an MSI GS66 Stealth, running kernel 5.4.0-53-generic.

The wifi is working fine, but the ethernet says "cable unplugged" even when I plug in an ethernet cable connected to my router. This same connection is working on my old computer, running, ubuntu 18.04, so I don't think it is a hardware issue.

ifconfig -a returns:

```

enx54bf643fb650: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 54:bf:64:3f:b6:50  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 6477  bytes 757684 (757.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6477  bytes 757684 (757.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.131  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fd00:58ef:6881:1052:89a3:5662:3a9:9dcd  prefixlen 64  scopeid 0x0<global>
        inet6 fd00:58ef:6881:1052:a2b7:1fa0:e04a:1113  prefixlen 64  scopeid 0x0<global>
        inet6 fd00:58ef:6881:1051:89a3:5662:3a9:9dcd  prefixlen 64  scopeid 0x0<global>
        inet6 fd00:58ef:6881:1051:a894:12df:5322:c883  prefixlen 64  scopeid 0x0<global>
        inet6 2600:8801:c300:e95:2b6c:1a3:8742:5462  prefixlen 64  scopeid 0x0<global>
        inet6 2600:8801:c300:e95:89a3:5662:3a9:9dcd  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::c9c0:b238:bb72:c5b5  prefixlen 64  scopeid 0x20<link>
        ether 9c:29:76:f1:c4:4e  txqueuelen 1000  (Ethernet)
        RX packets 1524156  bytes 1300251430 (1.3 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 348946  bytes 49962533 (49.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

Which looks a little weird to me. I think the first one should read "eth0". I looked up other people with similar issues, which suggested adjusting the interfaces file in /etc/network. Unfortunately I have no such file. Maybe this is an ubuntu version thing? Most of what I found was for previous versions of ubuntu.

Help would be much appreciated!

Thanks

---

### Post by Raffles727 on 2020-11-20
Please try ```
lspci
``` and post the results.

---

### Post by grahammechanical on 2020-11-20
Ubuntu is built on Debian and when Debian included something called systemd then Ubuntu went over to systemd. This link will explain why an ethernet adapter is no longer called eth0 but en ... something something.

[https://cgit.freedesktop.org/systemd/systemd/tree/src/udev/udev-builtin-net_id.c#n20](https://cgit.freedesktop.org/systemd/systemd/tree/src/udev/udev-builtin-net_id.c#n20)

My two ethernet adapters are enp2s0 and enp6s4. My WiFi adapter is wlx0015af0e9be0. It all makes sense to the Redhat developers who designed systemd. When you compare 18.04 with 20.04 are you using the same ethernet cable? One of my ethernet adapters has the cable unplugged message but I know that the cable is faulty.

Regards.

---

### Post by mysteriousmonkey29 on 2020-11-23
> **Raffles727 said:**
> Please try ```
lspci
``` and post the results.

```
00:00.0 Host bridge: Intel Corporation 10th Gen Core Processor Host Bridge/DRAM Registers (rev 02)
00:01.0 PCI bridge: Intel Corporation 6th-9th Gen Core Processor PCIe Controller (x16) (rev 02)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics (rev 05)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 02)
00:12.0 Signal processing controller: Intel Corporation Comet Lake PCH Thermal Controller
00:14.0 USB controller: Intel Corporation Comet Lake USB 3.1 xHCI Host Controller
00:14.2 RAM memory: Intel Corporation Comet Lake PCH Shared SRAM
00:14.3 Network controller: Intel Corporation Comet Lake PCH CNVi WiFi
00:15.0 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH Serial IO I2C Controller #0
00:15.2 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH Serial IO I2C Controller #2
00:16.0 Communication controller: Intel Corporation Comet Lake HECI Controller
00:1b.0 PCI bridge: Intel Corporation Comet Lake PCI Express Root Port #17 (rev f0)
00:1d.0 PCI bridge: Intel Corporation Comet Lake PCI Express Root Port #9 (rev f0)
00:1d.6 PCI bridge: Intel Corporation Device 06b6 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Comet Lake LPC Controller
00:1f.3 Audio device: Intel Corporation Comet Lake PCH cAVS
00:1f.4 SMBus: Intel Corporation Comet Lake PCH SMBus Controller
00:1f.5 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH SPI Controller
01:00.0 VGA compatible controller: NVIDIA Corporation TU106M [GeForce RTX 2060 Mobile] (rev a1)
01:00.1 Audio device: NVIDIA Corporation TU106 High Definition Audio Controller (rev a1)
01:00.2 USB controller: NVIDIA Corporation TU106 USB 3.1 Host Controller (rev a1)
01:00.3 Serial bus controller [0c80]: NVIDIA Corporation TU106 USB Type-C UCSI Controller (rev a1)
02:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
03:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
03:01.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
03:02.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
04:00.0 System peripheral: Intel Corporation JHL7540 Thunderbolt 3 NHI [Titan Ridge 2C 2018] (rev 06)
3a:00.0 USB controller: Intel Corporation JHL7540 Thunderbolt 3 USB Controller [Titan Ridge 2C 2018] (rev 06)
3b:00.0 Non-Volatile memory controller: Sandisk Corp WD Black 2019/PC SN750 NVMe SSD
3c:00.0 Ethernet controller: Intel Corporation Device 3101 (rev 02)
```

---

### Post by mysteriousmonkey29 on 2020-11-23
I actually accidentally solved the problem. I had secure boot disabled, and it was doing something weird to my drivers. Re-enabled it to solve a problem with my monitor, and now the ethernet works again! Thanks everyone for the help

---

### Post by CelticWarrior on 2020-11-23
Secure Boot disabled does nothing to any driver. OTOH, Secure Boot enabled prevents loading unsigned drivers like the ones for your graphics card.
There's no situation/scenario where hardware not working without secure boot suddenly works with it enabled.

---

### Post by Raffles727 on 2020-11-25
I checked out your rig on the WWW, a pretty powerful machine. I'm surprised to see only > 3c:00.0 Ethernet controller: Intel Corporation Device 3101 (rev 02)

As a matter of interest, what does it say now since you fixed the problem?

---

### Post by mysteriousmonkey29 on 2020-12-14
Sorry just saw this. Funnily enough, it broke again! I didn't change anything, as far as I am aware. I tried redisabling and enabling secure boot, but that didn't do it this time. Currently, ifconfig does not show an eth0 interface, my computer doesn't detect when an ethernet network is plugged in, and 

```

lspci

```

produces:

```

00:00.0 Host bridge: Intel Corporation 10th Gen Core Processor Host Bridge/DRAM Registers (rev 02)
00:01.0 PCI bridge: Intel Corporation 6th-9th Gen Core Processor PCIe Controller (x16) (rev 02)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics (rev 05)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 02)
00:12.0 Signal processing controller: Intel Corporation Comet Lake PCH Thermal Controller
00:14.0 USB controller: Intel Corporation Comet Lake USB 3.1 xHCI Host Controller
00:14.2 RAM memory: Intel Corporation Comet Lake PCH Shared SRAM
00:14.3 Network controller: Intel Corporation Comet Lake PCH CNVi WiFi
00:15.0 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH Serial IO I2C Controller #0
00:15.2 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH Serial IO I2C Controller #2
00:16.0 Communication controller: Intel Corporation Comet Lake HECI Controller
00:1b.0 PCI bridge: Intel Corporation Comet Lake PCI Express Root Port #17 (rev f0)
00:1d.0 PCI bridge: Intel Corporation Comet Lake PCI Express Root Port #9 (rev f0)
00:1d.6 PCI bridge: Intel Corporation Device 06b6 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Comet Lake LPC Controller
00:1f.3 Audio device: Intel Corporation Comet Lake PCH cAVS
00:1f.4 SMBus: Intel Corporation Comet Lake PCH SMBus Controller
00:1f.5 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH SPI Controller
01:00.0 VGA compatible controller: NVIDIA Corporation TU106M [GeForce RTX 2060 Mobile] (rev a1)
01:00.1 Audio device: NVIDIA Corporation TU106 High Definition Audio Controller (rev a1)
01:00.2 USB controller: NVIDIA Corporation TU106 USB 3.1 Host Controller (rev a1)
01:00.3 Serial bus controller [0c80]: NVIDIA Corporation TU106 USB Type-C UCSI Controller (rev a1)
02:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
03:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
03:01.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
03:02.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
04:00.0 System peripheral: Intel Corporation JHL7540 Thunderbolt 3 NHI [Titan Ridge 2C 2018] (rev 06)
3a:00.0 USB controller: Intel Corporation JHL7540 Thunderbolt 3 USB Controller [Titan Ridge 2C 2018] (rev 06)
3b:00.0 Non-Volatile memory controller: Sandisk Corp WD Black 2019/PC SN750 NVMe SSD
3c:00.0 Ethernet controller: Intel Corporation Device 3101 (rev 02)



```

Any more ideas?

---

### Post by mysteriousmonkey29 on 2020-12-15
Ok, even more weirdly, it started working again today! I really have no idea what's causing the changes. All I did since it wasn't working yesterday was restart overnight (and I tried restarting yesterday when it wasn't working, to no avail).

Currently,

```
ifconfig
```
produces:
```
docker0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.17.0.1  netmask 255.255.0.0  broadcast 172.17.255.255
        ether 02:42:25:e0:be:1b  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enx54bf643fb650: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.132  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::251a:a2c3:dc8a:9a55  prefixlen 64  scopeid 0x20<link>
        inet6 2600:8801:c300:e95:8c36:6723:e162:aebc  prefixlen 64  scopeid 0x0<global>
        inet6 fd00:58ef:6881:1052:954d:8be3:cd6:a0f1  prefixlen 64  scopeid 0x0<global>
        inet6 2600:8801:c300:e95:954d:8be3:cd6:a0f1  prefixlen 64  scopeid 0x0<global>
        inet6 fd00:58ef:6881:1052:26b1:28e4:56b0:7923  prefixlen 64  scopeid 0x0<global>
        ether 54:bf:64:3f:b6:50  txqueuelen 1000  (Ethernet)
        RX packets 74714  bytes 92888590 (92.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 42705  bytes 5344883 (5.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 1821  bytes 194996 (194.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1821  bytes 194996 (194.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


```

and
```
lspci
```
produces:
```
00:00.0 Host bridge: Intel Corporation 10th Gen Core Processor Host Bridge/DRAM Registers (rev 02)
00:01.0 PCI bridge: Intel Corporation 6th-9th Gen Core Processor PCIe Controller (x16) (rev 02)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics (rev 05)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 02)
00:12.0 Signal processing controller: Intel Corporation Comet Lake PCH Thermal Controller
00:14.0 USB controller: Intel Corporation Comet Lake USB 3.1 xHCI Host Controller
00:14.2 RAM memory: Intel Corporation Comet Lake PCH Shared SRAM
00:14.3 Network controller: Intel Corporation Comet Lake PCH CNVi WiFi
00:15.0 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH Serial IO I2C Controller #0
00:15.2 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH Serial IO I2C Controller #2
00:16.0 Communication controller: Intel Corporation Comet Lake HECI Controller
00:1b.0 PCI bridge: Intel Corporation Comet Lake PCI Express Root Port #17 (rev f0)
00:1d.0 PCI bridge: Intel Corporation Comet Lake PCI Express Root Port #9 (rev f0)
00:1d.6 PCI bridge: Intel Corporation Device 06b6 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Comet Lake LPC Controller
00:1f.3 Audio device: Intel Corporation Comet Lake PCH cAVS
00:1f.4 SMBus: Intel Corporation Comet Lake PCH SMBus Controller
00:1f.5 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH SPI Controller
01:00.0 VGA compatible controller: NVIDIA Corporation TU106M [GeForce RTX 2060 Mobile] (rev a1)
01:00.1 Audio device: NVIDIA Corporation TU106 High Definition Audio Controller (rev a1)
01:00.2 USB controller: NVIDIA Corporation TU106 USB 3.1 Host Controller (rev a1)
01:00.3 Serial bus controller [0c80]: NVIDIA Corporation TU106 USB Type-C UCSI Controller (rev a1)
02:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
03:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
03:01.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
03:02.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
04:00.0 System peripheral: Intel Corporation JHL7540 Thunderbolt 3 NHI [Titan Ridge 2C 2018] (rev 06)
3a:00.0 USB controller: Intel Corporation JHL7540 Thunderbolt 3 USB Controller [Titan Ridge 2C 2018] (rev 06)
3b:00.0 Non-Volatile memory controller: Sandisk Corp WD Black 2019/PC SN750 NVMe SSD
3c:00.0 Ethernet controller: Intel Corporation Device 3101 (rev 02)


```

Any idea what could be causing these intermittent issues? Thanks!

---


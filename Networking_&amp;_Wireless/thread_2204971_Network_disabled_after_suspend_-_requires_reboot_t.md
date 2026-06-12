---
title: "Network disabled after suspend - requires reboot to fix"
date: 2014-02-11
forum: Networking &amp; Wireless
---

### Post by typically2 on 2014-02-11
Hi all,

Disclaimer: This topic has been posted in many forms, and I've spent ages sifting through them. My specific problem may have already been addressed, but if so I cannot find the proper thread.

Using Ubuntu 13.10. The symptoms are that the wired network (eth0) becomes disabled when resuming after a suspend. The wifi (wlan0) does work. The network manager GUI menu has "Ethernet network" ghosted out and "disconnected". The MAC address of eth0 is set to 00:00:00:00:00:00 (as determined from the "Edit connections" GUI), which means MATLAB won't even run because it requires this address for licensing purposes.

The problem cannot be solved using [FONT=courier new]sudo service network-manager restart[/FONT]. Only a hard reboot works.

Here are various relevant outputs:

nm-tool (before suspend):


```

NetworkManager Tool


State: connected (global)


- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        14:FE:B5:C1:B1:91


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         134.94.8.176
    Prefix:          22 (255.255.252.0)
    Gateway:         134.94.8.1


    DNS:             134.94.80.4
    DNS:             134.94.80.2
    DNS:             134.94.80.3

```


nm-tool (after suspend):


```

State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:00:00:00:00:00


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off



```

ifconfig (before suspend):

```

eth0      Link encap:Ethernet  HWaddr 14:fe:b5:c1:b1:91  
          inet addr:134.94.8.176  Bcast:134.94.11.255  Mask:255.255.252.0
          inet6 addr: fe80::16fe:b5ff:fec1:b191/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6569 errors:0 dropped:1 overruns:0 frame:0
          TX packets:539 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1429075 (1.4 MB)  TX bytes:132284 (132.2 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:219 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:51603 (51.6 KB)  TX bytes:51603 (51.6 KB)


wlan0     Link encap:Ethernet  HWaddr ac:72:89:5a:cb:ca  
          inet addr:172.18.36.71  Bcast:172.18.255.255  Mask:255.255.0.0
          inet6 addr: fe80::ae72:89ff:fe5a:cbca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17705 errors:0 dropped:2 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3086242 (3.0 MB)  TX bytes:101709 (101.7 KB)



```

ifconfig (after suspend):

```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4475 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4475 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:541628 (541.6 KB)  TX bytes:541628 (541.6 KB)


wlan0     Link encap:Ethernet  HWaddr ac:72:89:5a:cb:ca  
          inet addr:172.18.36.71  Bcast:172.18.255.255  Mask:255.255.0.0
          inet6 addr: fe80::ae72:89ff:fe5a:cbca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:221438 errors:0 dropped:2 overruns:0 frame:0
          TX packets:6163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36898691 (36.8 MB)  TX bytes:1481885 (1.4 MB)

```

sudo gedit /etc/network/interfaces

```

# interfaces(5) file used by ifup(8) and ifdown(8)auto lo
iface lo inet loopback


#auto eth0
#iface eth0 inet dhcp

```

sudo gedit /etc/NetworkManager/NetworkManager.conf

```

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=14:FE:B5:C1:B1:91,

[ifupdown]
#managed=true
managed=false

```

dmesg (for r8169 driver, after suspend):

```
[  112.178559] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded[  112.178568] r8169 0000:06:00.0: can't disable ASPM; OS doesn't have ASPM control
[  112.178772] r8169 0000:06:00.0: irq 53 for MSI/MSI-X
[  112.178905] r8169 0000:06:00.0 eth0: RTL8168e/8111e at 0xffffc90000c2c000, 00:00:00:00:00:00, XID 0c200000 IRQ 53
[  112.178907] r8169 0000:06:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]

```

sudo lshw -C network

```
  *-network                      description: Wireless interface
       product: Centrino Wireless-N 1030 [Rainbow Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: ac:72:89:5a:cb:ca
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.11.0-15-generic firmware=18.168.6.1 ip=172.18.36.71 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:51 memory:f1b00000-f1b01fff
  *-network DISABLED
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=no multicast=yes port=MII speed=100Mbit/s
       resources: irq:53 ioport:2000(size=256) memory:f1804000-f1804fff memory:f1800000-f1803fff

```

rfkill list all

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

more /var/lib/NetworkManager/NetworkManager.state

```

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```

Things I have tried:

1. Restart network manager
2. Setting a [FONT=Ubuntu Mono][FONT=courier new]/etc/pm/sleep.d/network-manager-resume[/FONT] [/FONT]file, as here[FONT=Ubuntu Mono]: [http://ubuntuforums.org/showthread.php?t=1652574&p=10283728#post10283728](http://ubuntuforums.org/showthread.php?t=1652574&p=10283728#post10283728) 
[/FONT]3. [FONT=courier new]sudo nmcli nm sleep false: Error in sleep: Already awake[/FONT]
4. Changed "managed=true" and uncommented "iface eth0 inet dhcp" in /etc/network/interfaces and /etc/NetworkManager/NetworkManager.conf, respectively.

Seems to me network manager is coming out of suspend fine, but something is disabling the ethernet card.

Any advice would be highly appreciated. Hopefully there's something obvious here (e.g., the network-manager vs. ifup/ifdown stuff) that a relative newbie like myself is missing. This bug makes it next to impossible to use the suspend function of my laptop.

---

### Post by Toz on 2014-02-11
Hello and welcome to the forums.

Before suspending, unload the r8169 module:
```
sudo modprobe -r r8169
```
..then suspend. On resume, reload the module:
```
sudo modprobe r8169
```

Does this work?

---

### Post by typically2 on 2014-02-11
Hi Toz,

Thanks for your quick reply. Unfortunately this doesn't solve the problem. The eth0 network is still disabled. 

(Calling these commands prior to suspending works fine).

EDIT:

One thing that's bothering me is the line from dmesg:

```

r8169 0000:06:00.0: can't disable ASPM; OS doesn't have ASPM control

```

Thoughts on that?

---

### Post by Toz on 2014-02-11
> **typically2 said:**
> One thing that's bothering me is the line from dmesg:

```

r8169 0000:06:00.0: can't disable ASPM; OS doesn't have ASPM control

```

Thoughts on that?
Are there any aspm settings available in the bios for your computer?
Can you try the **pcie_aspm=force** kernel parameter? Post back your dmesg after you have booted with it.

Can you also post back your /var/log/pm-suspend.log file and the results of:
```
cat /var/log/syslog | grep PM:
```

---

### Post by typically2 on 2014-02-11
Couldn't find any ASPM options in the BIOS menus.

After setting the kernel parameter, here are the outputs:


dmesg (complete):


```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.11.0-15-generic (buildd@roseapple) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 (Ubuntu 3.11.0-15.25-generic 3.11.10)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic root=UUID=94a50132-076f-49df-9aae-da1abc32b8b6 ro persistent quiet splash vt.handoff=7 pcie_aspm=force
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] Disabled fast string operations
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bac8efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bac8f000-0x00000000bacabfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bacac000-0x00000000bacb8fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bacb9000-0x00000000badcefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000badcf000-0x00000000badcffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000badd0000-0x00000000badfafff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000badfb000-0x00000000badfcfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000badfd000-0x00000000badfefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000badff000-0x00000000bae01fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bae02000-0x00000000bae09fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bae0a000-0x00000000bae1afff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bae1b000-0x00000000baf17fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000baf18000-0x00000000baf1bfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000baf1c000-0x00000000baf1efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000baf1f000-0x00000000baf9efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000baf9f000-0x00000000baffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bafff000-0x00000000baffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb000000-0x00000000bf9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed08000-0x00000000fed08fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffd80000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000023e9fefff] usable
[    0.000000] BIOS-e820: [mem 0x000000023e9ff000-0x000000023fdfffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: Dell Inc.          Dell System XPS L502X/0NJT03, BIOS A06 07/20/2011
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x23e9ff max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0BC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0BB000000 mask FFF000000 uncachable
[    0.000000]   5 base 100000000 mask F00000000 write-back
[    0.000000]   6 base 200000000 mask FC0000000 write-back
[    0.000000]   7 base 23FE00000 mask FFFE00000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xbb000 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] reserving inaccessible SNB gfx pages
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fd1000, 0x01fd1fff] PGTABLE
[    0.000000] BRK [0x01fd2000, 0x01fd2fff] PGTABLE
[    0.000000] BRK [0x01fd3000, 0x01fd3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x23e600000-0x23e7fffff]
[    0.000000]  [mem 0x23e600000-0x23e7fffff] page 2M
[    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x23c000000-0x23e5fffff]
[    0.000000]  [mem 0x23c000000-0x23e5fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x23bffffff]
[    0.000000]  [mem 0x200000000-0x23bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xbac8efff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xbabfffff] page 2M
[    0.000000]  [mem 0xbac00000-0xbac8efff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbafff000-0xbaffffff]
[    0.000000]  [mem 0xbafff000-0xbaffffff] page 4k
[    0.000000] BRK [0x01fd5000, 0x01fd5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 2M
[    0.000000] BRK [0x01fd6000, 0x01fd6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x23e800000-0x23e9fefff]
[    0.000000]  [mem 0x23e800000-0x23e9fefff] page 4k
[    0.000000] RAMDISK: [mem 0x35eb0000-0x36f4ffff]
[    0.000000] ACPI: RSDP 00000000000f00e0 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000baffe120 00094 (v01 DELL    QA09    00000002 LOHR 00000002)
[    0.000000] ACPI: FACP 00000000bafef000 000F4 (v03 DELL    QA09    00000002 PTL  00000002)
[    0.000000] ACPI: DSDT 00000000baff2000 08C93 (v02 DELL    SNB-CPT 00000000 INTL 20061109)
[    0.000000] ACPI: FACS 00000000baf40000 00040
[    0.000000] ACPI: SLIC 00000000baffd000 00176 (v01 DELL    QA09    00000002 LOHR 00000001)
[    0.000000] ACPI: SSDT 00000000baffb000 01068 (v01 DELL   PtidDevc 00001000 INTL 20061109)
[    0.000000] ACPI: ASF! 00000000baff1000 000A5 (v32 DELL    QA09    00000002 PTL  00000002)
[    0.000000] ACPI: HPET 00000000bafee000 00038 (v01 DELL    QA09    00000002 PTL  00000002)
[    0.000000] ACPI: APIC 00000000bafed000 00098 (v01 DELL    QA09    00000002 PTL  00000002)
[    0.000000] ACPI: MCFG 00000000bafec000 0003C (v01 DELL    QA09    00000002 PTL  00000002)
[    0.000000] ACPI: SSDT 00000000bafea000 0124D (v01 NvORef NvOptTbl 00001000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bafe9000 00804 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bafe8000 00996 (v01  PmRef    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: UEFI 00000000bafe7000 0003E (v01 DELL    QA09    00000002 PTL  00000002)
[    0.000000] ACPI: UEFI 00000000bafe6000 00042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: DMAR 00000000bafe5000 000E8 (v01 INTEL      SNB  00000001 INTL 00000001)
[    0.000000] ACPI: UEFI 00000000bafe4000 0026A (v01 DELL    QA09    00000002 PTL  00000002)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000023e9fefff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x23e9fefff]
[    0.000000]   NODE_DATA [mem 0x23e9fa000-0x23e9fefff]
[    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880235e00000-ffff88023ddfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x23e9fefff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0xbac8efff]
[    0.000000]   node   0: [mem 0xbafff000-0xbaffffff]
[    0.000000]   node   0: [mem 0x100000000-0x23e9fefff]
[    0.000000] On node 0 totalpages: 2070059
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 156 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 11891 pages used for memmap
[    0.000000]   DMA32 zone: 760976 pages, LIFO batch:31
[    0.000000]   Normal zone: 20392 pages used for memmap
[    0.000000]   Normal zone: 1305087 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbac8f000-0xbacabfff]
[    0.000000] PM: Registered nosave memory: [mem 0xbacac000-0xbacb8fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbacb9000-0xbadcefff]
[    0.000000] PM: Registered nosave memory: [mem 0xbadcf000-0xbadcffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbadd0000-0xbadfafff]
[    0.000000] PM: Registered nosave memory: [mem 0xbadfb000-0xbadfcfff]
[    0.000000] PM: Registered nosave memory: [mem 0xbadfd000-0xbadfefff]
[    0.000000] PM: Registered nosave memory: [mem 0xbadff000-0xbae01fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbae02000-0xbae09fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbae0a000-0xbae1afff]
[    0.000000] PM: Registered nosave memory: [mem 0xbae1b000-0xbaf17fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbaf18000-0xbaf1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xbaf1c000-0xbaf1efff]
[    0.000000] PM: Registered nosave memory: [mem 0xbaf1f000-0xbaf9efff]
[    0.000000] PM: Registered nosave memory: [mem 0xbaf9f000-0xbaffefff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb000000-0xbf9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbfa00000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed07fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed08000-0xfed08fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed09000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffd7ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffd80000-0xffffffff]
[    0.000000] e820: [mem 0xbfa00000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88023e400000 s86720 r8192 d23872 u262144
[    0.000000] pcpu-alloc: s86720 r8192 d23872 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2037556
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic root=UUID=94a50132-076f-49df-9aae-da1abc32b8b6 ro persistent quiet splash vt.handoff=7 pcie_aspm=force
[    0.000000] PCIe ASPM is forcibly enabled
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8047996K/8280236K available (7149K kernel code, 1082K rwdata, 3312K rodata, 1364K init, 1420K bss, 232240K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-255.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2693.742 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5387.48 BogoMIPS (lpj=10774968)
[    0.000004] pid_max: default: 32768 minimum: 301
[    0.000024] Security Framework initialized
[    0.000040] AppArmor: AppArmor initialized
[    0.000041] Yama: becoming mindful.
[    0.000484] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.001944] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.002566] Mount-cache hash table entries: 256
[    0.002716] Initializing cgroup subsys memory
[    0.002724] Initializing cgroup subsys devices
[    0.002725] Initializing cgroup subsys freezer
[    0.002727] Initializing cgroup subsys blkio
[    0.002728] Initializing cgroup subsys perf_event
[    0.002730] Initializing cgroup subsys hugetlb
[    0.002747] Disabled fast string operations
[    0.002748] CPU: Physical Processor ID: 0
[    0.002749] CPU: Processor Core ID: 0
[    0.002753] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.002753] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.002756] mce: CPU supports 7 MCE banks
[    0.002763] CPU0: Thermal monitoring handled by SMI
[    0.002770] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.002770] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.002770] tlb_flushall_shift: 5
[    0.002849] Freeing SMP alternatives memory: 28K (ffffffff81e65000 - ffffffff81e6c000)
[    0.004605] ACPI: Core revision 20130517
[    0.009294] ACPI: All ACPI Tables successfully acquired
[    0.059545] ftrace: allocating 27844 entries in 109 pages
[    0.071371] dmar: Host address width 36
[    0.071373] dmar: DRHD base: 0x000000fed90000 flags: 0x0
[    0.071378] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020e60262 ecap f0101a
[    0.071380] dmar: DRHD base: 0x000000fed91000 flags: 0x1
[    0.071383] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap c9008020660262 ecap f0105a
[    0.071384] dmar: RMRR base: 0x000000bae1d000 end: 0x000000bae33fff
[    0.071385] dmar: RMRR base: 0x000000bb800000 end: 0x000000bf9fffff
[    0.071456] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.071457] HPET id 0 under DRHD base 0xfed91000
[    0.071457] HPET id 0 under DRHD base 0xfed91000
[    0.071458] HPET id 0 under DRHD base 0xfed91000
[    0.071459] HPET id 0 under DRHD base 0xfed91000
[    0.071460] HPET id 0 under DRHD base 0xfed91000
[    0.071460] HPET id 0 under DRHD base 0xfed91000
[    0.071461] HPET id 0 under DRHD base 0xfed91000
[    0.071462] HPET id 0 under DRHD base 0xfed91000
[    0.071671] Enabled IRQ remapping in x2apic mode
[    0.071672] Enabling x2apic
[    0.071673] Enabled x2apic
[    0.071678] Switched APIC routing to cluster x2apic.
[    0.072122] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.111791] smpboot: CPU0: Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz (fam: 06, model: 2a, stepping: 07)
[    0.111799] TSC deadline timer enabled
[    0.111808] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, full-width counters, Intel PMU driver.
[    0.111814] perf_event_intel: PEBS disabled due to CPU errata, please upgrade microcode
[    0.111816] ... version:                3
[    0.111817] ... bit width:              48
[    0.111817] ... generic registers:      4
[    0.111818] ... value mask:             0000ffffffffffff
[    0.111819] ... max period:             0000ffffffffffff
[    0.111820] ... fixed-purpose events:   3
[    0.111821] ... event mask:             000000070000000f
[    0.124103] Disabled fast string operations
[    0.124116] CPU1: Thermal monitoring handled by SMI
[    0.126288] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.137298] Disabled fast string operations
[    0.137310] CPU2: Thermal monitoring handled by SMI
[    0.150408] Disabled fast string operations
[    0.150420] CPU3: Thermal monitoring handled by SMI
[    0.113167] smpboot: Booting Node   0, Processors  #1 #2 #3
[    0.152526] Brought up 4 CPUs
[    0.152530] smpboot: Total of 4 processors activated (21549.93 BogoMIPS)
[    0.155990] devtmpfs: initialized
[    0.156912] EVM: security.selinux
[    0.156913] EVM: security.SMACK64
[    0.156914] EVM: security.capability
[    0.156961] PM: Registering ACPI NVS region [mem 0xbacac000-0xbacb8fff] (53248 bytes)
[    0.156964] PM: Registering ACPI NVS region [mem 0xbadcf000-0xbadcffff] (4096 bytes)
[    0.156965] PM: Registering ACPI NVS region [mem 0xbadfb000-0xbadfcfff] (8192 bytes)
[    0.156966] PM: Registering ACPI NVS region [mem 0xbadff000-0xbae01fff] (12288 bytes)
[    0.156967] PM: Registering ACPI NVS region [mem 0xbae0a000-0xbae1afff] (69632 bytes)
[    0.156969] PM: Registering ACPI NVS region [mem 0xbaf18000-0xbaf1bfff] (16384 bytes)
[    0.156970] PM: Registering ACPI NVS region [mem 0xbaf1f000-0xbaf9efff] (524288 bytes)
[    0.157587] regulator-dummy: no parameters
[    0.157617] RTC time: 20:17:44, date: 02/11/14
[    0.157645] NET: Registered protocol family 16
[    0.157769] ACPI: bus type PCI registered
[    0.157770] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.157820] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.157823] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.163932] PCI: Using configuration type 1 for base access
[    0.164081] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.164082] mtrr: probably your BIOS does not setup all CPUs.
[    0.164083] mtrr: corrected configuration.
[    0.164653] bio: create slab <bio-0> at 0
[    0.164776] ACPI: Added _OSI(Module Device)
[    0.164778] ACPI: Added _OSI(Processor Device)
[    0.164779] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.164780] ACPI: Added _OSI(Processor Aggregator Device)
[    0.166054] ACPI: EC: Look up EC in DSDT
[    0.167288] ACPI: Executed 1 blocks of module-level executable AML code
[    0.179907] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.180807] ACPI: SSDT 00000000bae06718 0067C (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.181131] ACPI: Dynamic OEM Table Load:
[    0.181133] ACPI: SSDT           (null) 0067C (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.188039] ACPI: SSDT 00000000bae07a98 00303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    0.188383] ACPI: Dynamic OEM Table Load:
[    0.188384] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    0.191933] ACPI: SSDT 00000000bae05d98 00119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    0.192252] ACPI: Dynamic OEM Table Load:
[    0.192254] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    0.198458] ACPI: Interpreter enabled
[    0.198465] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
[    0.198468] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.198480] ACPI: (supports S0 S3 S4 S5)
[    0.198481] ACPI: Using IOAPIC for interrupt routing
[    0.198501] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.198587] ACPI: No dock devices found.
[    0.203991] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.204020] \_SB_.PCI0:_OSC invalid UUID
[    0.204021] _OSC request data:1 8 0 
[    0.204047] \_SB_.PCI0:_OSC invalid UUID
[    0.204048] _OSC request data:1 1f 0 
[    0.204051] acpi PNP0A08:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.204052] acpi PNP0A08:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.204537] PCI host bridge to bus 0000:00
[    0.204539] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.204541] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.204542] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.204544] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.204545] pci_bus 0000:00: root bus resource [mem 0xbfa00000-0xfeafffff]
[    0.204547] pci_bus 0000:00: root bus resource [mem 0xfed40000-0xfed44fff]
[    0.204554] pci 0000:00:00.0: [8086:0104] type 00 class 0x060000
[    0.204622] pci 0000:00:01.0: [8086:0101] type 01 class 0x060400
[    0.204651] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.204680] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.204709] pci 0000:00:02.0: [8086:0126] type 00 class 0x030000
[    0.204718] pci 0000:00:02.0: reg 0x10: [mem 0xf1400000-0xf17fffff 64bit]
[    0.204723] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.204727] pci 0000:00:02.0: reg 0x20: [io  0x4000-0x403f]
[    0.204810] pci 0000:00:16.0: [8086:1c3a] type 00 class 0x078000
[    0.204833] pci 0000:00:16.0: reg 0x10: [mem 0xf1c05000-0xf1c0500f 64bit]
[    0.204907] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.204974] pci 0000:00:1a.0: [8086:1c2d] type 00 class 0x0c0320
[    0.204995] pci 0000:00:1a.0: reg 0x10: [mem 0xf1c0a000-0xf1c0a3ff]
[    0.205083] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.205128] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.205161] pci 0000:00:1b.0: [8086:1c20] type 00 class 0x040300
[    0.205176] pci 0000:00:1b.0: reg 0x10: [mem 0xf1c00000-0xf1c03fff 64bit]
[    0.205242] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.205278] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.205308] pci 0000:00:1c.0: [8086:1c10] type 01 class 0x060400
[    0.205439] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.205485] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.205515] pci 0000:00:1c.1: [8086:1c12] type 01 class 0x060400
[    0.205644] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.205690] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.205722] pci 0000:00:1c.3: [8086:1c16] type 01 class 0x060400
[    0.205852] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.205897] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.205924] pci 0000:00:1c.4: [8086:1c18] type 01 class 0x060400
[    0.206000] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.206037] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.206063] pci 0000:00:1c.5: [8086:1c1a] type 01 class 0x060400
[    0.206139] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.206175] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.206207] pci 0000:00:1d.0: [8086:1c26] type 00 class 0x0c0320
[    0.206228] pci 0000:00:1d.0: reg 0x10: [mem 0xf1c09000-0xf1c093ff]
[    0.206316] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.206360] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.206389] pci 0000:00:1f.0: [8086:1c4b] type 00 class 0x060100
[    0.206545] pci 0000:00:1f.2: [8086:1c03] type 00 class 0x010601
[    0.206562] pci 0000:00:1f.2: reg 0x10: [io  0x4088-0x408f]
[    0.206570] pci 0000:00:1f.2: reg 0x14: [io  0x4094-0x4097]
[    0.206578] pci 0000:00:1f.2: reg 0x18: [io  0x4080-0x4087]
[    0.206586] pci 0000:00:1f.2: reg 0x1c: [io  0x4090-0x4093]
[    0.206593] pci 0000:00:1f.2: reg 0x20: [io  0x4060-0x407f]
[    0.206601] pci 0000:00:1f.2: reg 0x24: [mem 0xf1c08000-0xf1c087ff]
[    0.206645] pci 0000:00:1f.2: PME# supported from D3hot
[    0.206698] pci 0000:00:1f.3: [8086:1c22] type 00 class 0x0c0500
[    0.206713] pci 0000:00:1f.3: reg 0x10: [mem 0xf1c04000-0xf1c040ff 64bit]
[    0.206733] pci 0000:00:1f.3: reg 0x20: [io  0xefa0-0xefbf]
[    0.206831] pci 0000:01:00.0: [10de:0df4] type 00 class 0x030000
[    0.206839] pci 0000:01:00.0: reg 0x10: [mem 0xf0000000-0xf0ffffff]
[    0.206847] pci 0000:01:00.0: reg 0x14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.206855] pci 0000:01:00.0: reg 0x1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.206860] pci 0000:01:00.0: reg 0x24: [io  0x3000-0x307f]
[    0.206866] pci 0000:01:00.0: reg 0x30: [mem 0xfff80000-0xffffffff pref]
[    0.206906] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.212562] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.212570] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.212576] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf10fffff]
[    0.212585] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.212694] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.212933] pci 0000:03:00.0: [8086:008a] type 00 class 0x028000
[    0.213096] pci 0000:03:00.0: reg 0x10: [mem 0xf1b00000-0xf1b01fff 64bit]
[    0.213806] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.213949] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.220680] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.220689] pci 0000:00:1c.1:   bridge window [mem 0xf1b00000-0xf1bfffff]
[    0.220853] pci 0000:04:00.0: [1033:0194] type 00 class 0x0c0330
[    0.220879] pci 0000:04:00.0: reg 0x10: [mem 0xf1a00000-0xf1a01fff 64bit]
[    0.221012] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.221044] pci 0000:04:00.0: System wakeup disabled by ACPI
[    0.228629] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    0.228647] pci 0000:00:1c.3:   bridge window [mem 0xf1a00000-0xf1afffff]
[    0.228754] pci 0000:00:1c.4: PCI bridge to [bus 05]
[    0.228760] pci 0000:00:1c.4:   bridge window [mem 0xf1900000-0xf19fffff]
[    0.228841] pci 0000:06:00.0: [10ec:8168] type 00 class 0x020000
[    0.228862] pci 0000:06:00.0: reg 0x10: [io  0x2000-0x20ff]
[    0.228896] pci 0000:06:00.0: reg 0x18: [mem 0xf1804000-0xf1804fff 64bit pref]
[    0.228917] pci 0000:06:00.0: reg 0x20: [mem 0xf1800000-0xf1803fff 64bit pref]
[    0.229010] pci 0000:06:00.0: supports D1 D2
[    0.229011] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.229046] pci 0000:06:00.0: System wakeup disabled by ACPI
[    0.236586] pci 0000:00:1c.5: PCI bridge to [bus 06]
[    0.236596] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
[    0.236615] pci 0000:00:1c.5:   bridge window [mem 0xf1800000-0xf18fffff 64bit pref]
[    0.237067] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.237114] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.237158] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.237201] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.237244] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.237287] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.237331] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.237375] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.237563] ACPI: Enabled 5 GPEs in block 00 to 3F
[    0.237588] ACPI: \_SB_.PCI0: notify handler is installed
[    0.237634] Found 1 acpi root devices
[    0.237698] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.237767] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.237771] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    0.237772] vgaarb: loaded
[    0.237773] vgaarb: bridge control possible 0000:01:00.0
[    0.237774] vgaarb: no bridge control possible 0000:00:02.0
[    0.237893] SCSI subsystem initialized
[    0.237895] ACPI: bus type ATA registered
[    0.237929] libata version 3.00 loaded.
[    0.237942] ACPI: bus type USB registered
[    0.237953] usbcore: registered new interface driver usbfs
[    0.237958] usbcore: registered new interface driver hub
[    0.237978] usbcore: registered new device driver usb
[    0.238058] PCI: Using ACPI for IRQ routing
[    0.239492] PCI: pci_cache_line_size set to 64 bytes
[    0.239638] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.239640] e820: reserve RAM buffer [mem 0xbac8f000-0xbbffffff]
[    0.239641] e820: reserve RAM buffer [mem 0xbb000000-0xbbffffff]
[    0.239643] e820: reserve RAM buffer [mem 0x23e9ff000-0x23fffffff]
[    0.239707] NetLabel: Initializing
[    0.239708] NetLabel:  domain hash size = 128
[    0.239708] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.239717] NetLabel:  unlabeled traffic allowed by default
[    0.239768] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.239772] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.241796] Switched to clocksource hpet
[    0.245475] AppArmor: AppArmor Filesystem Enabled
[    0.245497] pnp: PnP ACPI init
[    0.245508] ACPI: bus type PNP registered
[    0.245537] pnp 00:00: [dma 4]
[    0.245555] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.245635] pnp 00:01: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.245665] pnp 00:02: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.245700] system 00:03: [io  0x0680-0x069f] has been reserved
[    0.245702] system 00:03: [io  0x1000-0x1003] has been reserved
[    0.245703] system 00:03: [io  0x1004-0x1013] has been reserved
[    0.245704] system 00:03: [io  0xffff] has been reserved
[    0.245706] system 00:03: [io  0x0400-0x0453] could not be reserved
[    0.245708] system 00:03: [io  0x0458-0x047f] has been reserved
[    0.245709] system 00:03: [io  0x0500-0x057f] has been reserved
[    0.245710] system 00:03: [io  0x164e-0x164f] has been reserved
[    0.245712] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.245734] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.245769] system 00:05: [io  0x0454-0x0457] has been reserved
[    0.245771] system 00:05: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.245826] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.245866] pnp 00:07: Plug and Play ACPI device, IDs DLL050e PNP0f13 (active)
[    0.245956] pnp 00:08: disabling [mem 0xfffff000-0xffffffff] because it overlaps 0000:01:00.0 BAR 6 [mem 0xfff80000-0xffffffff pref]
[    0.245971] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.245972] system 00:08: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.245974] system 00:08: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.245975] system 00:08: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.245977] system 00:08: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.245978] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.245980] system 00:08: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.245981] system 00:08: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.245983] system 00:08: [mem 0xff000000-0xffffffff] could not be reserved
[    0.245984] system 00:08: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.245986] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.246085] pnp 00:09: Plug and Play ACPI device, IDs SMO8800 (active)
[    0.246182] pnp: PnP ACPI: found 10 devices
[    0.246183] ACPI: bus type PNP unregistered
[    0.252137] pci 0000:01:00.0: no compatible bridge window for [mem 0xfff80000-0xffffffff pref]
[    0.252196] pci 0000:01:00.0: BAR 6: assigned [mem 0xf1000000-0xf107ffff pref]
[    0.252199] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.252201] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.252203] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf10fffff]
[    0.252205] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.252209] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.252226] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.252232] pci 0000:00:1c.1:   bridge window [mem 0xf1b00000-0xf1bfffff]
[    0.252244] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    0.252250] pci 0000:00:1c.3:   bridge window [mem 0xf1a00000-0xf1afffff]
[    0.252262] pci 0000:00:1c.4: PCI bridge to [bus 05]
[    0.252267] pci 0000:00:1c.4:   bridge window [mem 0xf1900000-0xf19fffff]
[    0.252275] pci 0000:00:1c.5: PCI bridge to [bus 06]
[    0.252277] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
[    0.252284] pci 0000:00:1c.5:   bridge window [mem 0xf1800000-0xf18fffff 64bit pref]
[    0.252599] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.252600] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.252602] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.252603] pci_bus 0000:00: resource 7 [mem 0xbfa00000-0xfeafffff]
[    0.252604] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed44fff]
[    0.252606] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.252607] pci_bus 0000:01: resource 1 [mem 0xf0000000-0xf10fffff]
[    0.252608] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.252610] pci_bus 0000:03: resource 1 [mem 0xf1b00000-0xf1bfffff]
[    0.252612] pci_bus 0000:04: resource 1 [mem 0xf1a00000-0xf1afffff]
[    0.252613] pci_bus 0000:05: resource 1 [mem 0xf1900000-0xf19fffff]
[    0.252614] pci_bus 0000:06: resource 0 [io  0x2000-0x2fff]
[    0.252616] pci_bus 0000:06: resource 2 [mem 0xf1800000-0xf18fffff 64bit pref]
[    0.252639] NET: Registered protocol family 2
[    0.252789] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.252964] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.253088] TCP: Hash tables configured (established 65536 bind 65536)
[    0.253110] TCP: reno registered
[    0.253120] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.253146] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.253212] NET: Registered protocol family 1
[    0.253223] pci 0000:00:02.0: Boot video device
[    0.254400] PCI: CLS 64 bytes, default 64
[    0.254442] Trying to unpack rootfs image as initramfs...
[    0.498061] Freeing initrd memory: 17024K (ffff880035eb0000 - ffff880036f50000)
[    0.498070] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.498072] software IO TLB [mem 0xb6c8f000-0xbac8f000] (64MB) mapped at [ffff8800b6c8f000-ffff8800bac8efff]
[    0.498236] Scanning for low memory corruption every 60 seconds
[    0.498459] Initialise module verification
[    0.498487] audit: initializing netlink socket (disabled)
[    0.498496] type=2000 audit(1392149864.456:1): initialized
[    0.521094] bounce pool size: 64 pages
[    0.521103] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.522068] zbud: loaded
[    0.522176] VFS: Disk quotas dquot_6.5.2
[    0.522206] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.522554] fuse init (API version 7.22)
[    0.522610] msgmni has been set to 15752
[    0.523028] Key type asymmetric registered
[    0.523030] Asymmetric key parser 'x509' registered
[    0.523052] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.523083] io scheduler noop registered
[    0.523085] io scheduler deadline registered (default)
[    0.523103] io scheduler cfq registered
[    0.523176] pcieport 0000:00:01.0: irq 42 for MSI/MSI-X
[    0.523398] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.523408] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.523446] intel_idle: MWAIT substates: 0x21120
[    0.523447] intel_idle: v0.4 model 0x2A
[    0.523448] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.721662] ACPI: AC Adapter [ADP0] (on-line)
[    0.721717] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.721721] ACPI: Power Button [PWRB]
[    0.721742] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.721744] ACPI: Sleep Button [SLPB]
[    0.721767] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.722299] ACPI: Lid Switch [LID0]
[    0.722324] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.722326] ACPI: Power Button [PWRF]
[    0.722368] ACPI: Requesting acpi_cpufreq
[    0.723395] thermal LNXTHERM:00: registered as thermal_zone0
[    0.723398] ACPI: Thermal Zone [TZ00] (76 C)
[    0.723554] thermal LNXTHERM:01: registered as thermal_zone1
[    0.723555] ACPI: Thermal Zone [TZ01] (76 C)
[    0.723580] GHES: HEST is not enabled!
[    0.723649] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.728965] Linux agpgart interface v0.103
[    0.729926] brd: module loaded
[    0.730455] loop: module loaded
[    0.730688] libphy: Fixed MDIO Bus: probed
[    0.730761] tun: Universal TUN/TAP device driver, 1.6
[    0.730762] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.730795] PPP generic driver version 2.4.2
[    0.730823] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.730824] ehci-pci: EHCI PCI platform driver
[    0.730903] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    0.730910] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.730915] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.730952] ehci-pci 0000:00:1a.0: debug port 2
[    0.734860] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.734877] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf1c0a000
[    0.735442] ACPI: Battery Slot [BAT0] (battery present)
[    0.745648] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.745669] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.745670] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.745672] usb usb1: Product: EHCI Host Controller
[    0.745673] usb usb1: Manufacturer: Linux 3.11.0-15-generic ehci_hcd
[    0.745675] usb usb1: SerialNumber: 0000:00:1a.0
[    0.745751] hub 1-0:1.0: USB hub found
[    0.745754] hub 1-0:1.0: 2 ports detected
[    0.745872] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    0.745878] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.745881] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.745892] ehci-pci 0000:00:1d.0: debug port 2
[    0.749775] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.749788] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf1c09000
[    0.761641] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.761657] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.761658] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.761660] usb usb2: Product: EHCI Host Controller
[    0.761661] usb usb2: Manufacturer: Linux 3.11.0-15-generic ehci_hcd
[    0.761662] usb usb2: SerialNumber: 0000:00:1d.0
[    0.761736] hub 2-0:1.0: USB hub found
[    0.761739] hub 2-0:1.0: 2 ports detected
[    0.761794] ehci-platform: EHCI generic platform driver
[    0.761799] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.761800] ohci-pci: OHCI PCI platform driver
[    0.761806] ohci-platform: OHCI generic platform driver
[    0.761810] uhci_hcd: USB Universal Host Controller Interface driver
[    0.761865] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    0.761869] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
[    0.762047] xhci_hcd 0000:04:00.0: irq 43 for MSI/MSI-X
[    0.762053] xhci_hcd 0000:04:00.0: irq 44 for MSI/MSI-X
[    0.762058] xhci_hcd 0000:04:00.0: irq 45 for MSI/MSI-X
[    0.762063] xhci_hcd 0000:04:00.0: irq 46 for MSI/MSI-X
[    0.762068] xhci_hcd 0000:04:00.0: irq 47 for MSI/MSI-X
[    0.762185] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.762187] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.762188] usb usb3: Product: xHCI Host Controller
[    0.762189] usb usb3: Manufacturer: Linux 3.11.0-15-generic xhci_hcd
[    0.762190] usb usb3: SerialNumber: 0000:04:00.0
[    0.762236] xHCI xhci_add_endpoint called for root hub
[    0.762237] xHCI xhci_check_bandwidth called for root hub
[    0.762250] hub 3-0:1.0: USB hub found
[    0.762256] hub 3-0:1.0: 2 ports detected
[    0.762304] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    0.762306] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 4
[    0.765455] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.765457] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.765458] usb usb4: Product: xHCI Host Controller
[    0.765459] usb usb4: Manufacturer: Linux 3.11.0-15-generic xhci_hcd
[    0.765460] usb usb4: SerialNumber: 0000:04:00.0
[    0.765507] xHCI xhci_add_endpoint called for root hub
[    0.765509] xHCI xhci_check_bandwidth called for root hub
[    0.765521] hub 4-0:1.0: USB hub found
[    0.765527] hub 4-0:1.0: 2 ports detected
[    0.769673] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.774690] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.774694] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.774771] mousedev: PS/2 mouse device common for all mice
[    0.774954] rtc_cmos 00:04: RTC can wake from S4
[    0.775064] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.775091] rtc_cmos 00:04: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.775136] device-mapper: uevent: version 1.0.3
[    0.775180] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com
[    0.775250] cpuidle: using governor ladder
[    0.775332] cpuidle: using governor menu
[    0.775339] ledtrig-cpu: registered to indicate activity on CPUs
[    0.775405] TCP: cubic registered
[    0.775468] NET: Registered protocol family 10
[    0.775618] NET: Registered protocol family 17
[    0.775625] Key type dns_resolver registered
[    0.775802] PM: Hibernation image not present or could not be loaded.
[    0.775804] Loading module verification certificates
[    0.776598] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 233c65a83836c14ba34eda83a0b805044bc3b448'
[    0.776608] registered taskstats version 1
[    0.778357] Key type trusted registered
[    0.779709] Key type encrypted registered
[    0.781262] AppArmor: AppArmor sha1 policy hashing enabled
[    0.781657]   Magic number: 2:642:295
[    0.781679] tty tty28: hash matches
[    0.781721] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.781745] rtc_cmos 00:04: setting system clock to 2014-02-11 20:17:45 UTC (1392149865)
[    0.782259] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.782260] EDD information not available.
[    0.782990] Freeing unused kernel memory: 1364K (ffffffff81d10000 - ffffffff81e65000)
[    0.782991] Write protecting the kernel read-only data: 12288k
[    0.784862] Freeing unused kernel memory: 1032K (ffff8800016fe000 - ffff880001800000)
[    0.786164] Freeing unused kernel memory: 784K (ffff880001b3c000 - ffff880001c00000)
[    0.794482] systemd-udevd[125]: starting version 204
[    1.006585] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.006831] r8169 0000:06:00.0: irq 48 for MSI/MSI-X
[    1.006870] ahci 0000:00:1f.2: version 3.0
[    1.006979] ahci 0000:00:1f.2: irq 49 for MSI/MSI-X
[    1.006992] r8169 0000:06:00.0 eth0: RTL8168e/8111e at 0xffffc90000c2c000, 14:fe:b5:c1:b1:91, XID 0c200000 IRQ 48
[    1.006995] r8169 0000:06:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.007011] ahci: SSS flag set, parallel bus scan disabled
[    1.021587] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x13 impl SATA mode
[    1.021592] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems sxs apst 
[    1.021599] ahci 0000:00:1f.2: setting latency timer to 64
[    1.038124] scsi0 : ahci
[    1.038193] scsi1 : ahci
[    1.038242] scsi2 : ahci
[    1.038288] scsi3 : ahci
[    1.038336] scsi4 : ahci
[    1.038381] scsi5 : ahci
[    1.038421] ata1: SATA max UDMA/133 abar m2048@0xf1c08000 port 0xf1c08100 irq 49
[    1.038424] ata2: SATA max UDMA/133 abar m2048@0xf1c08000 port 0xf1c08180 irq 49
[    1.038425] ata3: DUMMY
[    1.038426] ata4: DUMMY
[    1.038428] ata5: SATA max UDMA/133 abar m2048@0xf1c08000 port 0xf1c08300 irq 49
[    1.038429] ata6: DUMMY
[    1.057549] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.190161] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.190164] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.190483] hub 1-1:1.0: USB hub found
[    1.190713] hub 1-1:1.0: 6 ports detected
[    1.301587] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.357578] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.387869] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    1.388240] ata1.00: ATA-8: HGST HTS725050A7E630, GH2OA420, max UDMA/133
[    1.388250] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.389353] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    1.389737] ata1.00: configured for UDMA/133
[    1.389983] scsi 0:0:0:0: Direct-Access     ATA      HGST HTS725050A7 GH2O PQ: 0 ANSI: 5
[    1.390130] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.390139] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.390141] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.390183] sd 0:0:0:0: [sda] Write Protect is off
[    1.390185] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.390201] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.434284] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.434294] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.434646] hub 2-1:1.0: USB hub found
[    1.434693] hub 2-1:1.0: 8 ports detected
[    1.454587]  sda: sda1 sda2 < sda5 >
[    1.455076] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.497529] tsc: Refined TSC clocksource calibration: 2693.884 MHz
[    1.505763] usb 1-1.4: new high-speed USB device number 3 using ehci-pci
[    1.599483] usb 1-1.4: New USB device found, idVendor=0408, idProduct=2fb1
[    1.599494] usb 1-1.4: New USB device strings: Mfr=3, Product=2, SerialNumber=0
[    1.599500] usb 1-1.4: Product: Laptop_Integrated_Webcam_2HDM
[    1.599504] usb 1-1.4: Manufacturer: CN07CN2C7866418A0D9CA00
[    1.705700] usb 2-1.2: new low-speed USB device number 3 using ehci-pci
[    1.709460] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.711640] ata2.00: ATAPI: HL-DT-STDVD+/-RW GT32N, A203, max UDMA/100
[    1.715235] ata2.00: configured for UDMA/100
[    1.718173] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GT32N    A203 PQ: 0 ANSI: 5
[    1.722313] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.722321] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.722533] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.722679] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.803966] usb 2-1.2: New USB device found, idVendor=046d, idProduct=c043
[    1.803970] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.803972] usb 2-1.2: Product: USB-PS/2 Optical Mouse
[    1.803974] usb 2-1.2: Manufacturer: Logitech
[    1.807053] hidraw: raw HID events driver (C) Jiri Kosina
[    1.812117] usbcore: registered new interface driver usbhid
[    1.812119] usbhid: USB HID core driver
[    1.813217] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input5
[    1.813327] hid-generic 0003:046D:C043.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1.2/input0
[    1.873630] usb 2-1.5: new full-speed USB device number 4 using ehci-pci
[    1.970484] usb 2-1.5: New USB device found, idVendor=8086, idProduct=0189
[    1.970494] usb 2-1.5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.041351] ata5: SATA link down (SStatus 0 SControl 300)
[    2.497205] Switched to clocksource tsc
[    2.501138] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   12.914217] Adding 8278012k swap on /dev/sda5.  Priority:-1 extents:1 across:8278012k FS
[   13.081891] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.136903] systemd-udevd[305]: starting version 204
[   13.261742] lp: driver loaded but no devices found
[   13.290711] [drm] Initialized drm 1.1.0 20060810
[   13.291263] mei_me 0000:00:16.0: setting latency timer to 64
[   13.291305] mei_me 0000:00:16.0: irq 50 for MSI/MSI-X
[   13.303231] [drm] Memory usable by graphics device = 2048M
[   13.303236] i915 0000:00:02.0: setting latency timer to 64
[   13.326908] i915 0000:00:02.0: irq 51 for MSI/MSI-X
[   13.326915] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   13.326916] [drm] Driver supports precise vblank timestamp query.
[   13.326930] ACPI Warning: \_SB_.PCI0.GFX0._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20130517/nsarguments-95)
[   13.326951] ACPI Warning: \_SB_.PCI0.GFX0._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20130517/nsarguments-95)
[   13.326961] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20130517/nsarguments-95)
[   13.326983] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20130517/nsarguments-95)
[   13.327035] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   13.327036] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0
[   13.353917] [drm] Wrong MCH_SSKPD value: 0x16040307
[   13.353920] [drm] This can cause pipe underruns and display issues.
[   13.353921] [drm] Please upgrade your BIOS to fix this.
[   13.398772] wmi: Mapper loaded
[   13.411441] cfg80211: Calling CRDA to update world regulatory domain
[   13.416645] Intel(R) Wireless WiFi driver for Linux, in-tree:
[   13.416648] Copyright(c) 2003-2013 Intel Corporation
[   13.416907] iwlwifi 0000:03:00.0: irq 52 for MSI/MSI-X
[   13.422330] ACPI Warning: \_SB_.PCI0.GFX0._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20130517/nsarguments-95)
[   13.422399] ACPI Warning: \_SB_.PCI0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
[   13.422564] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20130517/nsarguments-95)
[   13.422593] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
[   13.422847] VGA switcheroo: detected Optimus DSM method \_SB_.PCI0.PEG0.PEGP handle
[   13.422874] nouveau 0000:01:00.0: enabling device (0006 -> 0007)
[   13.439232] microcode: CPU0 sig=0x206a7, pf=0x10, revision=0x1a
[   13.439876] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
[   13.455574] fbcon: inteldrmfb (fb0) is primary device
[   13.503646] type=1400 audit(1392149878.220:2): apparmor="STATUS" operation="profile_load" parent=368 profile="unconfined" name="/sbin/dhclient" pid=389 comm="apparmor_parser"
[   13.503650] type=1400 audit(1392149878.220:3): apparmor="STATUS" operation="profile_load" parent=368 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=389 comm="apparmor_parser"
[   13.503653] type=1400 audit(1392149878.220:4): apparmor="STATUS" operation="profile_load" parent=368 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=389 comm="apparmor_parser"
[   13.504127] type=1400 audit(1392149878.220:5): apparmor="STATUS" operation="profile_replace" parent=368 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=389 comm="apparmor_parser"
[   13.504131] type=1400 audit(1392149878.220:6): apparmor="STATUS" operation="profile_replace" parent=368 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=389 comm="apparmor_parser"
[   13.504388] type=1400 audit(1392149878.220:7): apparmor="STATUS" operation="profile_replace" parent=368 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=389 comm="apparmor_parser"
[   13.734604] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[   13.747080] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   13.747082] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   13.747083] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   13.747083] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
[   13.747085] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1030 BGN, REV=0xB0
[   13.747140] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   13.766810] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.938647] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   14.269548] Console: switching to colour frame buffer device 240x67
[   14.273029] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   14.273030] i915 0000:00:02.0: registered panic notifier
[   14.273178] ACPI Exception: AE_NOT_FOUND, Evaluating _DOD (20130517/video-1264)
[   14.273182] ACPI: Video Device [PEGP] (multi-head: no  rom: yes  post: no)
[   14.273524] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:33/LNXVIDEO:00/input/input6
[   14.288283] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   14.291997] acpi device:35: registered as cooling_device4
[   14.292221] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   14.292297] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input7
[   14.293559] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   14.293973] snd_hda_intel 0000:00:1b.0: irq 53 for MSI/MSI-X
[   14.294398] nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0x0c1a00a1
[   14.294402] nouveau  [  DEVICE][0000:01:00.0] Chipset: GF108 (NVC1)
[   14.294404] nouveau  [  DEVICE][0000:01:00.0] Family : NVC0
[   14.296273] nouveau  [   VBIOS][0000:01:00.0] checking PRAMIN for image...
[   14.306003] nouveau  [   VBIOS][0000:01:00.0] ... signature not found
[   14.306005] nouveau  [   VBIOS][0000:01:00.0] checking PROM for image...
[   14.306073] nouveau  [   VBIOS][0000:01:00.0] ... signature not found
[   14.306074] nouveau  [   VBIOS][0000:01:00.0] checking ACPI for image...
[   14.312467] input: Dell WMI hotkeys as /devices/virtual/input/input8
[   14.312529] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xa40000/0x8a0400, board id: 3655, fw id: 662324
[   14.316366] hda_codec: ALC665: SKU not ready 0x598301f0
[   14.316655] autoconfig: line_outs=1 (0x15/0x0/0x0/0x0/0x0) type:speaker
[   14.316656]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   14.316657]    hp_outs=2 (0x1b/0x19/0x0/0x0/0x0)
[   14.316658]    mono: mono_out=0x0
[   14.316658]    dig-out=0x1e/0x0
[   14.316659]    inputs:
[   14.316660]      Mic=0x1a
[   14.316661]      Internal Mic=0x12
[   14.316662] realtek: No valid SSID, checking pincfg 0x598301f0 for NID 0x1d
[   14.316663] realtek: Enable default setup for auto mode as fallback
[   14.319417] microcode: CPU1 sig=0x206a7, pf=0x10, revision=0x1a
[   14.327343] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   14.327418] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   14.327475] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   14.327530] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   14.327839] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20130517/utaddress-251)
[   14.327845] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.327849] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[   14.327853] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20130517/utaddress-251)
[   14.327856] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.327857] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[   14.327860] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20130517/utaddress-251)
[   14.327863] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.327864] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[   14.327867] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20130517/utaddress-251)
[   14.327870] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.327871] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   14.331516] microcode: CPU2 sig=0x206a7, pf=0x10, revision=0x1a
[   14.336537] microcode: CPU3 sig=0x206a7, pf=0x10, revision=0x1a
[   14.336997] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   14.375568] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input13
[   14.678328] cfg80211: World regulatory domain updated:
[   14.678332] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.678334] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.678335] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.678337] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.678338] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.678339] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.853584] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[   14.892069] init: failsafe main process (673) killed by TERM signal
[   14.962765] Bluetooth: Core ver 2.16
[   14.962778] NET: Registered protocol family 31
[   14.962779] Bluetooth: HCI device and connection manager initialized
[   14.962787] Bluetooth: HCI socket layer initialized
[   14.962789] Bluetooth: L2CAP socket layer initialized
[   14.962794] Bluetooth: SCO socket layer initialized
[   15.010007] usbcore: registered new interface driver btusb
[   15.139316] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.139319] Bluetooth: BNEP filters: protocol multicast
[   15.139328] Bluetooth: BNEP socket layer initialized
[   15.139723] Bluetooth: RFCOMM TTY layer initialized
[   15.139730] Bluetooth: RFCOMM socket layer initialized
[   15.139731] Bluetooth: RFCOMM ver 1.11
[   15.172775] Linux video capture interface: v2.00
[   15.225424] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_2HDM (0408:2fb1)
[   15.504636] uvcvideo: No streaming interface found for terminal 6.
[   15.504671] input: Laptop_Integrated_Webcam_2HDM as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input14
[   15.504741] usbcore: registered new interface driver uvcvideo
[   15.504743] USB Video Class driver (1.1.1)
[   15.541305] init: avahi-cups-reload main process (786) terminated with status 1
[   15.682841] ppdev: user-space parallel port driver
[   15.691385] type=1400 audit(1392149880.408:8): apparmor="STATUS" operation="profile_load" parent=797 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=801 comm="apparmor_parser"
[   15.691390] type=1400 audit(1392149880.408:9): apparmor="STATUS" operation="profile_load" parent=797 profile="unconfined" name="/usr/sbin/cupsd" pid=801 comm="apparmor_parser"
[   15.691988] type=1400 audit(1392149880.408:10): apparmor="STATUS" operation="profile_replace" parent=797 profile="unconfined" name="/usr/sbin/cupsd" pid=801 comm="apparmor_parser"
[   15.925236] nouveau  [   VBIOS][0000:01:00.0] ... appears to be valid
[   15.925240] nouveau  [   VBIOS][0000:01:00.0] using image from ACPI
[   15.925324] nouveau  [   VBIOS][0000:01:00.0] BIT signature found
[   15.925326] nouveau  [   VBIOS][0000:01:00.0] version 70.08.44.00.11
[   15.925525] nouveau  [ DEVINIT][0000:01:00.0] adaptor not initialised
[   15.925527] nouveau  [   VBIOS][0000:01:00.0] running init tables
[   16.039980] nouveau  [     PFB][0000:01:00.0] RAM type: DDR3
[   16.039983] nouveau  [     PFB][0000:01:00.0] RAM size: 1024 MiB
[   16.039984] nouveau  [     PFB][0000:01:00.0]    ZCOMP: 0 tags
[   16.064315] nouveau  [  PTHERM][0000:01:00.0] FAN control: none / external
[   16.064323] nouveau  [  PTHERM][0000:01:00.0] fan management: disabled
[   16.064328] nouveau  [  PTHERM][0000:01:00.0] internal sensor: yes
[   16.067371] vga_switcheroo: enabled
[   16.067455] [TTM] Zone  kernel: Available graphics memory: 4034114 kiB
[   16.067456] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[   16.067457] [TTM] Initializing pool allocator
[   16.067460] [TTM] Initializing DMA pool allocator
[   16.067468] nouveau  [     DRM] VRAM: 1024 MiB
[   16.067469] nouveau  [     DRM] GART: 1048576 MiB
[   16.067473] nouveau  [     DRM] TMDS table version 2.0
[   16.067474] nouveau  [     DRM] DCB version 4.0
[   16.067476] nouveau  [     DRM] DCB outp 00: 02014300 00000000
[   16.067477] nouveau  [     DRM] DCB outp 01: 02021362 00020010
[   16.067478] nouveau  [     DRM] DCB conn 00: 00000340
[   16.067480] nouveau  [     DRM] DCB conn 01: 00001061
[   16.067481] nouveau  [     DRM] DCB conn 02: 00000147
[   16.067482] nouveau  [     DRM] DCB conn 03: 00002346
[   16.067483] nouveau  [     DRM] DCB conn 04: 00000400
[   16.067484] nouveau  [     DRM] DCB conn 05: 00000210
[   16.067484] nouveau  [     DRM] DCB conn 06: 00000211
[   16.067485] nouveau  [     DRM] DCB conn 07: 00000213
[   16.068101] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   16.068102] [drm] No driver support for vblank timestamp query.
[   16.068104] nouveau  [     DRM] ACPI backlight interface available, not registering our own
[   16.068281] nouveau  [     DRM] 3 available performance level(s)
[   16.068283] nouveau  [     DRM] 0: core 50MHz shader 101MHz memory 135MHz voltage 830mV
[   16.068285] nouveau  [     DRM] 1: core 202MHz shader 405MHz memory 324MHz voltage 830mV
[   16.068286] nouveau  [     DRM] 3: core 672MHz shader 1344MHz memory 900MHz voltage 980mV
[   16.068288] nouveau  [     DRM] c: core 202MHz shader 405MHz memory 324MHz voltage 980mV
[   16.073317] nouveau  [     DRM] MM: using COPY0 for buffer copies
[   16.116034] nouveau  [     DRM] allocated 1024x768 fb: 0x60000, bo ffff88022a43a400
[   16.116123] nouveau 0000:01:00.0: fb1: nouveaufb frame buffer device
[   16.116127] [drm] Initialized nouveau 1.1.1 20120801 for 0000:01:00.0 on minor 1
[   16.266488] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   16.273222] iwlwifi 0000:03:00.0: Radio type=0x2-0x2-0x1
[   16.340691] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   16.347342] iwlwifi 0000:03:00.0: Radio type=0x2-0x2-0x1
[   16.403309] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.403520] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.648485] r8169 0000:06:00.0 eth0: link down
[   16.648527] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.648836] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.326449] type=1400 audit(1392149882.044:11): apparmor="STATUS" operation="profile_replace" parent=912 profile="unconfined" name="/sbin/dhclient" pid=920 comm="apparmor_parser"
[   17.694741] wlan0: authenticate with 44:32:c8:9c:2d:77
[   17.707198] wlan0: send auth to 44:32:c8:9c:2d:77 (try 1/3)
[   17.709907] wlan0: authenticated
[   17.712343] wlan0: associate with 44:32:c8:9c:2d:77 (try 1/3)
[   17.715588] wlan0: RX AssocResp from 44:32:c8:9c:2d:77 (capab=0x411 status=0 aid=1)
[   17.717529] wlan0: associated
[   17.717547] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   21.208030] postgres (1455): /proc/1455/oom_adj is deprecated, please use /proc/1455/oom_score_adj instead.
[   25.324747] Non-volatile memory driver v1.3
[   25.610331] init: plymouth-stop pre-start process (1952) terminated with status 1
[  159.991223] wlan0: deauthenticating from 44:32:c8:9c:2d:77 by local choice (reason=3)
[  160.002883] cfg80211: Calling CRDA to update world regulatory domain
[  160.005683] cfg80211: World regulatory domain updated:
[  160.005693] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  160.005698] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  160.005702] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  160.005706] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  160.005709] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  160.005712] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  161.929883] PM: Syncing filesystems ... done.
[  162.169738] PM: Preparing system for mem sleep
[  162.454406] Freezing user space processes ... (elapsed 0.001 seconds) done.
[  162.456262] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[  162.457536] PM: Entering mem sleep
[  162.457569] Suspending console(s) (use no_console_suspend to debug)
[  162.457774] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  162.457895] sd 0:0:0:0: [sda] Stopping disk
[  162.504679] nouveau  [     DRM] suspending fbcon...
[  162.504681] nouveau  [     DRM] suspending display...
[  162.504687] nouveau  [     DRM] unpinning framebuffer(s)...
[  162.504753] nouveau  [     DRM] evicting buffers...
[  162.504837] mei_me 0000:00:16.0: suspend
[  162.528453] nouveau  [     DRM] waiting for kernel channels to go idle...
[  162.528478] nouveau  [     DRM] suspending client object trees...
[  162.528765] nouveau  [     DRM] suspending kernel object tree...
[  163.289701] nouveau 0000:01:00.0: power state changed by ACPI to D3cold
[  163.289737] PM: suspend of devices complete after 832.335 msecs
[  163.289874] PM: late suspend of devices complete after 0.135 msecs
[  163.290078] xhci_hcd 0000:04:00.0: System wakeup enabled by ACPI
[  163.321636] ehci-pci 0000:00:1d.0: System wakeup enabled by ACPI
[  163.337783] ehci-pci 0000:00:1a.0: System wakeup enabled by ACPI
[  163.369541] PM: noirq suspend of devices complete after 79.691 msecs
[  163.369762] ACPI: Preparing to enter system sleep state S3
[  163.371748] PM: Saving platform NVS memory
[  163.372340] Disabling non-boot CPUs ...
[  163.373802] smpboot: CPU 1 is now offline
[  163.477476] smpboot: CPU 2 is now offline
[  163.477807] Broke affinity for irq 16
[  163.477809] Broke affinity for irq 23
[  163.477811] Broke affinity for irq 43
[  163.477813] Broke affinity for irq 44
[  163.477814] Broke affinity for irq 45
[  163.477816] Broke affinity for irq 46
[  163.477817] Broke affinity for irq 47
[  163.477820] Broke affinity for irq 52
[  163.581441] smpboot: CPU 3 is now offline
[  163.582706] ACPI: Low-level resume complete
[  163.582744] PM: Restoring platform NVS memory
[  163.583395] CPU0: Thermal monitoring handled by SMI
[  163.583423] Enabling non-boot CPUs ...
[  163.583453] smpboot: Booting Node 0 Processor 1 APIC 0x1
[  163.594411] Disabled fast string operations
[  163.594423] CPU1: Thermal monitoring handled by SMI
[  163.596769] CPU1 is up
[  163.596784] smpboot: Booting Node 0 Processor 2 APIC 0x2
[  163.607718] Disabled fast string operations
[  163.607730] CPU2: Thermal monitoring handled by SMI
[  163.610056] CPU2 is up
[  163.610070] smpboot: Booting Node 0 Processor 3 APIC 0x3
[  163.621005] Disabled fast string operations
[  163.621016] CPU3: Thermal monitoring handled by SMI
[  163.623380] CPU3 is up
[  163.626834] ACPI: Waking up from system sleep state S3
[  163.683250] ehci-pci 0000:00:1a.0: System wakeup disabled by ACPI
[  163.715229] ehci-pci 0000:00:1d.0: System wakeup disabled by ACPI
[  163.731320] nouveau 0000:01:00.0: power state changed by ACPI to D0
[  163.779229] xhci_hcd 0000:04:00.0: System wakeup disabled by ACPI
[  163.779372] PM: noirq resume of devices complete after 140.792 msecs
[  163.779495] PM: early resume of devices complete after 0.090 msecs
[  163.779520] i915 0000:00:02.0: setting latency timer to 64
[  163.779550] mei_me 0000:00:16.0: irq 48 for MSI/MSI-X
[  163.779613] ehci-pci 0000:00:1a.0: setting latency timer to 64
[  163.779636] ahci 0000:00:1f.2: setting latency timer to 64
[  163.779729] snd_hda_intel 0000:00:1b.0: irq 50 for MSI/MSI-X
[  163.779749] ehci-pci 0000:00:1d.0: setting latency timer to 64
[  163.779768] nouveau  [     DRM] re-enabling device...
[  163.779777] nouveau  [     DRM] resuming kernel object tree...
[  163.779783] nouveau  [   VBIOS][0000:01:00.0] running init tables
[  163.791291] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[  163.792340] [drm] Wrong MCH_SSKPD value: 0x16040307
[  163.792341] [drm] This can cause pipe underruns and display issues.
[  163.792341] [drm] Please upgrade your BIOS to fix this.
[  163.941564] nouveau  [     DRM] resuming client object trees...
[  163.941660] nouveau  [     DRM] resuming display...
[  163.991070] usb 1-1.4: reset high-speed USB device number 3 using ehci-pci
[  164.123064] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  164.126562] ata2.00: configured for UDMA/100
[  164.131054] ata5: SATA link down (SStatus 0 SControl 300)
[  164.343165] usb 2-1.2: reset low-speed USB device number 3 using ehci-pci
[  164.695049] usb 2-1.5: reset full-speed USB device number 4 using ehci-pci
[  164.789760] btusb 2-1.5:1.0: no reset_resume for driver btusb?
[  164.789763] btusb 2-1.5:1.1: no reset_resume for driver btusb?
[  165.690577] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  165.691676] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[  165.693205] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[  165.693478] ata1.00: configured for UDMA/133
[  165.706664] sd 0:0:0:0: [sda] Starting disk
[  165.727635] PM: resume of devices complete after 1948.753 msecs
[  165.728039] PM: Finishing wakeup.
[  165.728040] Restarting tasks ... done.
[  165.736960] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[  165.744753] video LNXVIDEO:00: Restoring backlight state
[  165.744757] video LNXVIDEO:01: Restoring backlight state
[  165.753785] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[  165.760495] iwlwifi 0000:03:00.0: Radio type=0x2-0x2-0x1
[  165.826312] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  167.027520] wlan0: authenticate with 44:32:c8:9c:2d:77
[  167.037221] wlan0: send auth to 44:32:c8:9c:2d:77 (try 1/3)
[  167.039890] wlan0: authenticated
[  167.042153] wlan0: associate with 44:32:c8:9c:2d:77 (try 1/3)
[  167.045416] wlan0: RX AssocResp from 44:32:c8:9c:2d:77 (capab=0x411 status=0 aid=1)
[  167.047499] wlan0: associated
[  167.047524] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  167.181704] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[  167.181936] r8169 0000:06:00.0: irq 53 for MSI/MSI-X
[  167.182555] r8169 0000:06:00.0 eth0: RTL8168e/8111e at 0xffffc90000c2c000, 00:00:00:00:00:00, XID 0c200000 IRQ 53
[  167.182559] r8169 0000:06:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[  167.186019] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

```


/var/log/pm-suspend.log (current session):


```

Initial commandline parameters: 
Tue Feb 11 21:20:25 CET 2014: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.




Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.




Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux typically-laptop 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
nvram                  14362  0 
parport_pc             32701  0 
ppdev                  17671  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40499  1 uvcvideo
videodev              133509  2 uvcvideo,videobuf2_core
rfcomm                 69130  12 
bnep                   19704  2 
btusb                  28267  0 
bluetooth             372041  22 bnep,btusb,rfcomm
binfmt_misc            17468  1 
x86_pkg_temp_thermal    14162  0 
joydev                 17377  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138567  0 
kvm                   431720  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec_hdmi     41117  1 
snd_hda_codec_realtek    55704  1 
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            17369  0 
dcdbas                 14847  1 dell_laptop
arc4                   12608  2 
iwldvm                237469  0 
mac80211              597268  1 iwldvm
microcode              23576  0 
psmouse                97655  0 
serio_raw              13413  0 
nouveau               943717  1 
iwlwifi               165675  1 iwldvm
cfg80211              480503  3 iwlwifi,mac80211,iwldvm
lpc_ich                21080  0 
mxm_wmi                13021  1 nouveau
ttm                    84169  1 nouveau
wmi                    19070  3 dell_wmi,mxm_wmi,nouveau
snd_hda_intel          48171  3 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
i915                  661261  3 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
video                  19318  2 i915,nouveau
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
drm_kms_helper         52710  2 i915,nouveau
mei_me                 18421  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
mei                    77782  1 mei_me
snd_timer              29433  2 snd_pcm,snd_seq
drm                   297056  7 ttm,i915,drm_kms_helper,nouveau
snd                    69141  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i2c_algo_bit           13413  2 i915,nouveau
soundcore              12680  1 snd
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 53014  0 
hid                   105858  2 hid_generic,usbhid
ahci                   25819  2 
r8169                  67581  0 
libahci                31928  1 ahci
mii                    13934  1 r8169
             total       used       free     shared    buffers     cached
Mem:       8068228    1696392    6371836          0      96128     819212
-/+ buffers/cache:     781052    7287176
Swap:      8278012          0    8278012
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.




Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.




Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.




Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.




Running hook /usr/lib/pm-utils/sleep.d/49tlp suspend suspend:
grep: /sys/devices/platform/dock.?/type: No such file or directory
/usr/lib/pm-utils/sleep.d/49tlp suspend suspend: success.




Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.




Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.




[B]Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module r8169...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.[/B]




Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.




Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.




Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.




Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.




Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.




Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.




Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.




Running hook /etc/pm/sleep.d/network-manager-resume suspend suspend:
/etc/pm/sleep.d/network-manager-resume suspend suspend: success.




Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.




Tue Feb 11 21:20:26 CET 2014: performing suspend
Tue Feb 11 21:20:39 CET 2014: Awake.
Tue Feb 11 21:20:39 CET 2014: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.




Running hook /etc/pm/sleep.d/network-manager-resume resume suspend:
/etc/pm/sleep.d/network-manager-resume resume suspend: success.




Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.




Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.




Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.




Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:




/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254




/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.




Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.




Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.




Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.




[B]Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.[/B]




Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Selected interface 'wlan0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.




Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.




Running hook /usr/lib/pm-utils/sleep.d/49tlp resume suspend:
/usr/lib/pm-utils/sleep.d/49tlp resume suspend: success.




Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.




Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.




Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.




Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.




Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.




Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.




Tue Feb 11 21:20:41 CET 2014: Finished.

```


cat /var/log/syslog | grep PM: (current session):


```

Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbac8f000-0xbacabfff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbacac000-0xbacb8fff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbacb9000-0xbadcefff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbadcf000-0xbadcffff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbadd0000-0xbadfafff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbadfb000-0xbadfcfff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbadfd000-0xbadfefff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbadff000-0xbae01fff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbae02000-0xbae09fff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbae0a000-0xbae1afff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbae1b000-0xbaf17fff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbaf18000-0xbaf1bfff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbaf1c000-0xbaf1efff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbaf1f000-0xbaf9efff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbaf9f000-0xbaffefff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb000000-0xbf9fffff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbfa00000-0xf7ffffff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed07fff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed08000-0xfed08fff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed09000-0xfed0ffff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed19fff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffd7ffff]
Feb 11 21:16:34 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffd80000-0xffffffff]
Feb 11 21:16:34 typically-laptop kernel: [    0.156922] PM: Registering ACPI NVS region [mem 0xbacac000-0xbacb8fff] (53248 bytes)
Feb 11 21:16:34 typically-laptop kernel: [    0.156925] PM: Registering ACPI NVS region [mem 0xbadcf000-0xbadcffff] (4096 bytes)
Feb 11 21:16:34 typically-laptop kernel: [    0.156926] PM: Registering ACPI NVS region [mem 0xbadfb000-0xbadfcfff] (8192 bytes)
Feb 11 21:16:34 typically-laptop kernel: [    0.156927] PM: Registering ACPI NVS region [mem 0xbadff000-0xbae01fff] (12288 bytes)
Feb 11 21:16:34 typically-laptop kernel: [    0.156928] PM: Registering ACPI NVS region [mem 0xbae0a000-0xbae1afff] (69632 bytes)
Feb 11 21:16:34 typically-laptop kernel: [    0.156930] PM: Registering ACPI NVS region [mem 0xbaf18000-0xbaf1bfff] (16384 bytes)
Feb 11 21:16:34 typically-laptop kernel: [    0.156931] PM: Registering ACPI NVS region [mem 0xbaf1f000-0xbaf9efff] (524288 bytes)
Feb 11 21:16:34 typically-laptop kernel: [    0.775668] PM: Hibernation image not present or could not be loaded.
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbac8f000-0xbacabfff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbacac000-0xbacb8fff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbacb9000-0xbadcefff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbadcf000-0xbadcffff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbadd0000-0xbadfafff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbadfb000-0xbadfcfff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbadfd000-0xbadfefff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbadff000-0xbae01fff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbae02000-0xbae09fff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbae0a000-0xbae1afff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbae1b000-0xbaf17fff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbaf18000-0xbaf1bfff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbaf1c000-0xbaf1efff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbaf1f000-0xbaf9efff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbaf9f000-0xbaffefff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbb000000-0xbf9fffff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbfa00000-0xf7ffffff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed07fff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed08000-0xfed08fff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed09000-0xfed0ffff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed19fff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffd7ffff]
Feb 11 21:17:59 typically-laptop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffd80000-0xffffffff]
Feb 11 21:17:59 typically-laptop kernel: [    0.156961] PM: Registering ACPI NVS region [mem 0xbacac000-0xbacb8fff] (53248 bytes)
Feb 11 21:17:59 typically-laptop kernel: [    0.156964] PM: Registering ACPI NVS region [mem 0xbadcf000-0xbadcffff] (4096 bytes)
Feb 11 21:17:59 typically-laptop kernel: [    0.156965] PM: Registering ACPI NVS region [mem 0xbadfb000-0xbadfcfff] (8192 bytes)
Feb 11 21:17:59 typically-laptop kernel: [    0.156966] PM: Registering ACPI NVS region [mem 0xbadff000-0xbae01fff] (12288 bytes)
Feb 11 21:17:59 typically-laptop kernel: [    0.156967] PM: Registering ACPI NVS region [mem 0xbae0a000-0xbae1afff] (69632 bytes)
Feb 11 21:17:59 typically-laptop kernel: [    0.156969] PM: Registering ACPI NVS region [mem 0xbaf18000-0xbaf1bfff] (16384 bytes)
Feb 11 21:17:59 typically-laptop kernel: [    0.156970] PM: Registering ACPI NVS region [mem 0xbaf1f000-0xbaf9efff] (524288 bytes)
Feb 11 21:17:59 typically-laptop kernel: [    0.775802] PM: Hibernation image not present or could not be loaded.
Feb 11 21:20:26 typically-laptop kernel: [  161.929883] PM: Syncing filesystems ... done.
Feb 11 21:20:26 typically-laptop kernel: [  162.169738] PM: Preparing system for mem sleep
Feb 11 21:20:39 typically-laptop kernel: [  162.457536] PM: Entering mem sleep
Feb 11 21:20:39 typically-laptop kernel: [  163.289737] PM: suspend of devices complete after 832.335 msecs
Feb 11 21:20:39 typically-laptop kernel: [  163.289874] PM: late suspend of devices complete after 0.135 msecs
Feb 11 21:20:39 typically-laptop kernel: [  163.369541] PM: noirq suspend of devices complete after 79.691 msecs
Feb 11 21:20:39 typically-laptop kernel: [  163.371748] PM: Saving platform NVS memory
Feb 11 21:20:39 typically-laptop kernel: [  163.582744] PM: Restoring platform NVS memory
Feb 11 21:20:39 typically-laptop kernel: [  163.779372] PM: noirq resume of devices complete after 140.792 msecs
Feb 11 21:20:39 typically-laptop kernel: [  163.779495] PM: early resume of devices complete after 0.090 msecs
Feb 11 21:20:39 typically-laptop kernel: [  165.727635] PM: resume of devices complete after 1948.753 msecs
Feb 11 21:20:39 typically-laptop kernel: [  165.728039] PM: Finishing wakeup.

```

I've highlighted the "75modules" part of pm-suspend.log. These are (for suspend and wakeup):

```

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module r8169...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

```

Reports no issues there...

Thanks again!

---

### Post by Toz on 2014-02-11
> r8169 0000:06:00.0: can't disable ASPM; **[COLOR="#FF0000"]OS doesn't have ASPM control[/COLOR]**
And from your dmesg:
> [    0.204020] \_SB_.PCI0:_OSC invalid UUID
[    0.204021] _OSC request data:1 8 0 
[    0.204047] \_SB_.PCI0:_OSC invalid UUID
[    0.204048] _OSC request data:1 1f 0 
[    0.204051] acpi PNP0A08:00: ACPI _OSC support notification failed, **[COLOR="#FF0000"]disabling PCIe ASPM[/COLOR]**
[    0.204052] acpi PNP0A08:00: Unable to request _OSC control (_OSC support mask: 0x08)
And [according to Matthew Garret]("https://bugzilla.redhat.com/show_bug.cgi?id=802224"):
> Your firmware refuses to hand over control of PCIe functionality to the kernel, which is something the spec allows it to do. This isn't a bug.
This looks relevant.



> [    0.000000] DMI: Dell Inc.          Dell System XPS L502X/0NJT03, **[COLOR="#FF0000"]BIOS A06 07/20/2011[/COLOR]**
Have you checked to see if a bios update is available?

---

### Post by typically2 on 2014-02-12
Hi again,

I am a bit reluctant to risk a BIOS upgrade because Dell doesn't officially support Linux, and I am dubious that they've changed this behaviour (given that they're geared towards Windows systems). Also, I'm not sure ASPM is actually the issue with eth0, because when I disable it entirely entirely using the kernel parameter "pcie_aspm=off" (as [here]("http://askubuntu.com/questions/202308/acpi-osc-control")), I get no ASPM error:

dmesg | grep 'eth0\|r8169'    (>120s is after resume)

```
[    0.980210] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.980421] r8169 0000:06:00.0: irq 48 for MSI/MSI-X
[    0.980538] r8169 0000:06:00.0 eth0: RTL8168e/8111e at 0xffffc90000c2c000, 14:fe:b5:c1:b1:91, XID 0c200000 IRQ 48
[    0.980540] r8169 0000:06:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   13.437102] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.949605] r8169 0000:06:00.0 eth0: link down
[   16.949642] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.949937] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.636590] r8169 0000:06:00.0 eth0: link up
[   18.636598] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  120.889172] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[  120.889388] r8169 0000:06:00.0: irq 53 for MSI/MSI-X
[  120.889557] r8169 0000:06:00.0 eth0: RTL8168e/8111e at 0xffffc90000c2c000, 00:00:00:00:00:00, XID 0c200000 IRQ 53
[  120.889560] r8169 0000:06:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[  120.893010] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready


```

...but the issue persists. The link never becomes ready. In the third-from-last line the address is being set to zeros, and the IRQ is different than on startup. Is that relevant?

Do you think a BIOS update would be worth doing?

Thanks for the ideas so far!

---

### Post by Toz on 2014-02-12
Not sure if you've seen these already, but here are a couple of bug reports that look related:
- [https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1184262]("https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1184262")
- [https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1252121]("https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1252121")

The first ones references a PPA that might be helpful. Otherwise, it seems that you have tried some of the suggestions there that have worked for others. I'm afraid that I don't know what more to add. It sure does look like some sort of bug you are experiencing.

---

### Post by typically2 on 2014-02-19
Thanks for the references. I've checked but the problems there appear to be with wireless, and also appear to be fixed by restarting the network manager. 

Just as an update, for this bug:

[https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1252121](https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1252121)

it was suggested to test whether the problem is due only to the lid closing, which behaves somewhat differently than a direct sleep call. However, the call

```

sudo gdbus call -y -d org.freedesktop.login1 -o /org/freedesktop/login1 -m org.freedesktop.login1.Manager.Suspend true

```

results in the same issue. I'll consider filing a bug report I guess.

---

### Post by luke_lukem on 2014-02-21
Hi everyone, i'd like to share my results around this bug, although it seems some update just solved the problem !
Before today, i found a workaround: disabling my ethernet connection from the network manager icon, and then suspend. After resuming, enabling ethernet again.
Today i tested again a few times, but it seems resolved :)
Cheers!
--------- Edit 2014-02-24 ----------
Sorry, the bug is back!
Jus like it happens to you, i had to kill the "NetworkManager" process, then the nm-applet restarts it and my connection is back online.
Sorry, nothing helpful so far ¬_¬

---


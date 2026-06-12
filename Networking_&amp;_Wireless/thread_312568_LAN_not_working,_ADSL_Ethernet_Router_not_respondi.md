---
title: "LAN not working, ADSL Ethernet Router not responding to PING (Host Unreachable)"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by RFMaster on 2006-12-04
Hi,
I have this problem, I've installed Xubuntu 6.10 Edgy Eft, on my second Harddisk, I also have Windows XP SP2 in my first Harddisk, I connect to the internet through a LAN with static IPs, my connection works fine with Win XP, but the ADSL modem-router doesn't answer to pings. I configured everything right and still it doesn't work.
 
PS: (sorry if I've posted irrelevant info, it's just that I'm new with Linux and I don't know what's relevant, and I want to give the most info I can to anyone who can help)
 
My computer's host name is:
rfmaster
IP: 10.0.0.2
subnet mask: 255.255.255.0
default gateway: 10.0.0.1
 
My modem-router's name is:
router
IP: 10.0.0.1
subnet mask: 255.255.255.0
 
I collected this information:
 
```

PING rfmaster (10.0.0.2) 56(84) bytes of data.
64 bytes from rfmaster (10.0.0.2): icmp_seq=1 ttl=64 time=0.482 ms
64 bytes from rfmaster (10.0.0.2): icmp_seq=2 ttl=64 time=0.131 ms
64 bytes from rfmaster (10.0.0.2): icmp_seq=3 ttl=64 time=0.145 ms
Warning: time of day goes back (-491086us), taking countermeasures.
Warning: time of day goes back (-490103us), taking countermeasures.
64 bytes from rfmaster (10.0.0.2): icmp_seq=4 ttl=64 time=0.000 ms
64 bytes from rfmaster (10.0.0.2): icmp_seq=5 ttl=64 time=0.775 ms
Warning: time of day goes back (-491045us), taking countermeasures.
64 bytes from rfmaster (10.0.0.2): icmp_seq=6 ttl=64 time=0.000 ms
Warning: time of day goes back (-80us), taking countermeasures.
64 bytes from rfmaster (10.0.0.2): icmp_seq=7 ttl=64 time=0.000 ms
64 bytes from rfmaster (10.0.0.2): icmp_seq=8 ttl=64 time=491 ms
Warning: time of day goes back (-90us), taking countermeasures.
64 bytes from rfmaster (10.0.0.2): icmp_seq=9 ttl=64 time=0.000 ms
Warning: time of day goes back (-491025us), taking countermeasures.
64 bytes from rfmaster (10.0.0.2): icmp_seq=10 ttl=64 time=0.000 ms
--- rfmaster ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 10966ms
rtt min/avg/max/mdev = 0.000/49.268/491.147/147.293 ms

```
 
```

PING router (10.0.0.1) 56(84) bytes of data.
From rfmaster (10.0.0.2) icmp_seq=1 Destination Host Unreachable
From rfmaster (10.0.0.2) icmp_seq=2 Destination Host Unreachable
From rfmaster (10.0.0.2) icmp_seq=3 Destination Host Unreachable
From rfmaster (10.0.0.2) icmp_seq=4 Destination Host Unreachable
From rfmaster (10.0.0.2) icmp_seq=5 Destination Host Unreachable
From rfmaster (10.0.0.2) icmp_seq=6 Destination Host Unreachable
From rfmaster (10.0.0.2) icmp_seq=7 Destination Host Unreachable
From rfmaster (10.0.0.2) icmp_seq=8 Destination Host Unreachable
From rfmaster (10.0.0.2) icmp_seq=9 Destination Host Unreachable
From rfmaster (10.0.0.2) icmp_seq=10 Destination Host Unreachable
From rfmaster (10.0.0.2) icmp_seq=11 Destination Host Unreachable
From rfmaster (10.0.0.2) icmp_seq=12 Destination Host Unreachable
--- router ping statistics ---
12 packets transmitted, 0 received, +12 errors, 100% packet loss, time 13470ms
, pipe 3

```
 
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use    Iface
10.0.0.0        0.0.0.0     255.255.255.0        U      0     0       0     eth0
0.0.0.0        10.0.0.1        0.0.0.0          UG      0     0       0     eth0

```
 
```

00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```
 
```

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:54:23:2A:22  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:54ff:fe23:2a22/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xef00 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:816 errors:0 dropped:0 overruns:0 frame:0
          TX packets:816 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43394 (42.3 KiB)  TX bytes:43394 (42.3 KiB)

```
 
```

rfmaster@rfmaster:~$ net lookup rfmaster
10.0.0.2
rfmaster@rfmaster:~$ net lookup router
10.0.0.1
rfmaster@rfmaster:~$ netstat
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ]         DGRAM                    4228     @/com/ubuntu/upstart
unix  2      [ ]         DGRAM                    4334     @/org/kernel/udev/udevd
unix  2      [ ]         DGRAM                    8412     @/org/freedesktop/hal/udev_event
unix  4      [ ]         DGRAM                    10483    /dev/log
unix  3      [ ]         STREAM     CONNECTED     12616    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12615    
unix  2      [ ]         DGRAM                    10947    
unix  3      [ ]         STREAM     CONNECTED     10722    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10721    
unix  2      [ ]         DGRAM                    10486    
unix  3      [ ]         STREAM     CONNECTED     10100    
unix  3      [ ]         STREAM     CONNECTED     10099    
unix  3      [ ]         STREAM     CONNECTED     10097    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10096    
unix  3      [ ]         STREAM     CONNECTED     10093    @/tmp/dbus-yU2C6XkUay
unix  3      [ ]         STREAM     CONNECTED     10092    
unix  3      [ ]         STREAM     CONNECTED     10086    @/tmp/dbus-yU2C6XkUay
unix  3      [ ]         STREAM     CONNECTED     10085    
unix  3      [ ]         STREAM     CONNECTED     10083    @/tmp/dbus-yU2C6XkUay
unix  3      [ ]         STREAM     CONNECTED     10082    
unix  3      [ ]         STREAM     CONNECTED     10080    /tmp/.ICE-unix/4091
unix  3      [ ]         STREAM     CONNECTED     10079    
unix  3      [ ]         STREAM     CONNECTED     10076    @/tmp/fam-rfmaster-
unix  3      [ ]         STREAM     CONNECTED     10075    
unix  3      [ ]         STREAM     CONNECTED     10073    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10072    
unix  3      [ ]         STREAM     CONNECTED     10066    /tmp/.ICE-unix/4091
unix  3      [ ]         STREAM     CONNECTED     10065    
unix  3      [ ]         STREAM     CONNECTED     10061    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10060    
unix  3      [ ]         STREAM     CONNECTED     10055    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10054    
unix  3      [ ]         STREAM     CONNECTED     10049    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10048    
unix  3      [ ]         STREAM     CONNECTED     10043    @/tmp/dbus-yU2C6XkUay
unix  3      [ ]         STREAM     CONNECTED     10042    
unix  3      [ ]         STREAM     CONNECTED     10039    @/tmp/fam-rfmaster-
unix  3      [ ]         STREAM     CONNECTED     10038    
unix  3      [ ]         STREAM     CONNECTED     10030    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10029    
unix  3      [ ]         STREAM     CONNECTED     10021    /tmp/.ICE-unix/4091
unix  3      [ ]         STREAM     CONNECTED     10020    
unix  3      [ ]         STREAM     CONNECTED     10018    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10017    
unix  3      [ ]         STREAM     CONNECTED     10011    /tmp/.ICE-unix/4091
unix  3      [ ]         STREAM     CONNECTED     10010    
unix  3      [ ]         STREAM     CONNECTED     10007    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10006    
unix  3      [ ]         STREAM     CONNECTED     10001    /tmp/orbit-rfmaster/linc-ffb-0-50883e829d1c4
unix  3      [ ]         STREAM     CONNECTED     10000    
unix  3      [ ]         STREAM     CONNECTED     9999     /tmp/orbit-rfmaster/linc-1025-0-20a9c8407aa0e
unix  3      [ ]         STREAM     CONNECTED     9992     
unix  2      [ ]         DGRAM                    9978     
unix  3      [ ]         STREAM     CONNECTED     9962     /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9961     
unix  3      [ ]         STREAM     CONNECTED     9950     /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9949     
unix  3      [ ]         STREAM     CONNECTED     9946     /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9945     
unix  3      [ ]         STREAM     CONNECTED     9944     
unix  3      [ ]         STREAM     CONNECTED     9943     
unix  2      [ ]         DGRAM                    9887     
unix  3      [ ]         STREAM     CONNECTED     9598     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9597     
unix  3      [ ]         STREAM     CONNECTED     9587     @/tmp/hald-local/dbus-4CYGzXdWrw
unix  3      [ ]         STREAM     CONNECTED     9586     
unix  3      [ ]         STREAM     CONNECTED     9577     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9576     
unix  4      [ ]         STREAM     CONNECTED     9699     /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9541     
unix  3      [ ]         STREAM     CONNECTED     9518     /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     9517     
unix  3      [ ]         STREAM     CONNECTED     9447     @/tmp/hald-local/dbus-4CYGzXdWrw
unix  3      [ ]         STREAM     CONNECTED     9439     
unix  3      [ ]         STREAM     CONNECTED     9411     /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     9410     
unix  3      [ ]         STREAM     CONNECTED     9414     @/tmp/hald-local/dbus-4CYGzXdWrw
unix  3      [ ]         STREAM     CONNECTED     9405     
unix  3      [ ]         STREAM     CONNECTED     8407     @/tmp/hald-runner/dbus-0p18I47nbx
unix  3      [ ]         STREAM     CONNECTED     8406     
unix  3      [ ]         STREAM     CONNECTED     8388     
unix  3      [ ]         STREAM     CONNECTED     8387     
unix  2      [ ]         DGRAM                    8321     
unix  2      [ ]         STREAM     CONNECTED     8268     /var/run/acpid.socket

```
 
```

lsmod
Module                             Size  Used by
ipv6                            272288  10 
cpufreq_userspace                 5408  0 
cpufreq_stats                     7744  0 
freq_table                        6048  1 cpufreq_stats
cpufreq_powersave                 2944  0 
cpufreq_ondemand                  8876  0 
cpufreq_conservative              8712  0 
video                            17540  0 
tc1100_wmi                        8324  0 
sbs                              16804  0 
sony_acpi                         6412  0 
pcc_acpi                         14080  0 
i2c_ec                            6272  1 sbs
hotkey                           11556  0 
dev_acpi                         12292  0 
button                            7952  0 
battery                          11652  0 
container                         5632  0 
ac                                6788  0 
asus_acpi                        17688  0 
lp                               12964  0 
tsdev                             9152  0 
parport_pc                       37796  1 
parport                          39496  2 lp,parport_pc
serio_raw                         8452  0 
evdev                            11392  1 
ns558                             6016  0 
gameport                         17160  2 ns558
floppy                           63044  0 
psmouse                          41352  0 
pcspkr                            4352  0 
sis5595                          16648  0 
i2c_isa                           6144  1 sis5595
i2c_sis5595                       8580  0 
i2c_sis630                        8844  0 
8139cp                           24832  0 
i2c_core                         23424  5 i2c_ec,sis5595,i2c_isa,i2c_sis5595,i2c_sis630
8139too                          29056  0 
mii                               6912  2 8139cp,8139too
shpchp                           42144  0 
sis_agp                           9860  0 
agpgart                          34888  1 sis_agp
pci_hotplug                      32828  1 shpchp
ext3                            142728  1 
jbd                              62228  1 ext3
ide_generic                       2432  0 
ohci_hcd                         22532  0 
usbcore                         134912  2 ohci_hcd
ide_disk                         18560  3 
ide_cd                           33696  0 
cdrom                            38944  1 ide_cd
sis5513                          15368  1 
generic                           5764  0 
thermal                          15624  0 
processor                        31560  1 thermal
fan                               6020  0 
fbcon                            41504  0 
tileblit                          3840  1 fbcon
font                              9344  1 fbcon
bitblit                           7168  1 fbcon
softcursor                        3328  1 bitblit
vesafb                            9244  0 
capability                        5896  0 
commoncap                         8704  1 capability

```
 
```

auto eth0
iface eth0 inet static
 
address 10.0.0.2
 
netmask 255.255.255.0
 
network 10.0.0.0
 
broadcast 10.0.0.255
 
gateway 10.0.0.1
 
dns-nameservers 200.43.2.6

```
 
```

dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000007ff0000 (usable)
[17179569.184000]  BIOS-e820: 0000000007ff0000 - 0000000007ff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000007ff8000 - 0000000008000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000ffef0000 - 00000000fff00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 127MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 32752
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 28656 pages, LIFO batch:7
[17179569.184000] DMI 2.0 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fb230
[17179569.184000] ACPI: RSDT (v001 AMIINT          0x00000000 MSFT 0x00000097) @ 0x07ff0000
[17179569.184000] ACPI: FADT (v001 AMIINT          0x00000000 MSFT 0x00000097) @ 0x07ff0030
[17179569.184000] ACPI: DSDT (v001    SiS          0x00001000 MSFT 0x0100000a) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x408
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 08000000:f7ef0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hdd2 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01109000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 512 (order: 9, 2048 bytes)
[17179569.184000] Detected 334.135 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.048000] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179570.052000] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
[17179570.080000] Memory: 120252k/131008k available (1910k kernel code, 10224k reserved, 1070k data, 308k init, 0k highmem)
[17179570.080000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.160000] Calibrating delay using timer specific routine.. 669.14 BogoMIPS (lpj=1338292)
[17179570.160000] Security Framework v1.0.0 initialized
[17179570.160000] SELinux:  Disabled at boot.
[17179570.160000] Mount-cache hash table entries: 512
[17179570.160000] CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179570.160000] CPU: After vendor identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179570.160000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179570.160000] CPU: L2 cache: 128K
[17179570.160000] CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[17179570.160000] Checking 'hlt' instruction... OK.
[17179570.176000] SMP alternatives: switching to UP code
[17179570.176000] Freeing SMP alternatives: 16k freed
[17179570.176000] checking if image is initramfs... it is
[17179573.104000] Freeing initrd memory: 5318k freed
[17179573.104000] ACPI: Core revision 20060707
[17179573.108000] ACPI: Looking for DSDT ... not found!
[17179573.112000] ACPI: setting ELCR to 0800 (from 0600)
[17179573.112000] CPU0: Intel Celeron (Mendocino) stepping 00
[17179573.112000] SMP motherboard not detected.
[17179573.112000] Local APIC not detected. Using dummy APIC emulation.
[17179573.116000] Brought up 1 CPUs
[17179573.116000] migration_cost=0
[17179573.116000] NET: Registered protocol family 16
[17179573.116000] EISA bus registered
[17179573.116000] ACPI: bus type pci registered
[17179573.120000] PCI: PCI BIOS revision 2.10 entry at 0xfdb81, last bus=1
[17179573.120000] PCI: Using configuration type 1
[17179573.120000] Setting up standard PCI resources
[17179573.136000] ACPI: Interpreter enabled
[17179573.136000] ACPI: Using PIC for interrupt routing
[17179573.140000] ACPI: PCI Root Bridge [NRTH] (0000:00)
[17179573.140000] PCI: Probing PCI hardware (bus 00)
[17179573.140000] ACPI: Assume root bridge [\_SB_.NRTH] bus is 0
[17179573.152000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:00.1
[17179573.152000] Boot video device is 0000:01:00.0
[17179573.152000] ACPI: PCI Interrupt Routing Table [\_SB_.NRTH._PRT]
[17179573.180000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15), disabled.
[17179573.180000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.184000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.184000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179573.184000] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[17179573.184000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.184000] pnp: PnP ACPI init
[17179573.212000] pnp: PnP ACPI: found 13 devices
[17179573.212000] PnPBIOS: Disabled by ACPI PNP
[17179573.212000] PCI: Using ACPI for IRQ routing
[17179573.212000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.220000] pnp: 00:01: ioport range 0x400-0x40f could not be reserved
[17179573.220000] pnp: 00:01: ioport range 0x410-0x43f could not be reserved
[17179573.220000] PCI: Bridge: 0000:00:02.0
[17179573.220000]   IO window: c000-cfff
[17179573.220000]   MEM window: dfe00000-dfefffff
[17179573.220000]   PREFETCH window: dec00000-dfcfffff
[17179573.220000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179573.224000] NET: Registered protocol family 2
[17179573.260000] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
[17179573.260000] TCP established hash table entries: 4096 (order: 3, 32768 bytes)
[17179573.260000] TCP bind hash table entries: 2048 (order: 2, 16384 bytes)
[17179573.260000] TCP: Hash tables configured (established 4096 bind 2048)
[17179573.260000] TCP reno registered
[17179573.264000] audit: initializing netlink socket (disabled)
[17179573.264000] audit(1165233161.264:1): initialized
[17179573.268000] VFS: Disk quotas dquot_6.5.1
[17179573.268000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.268000] Initializing Cryptographic API
[17179573.268000] io scheduler noop registered
[17179573.268000] io scheduler anticipatory registered
[17179573.268000] io scheduler deadline registered
[17179573.268000] io scheduler cfq registered (default)
[17179573.268000] isapnp: Scanning for PnP cards...
[17179573.368000] pnp: CMI8330 quirk - fixing interrupts and dma
[17179573.368000] isapnp: Card 'CMI8330/C3D Audio Adapter'
[17179573.368000] isapnp: 1 Plug & Play card detected total
[17179573.648000] Real Time Clock Driver v1.12ac
[17179573.648000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179573.648000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.652000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.660000] pnp: Device 00:0b activated.
[17179573.660000] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.664000] mice: PS/2 mouse device common for all mice
[17179573.668000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.668000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.668000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.672000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179573.672000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.672000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.676000] EISA: Probing bus 0 at eisa.0
[17179573.676000] EISA: Detected 0 cards.
[17179573.676000] TCP bic registered
[17179573.676000] NET: Registered protocol family 1
[17179573.676000] NET: Registered protocol family 8
[17179573.676000] NET: Registered protocol family 20
[17179573.676000] Using IPI No-Shortcut mode
[17179573.676000] ACPI: (supports S0 S1 S5)
[17179573.680000] Freeing unused kernel memory: 308k freed
[17179573.744000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.312000] Capability LSM initialized
[17179575.604000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179578.936000] SIS5513: IDE controller at PCI slot 0000:00:00.1
[17179578.936000] ACPI: Unable to derive IRQ for device 0000:00:00.1
[17179578.936000] ACPI: PCI Interrupt 0000:00:00.1[A]: no GSI
[17179578.936000] SIS5513: chipset revision 208
[17179578.936000] SIS5513: not 100% native mode: will probe irqs later
[17179578.936000] SIS5513: SiS5600 ATA 33 controller
[17179578.936000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:pio, hdb:pio
[17179578.936000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:pio
[17179578.936000] Probing IDE interface ide0...
[17179579.672000] hda: SAMSUNG CD-R/RW SW-248F, ATAPI CD/DVD-ROM drive
[17179580.008000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179580.008000] Probing IDE interface ide1...
[17179580.296000] hdc: Maxtor 90648D3, ATA DISK drive
[17179580.576000] hdd: ST310212A, ATA DISK drive
[17179580.632000] ide1 at 0x170-0x177,0x376 on irq 15
[17179580.756000] hda: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179580.756000] Uniform CD-ROM driver Revision: 3.20
[17179580.796000] hdc: max request size: 128KiB
[17179580.796000] hdc: 12656448 sectors (6480 MB) w/256KiB Cache, CHS=12556/16/63, UDMA(33)
[17179580.796000] hdc: cache flushes not supported
[17179580.796000]  hdc: hdc1
[17179580.812000] hdd: max request size: 128KiB
[17179580.812000] hdd: 20005650 sectors (10242 MB) w/512KiB Cache, CHS=19846/16/63, UDMA(33)
[17179580.812000] hdd: cache flushes not supported
[17179580.812000]  hdd: hdd1 hdd2 hdd3 < hdd5 >
[17179582.392000] usbcore: registered new driver usbfs
[17179582.396000] usbcore: registered new driver hub
[17179582.412000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179582.416000] ACPI: PCI Interrupt Link [LNKU] enabled at IRQ 10
[17179582.416000] PCI: setting IRQ 10 as level-triggered
[17179582.416000] ACPI: PCI Interrupt 0000:00:01.2[A] -> Link [LNKU] -> GSI 10 (level, low) -> IRQ 10
[17179582.416000] ohci_hcd 0000:00:01.2: OHCI Host Controller
[17179582.416000] ohci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[17179582.500000] ohci_hcd 0000:00:01.2: irq 10, io mem 0xe7fff000
[17179582.556000] usb usb1: configuration #1 chosen from 1 choice
[17179582.560000] hub 1-0:1.0: USB hub found
[17179582.560000] hub 1-0:1.0: 2 ports detected
[17179583.348000] Attempting manual resume
[17179583.484000] kjournald starting.  Commit interval 5 seconds
[17179583.484000] EXT3-fs: mounted filesystem with ordered data mode.
[17179605.096000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179605.164000] Linux agpgart interface v0.101 (c) Dave Jones
[17179605.188000] agpgart: Unsupported SiS chipset (device id: 5600)
[17179605.220000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179605.896000] 8139too Fast Ethernet driver 0.9.27
[17179605.896000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179605.896000] PCI: setting IRQ 11 as level-triggered
[17179605.896000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179605.896000] eth0: RealTek RTL8139 at 0xc885ef00, 00:08:54:23:2a:22, IRQ 11
[17179605.896000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179606.272000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179606.348000] sis630_smbus 0000:00:01.0: SIS630 comp. bus not detected, module not inserted.
[17179607.908000] input: PC Speaker as /class/input/input1
[17179610.344000] Floppy drive(s): fd0 is 1.44M
[17179610.372000] pnp: Device 01:01.02 activated.
[17179610.392000] gameport: NS558 PnP Gameport is pnp01:01.02/gameport0, io 0x200, speed 497kHz
[17179610.412000] FDC 0 is a post-1991 82077
[17179610.916000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[17179611.048000] parport: PnPBIOS parport detected.
[17179611.048000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179611.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17179611.840000] ts: Compaq touchscreen protocol output
[17179614.772000] lp0: using parport0 (interrupt-driven).
[17179614.984000] Adding 192740k swap on /dev/disk/by-uuid/2db8ee69-58f0-48d6-9fcd-c55994acd7c7.  Priority:-1 extents:1 across:192740k
[17179615.180000] EXT3 FS on hdd2, internal journal
[17179621.492000] ACPI: Power Button (FF) [PWRF]
[17179622.116000] ibm_acpi: ec object not found
[17179622.248000] pcc_acpi: loading...
[17179623.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17179626.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17179626.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17179626.436000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[17179626.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17179626.436000] eth0:  Tx descriptor 2 is 0008a03c.
[17179626.436000] eth0:  Tx descriptor 3 is 0008a03c.
[17179626.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17179634.804000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179634.804000] apm: overridden by ACPI.
[17179638.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17179641.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17179641.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17179641.436000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[17179641.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17179641.436000] eth0:  Tx descriptor 2 is 0008a03c.
[17179641.436000] eth0:  Tx descriptor 3 is 0008a03c.
[17179641.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17179647.196000] NET: Registered protocol family 10
[17179647.196000] lo: Disabled Privacy Extensions
[17179647.200000] IPv6 over IPv4 tunneling driver
[17179653.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17179656.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17179656.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17179656.436000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[17179656.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17179656.436000] eth0:  Tx descriptor 2 is 0008a03c.
[17179656.436000] eth0:  Tx descriptor 3 is 0008a03c.
[17179656.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17179657.548000] eth0: no IPv6 routers present
[17179668.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17179671.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17179671.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17179671.436000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[17179671.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17179671.436000] eth0:  Tx descriptor 2 is 0008a03c.
[17179671.436000] eth0:  Tx descriptor 3 is 0008a03c.
[17179671.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17179683.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17179686.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17179686.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17179686.436000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[17179686.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17179686.436000] eth0:  Tx descriptor 2 is 0008a05a.
[17179686.436000] eth0:  Tx descriptor 3 is 0008a04e.
[17179686.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17179698.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17179701.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17179701.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17179701.436000] eth0:  Tx descriptor 0 is 0008a046. (queue head)
[17179701.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17179701.436000] eth0:  Tx descriptor 2 is 0008a046.
[17179701.436000] eth0:  Tx descriptor 3 is 0008a03c.
[17179701.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17179713.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17179716.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17179716.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17179716.436000] eth0:  Tx descriptor 0 is 0008a05a. (queue head)
[17179716.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17179716.436000] eth0:  Tx descriptor 2 is 0008a046.
[17179716.436000] eth0:  Tx descriptor 3 is 0008a03c.
[17179716.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17179728.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17179731.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17179731.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17179731.436000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[17179731.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17179731.436000] eth0:  Tx descriptor 2 is 0008a03c.
[17179731.436000] eth0:  Tx descriptor 3 is 0008a03c.
[17179731.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17179743.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17179746.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17179746.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17179746.436000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[17179746.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17179746.436000] eth0:  Tx descriptor 2 is 0008a03c.
[17179746.436000] eth0:  Tx descriptor 3 is 0008a03c.
[17179746.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17179758.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17179761.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17179761.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17179761.436000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[17179761.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17179761.436000] eth0:  Tx descriptor 2 is 0008a03c.
[17179761.436000] eth0:  Tx descriptor 3 is 0008a03c.
[17179761.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17179773.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17179776.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17179776.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17179776.436000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[17179776.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17179776.436000] eth0:  Tx descriptor 2 is 0008a03c.
[17179776.436000] eth0:  Tx descriptor 3 is 0008a03c.
[17179776.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17179788.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17179791.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17179791.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17179791.436000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[17179791.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17179791.436000] eth0:  Tx descriptor 2 is 0008a03c.
[17179791.436000] eth0:  Tx descriptor 3 is 0008a03c.
[17179791.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17179803.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17179806.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17179806.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17179806.436000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[17179806.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17179806.436000] eth0:  Tx descriptor 2 is 0008a03c.
[17179806.436000] eth0:  Tx descriptor 3 is 0008a03c.
[17179806.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17179818.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17179821.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17179821.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17179821.436000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[17179821.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17179821.436000] eth0:  Tx descriptor 2 is 0008a03c.
[17179821.436000] eth0:  Tx descriptor 3 is 0008a03c.
[17179821.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17179833.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17179836.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17179836.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17179836.436000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[17179836.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17179836.436000] eth0:  Tx descriptor 2 is 0008a03c.
[17179836.436000] eth0:  Tx descriptor 3 is 0008a03c.
[17179836.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17179848.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17179851.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17179851.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17179851.436000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[17179851.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17179851.436000] eth0:  Tx descriptor 2 is 0008a03c.
[17179851.436000] eth0:  Tx descriptor 3 is 0008a03c.
[17179851.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17179863.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17179866.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17179866.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17179866.436000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[17179866.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17179866.436000] eth0:  Tx descriptor 2 is 0008a03c.
[17179866.436000] eth0:  Tx descriptor 3 is 0008a03c.
[17179866.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17179878.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17179881.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17179881.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17179881.436000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[17179881.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17179881.436000] eth0:  Tx descriptor 2 is 0008a03c.
[17179881.436000] eth0:  Tx descriptor 3 is 0008a03c.
[17179881.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17179893.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17179896.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17179896.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17179896.436000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[17179896.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17179896.436000] eth0:  Tx descriptor 2 is 0008a03c.
[17179896.436000] eth0:  Tx descriptor 3 is 0008a03c.
[17179896.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17179956.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17179959.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17179959.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17179959.436000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[17179959.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17179959.436000] eth0:  Tx descriptor 2 is 0008a03c.
[17179959.436000] eth0:  Tx descriptor 3 is 0008a03c.
[17179959.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17179971.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17179974.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17179974.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17179974.436000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[17179974.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17179974.436000] eth0:  Tx descriptor 2 is 0008a03c.
[17179974.436000] eth0:  Tx descriptor 3 is 0008a03c.
[17179974.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17180820.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17180823.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17180823.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17180823.436000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[17180823.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17180823.436000] eth0:  Tx descriptor 2 is 0008a03c.
[17180823.436000] eth0:  Tx descriptor 3 is 0008a03c.
[17180823.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17180835.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17180838.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17180838.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17180838.436000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[17180838.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17180838.436000] eth0:  Tx descriptor 2 is 0008a03c.
[17180838.436000] eth0:  Tx descriptor 3 is 0008a03c.
[17180838.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[17180850.436000] NETDEV WATCHDOG: eth0: transmit timed out
[17180853.436000] eth0: Transmit timeout, status 0c 0005 c07f media 00.
[17180853.436000] eth0: Tx queue start entry 4  dirty entry 0.
[17180853.436000] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[17180853.436000] eth0:  Tx descriptor 1 is 0008a03c.
[17180853.436000] eth0:  Tx descriptor 2 is 0008a03c.
[17180853.436000] eth0:  Tx descriptor 3 is 0008a03c.
[17180853.436000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000

```

---

### Post by ingo on 2006-12-06
I'm afraid I haven't got much experience when it comes to static IPs, but can you post your /etc/network/interfaces?

---

### Post by lloyd_b on 2006-12-06
I'd be willing to bet that the problem is with the Realtek card/driver.  Search the forums for "Realtek" and you'll find several dozen threads on the subject.

Unfortunately, there doesn't seem to be any single fix for this - many people have resolved the issue, but each one is using a different fix.

Everything else in your configuration looks fine.

Lloyd B.

---

### Post by RFMaster on 2006-12-06
Thank you sooo so very much I'll try to find a fix in the realtek threads.
I apreciate your help.

---


---
title: "Ubuntu 18.04 asymmetrical wired network connection speeds?"
date: 2018-12-24
forum: Networking &amp; Wireless
---

### Post by todd-4 on 2018-12-24
So... I'm relatively new to this, just did a new install of Ubuntu 18.04 on an older laptop (dual boot with Win10) and am having a somewhat weird issue with file transfer speeds, not sure where to go to troubleshoot.

The machine is an older Lenovo (3000 V200 laptop) that has been running various Windows since it was born, currently on Win10 and working fine, just veeerrrryyyy slow with Win...  I loaded Ubuntu on it in hopes of having a snappier option to use for various low-impact tasks (like web browsing, downloading, file transfers...)

The machine is part of a local network that includes various other devices, including two Raspberry Pi media centers (one for video running Openelec/Kodi, one for audio running Raspbian/Clementine) and a home office desktop that is on Windows 10.  All devices are wired connections, all appear to be working fine themselves.  I can transfer files at "normal" speeds between the various RPI and desktop devices with no problems.

When the Lenovo is booted to Windows, it also has no problem with this - transfer speeds usually in the 10MB/S range.  

HOWEVER, when the Lenovo is booted into Ubuntu, the same machine, with no changes in connectivity, will only transfer FROM itself TO other devices with a max transfer speed of about 400Kb/S.   Often substantially slower.

Strangely enough, if I initiate a transfer TO the laptop from any of the other devices on the network (doing this using the laptop's file manager), the transfer speed approaches the same 10MB/S I get when the machine is doing the same transfer inside Windows.

To summarize - transfers from laptop to network devices, slow.  Transfers from network devices to laptop, fast.  Boot same machine into Windows with no changes otherwise, both directions fast...

I'm far from a Linux expert, but here are some configuration details below.  

What should I look for in this to figure this out?   It's not the world's largest problem, but the general purpose of this machine is to download large files and transfer them out to the network so it's annoying to have that take 10-20 times the time it should...

___________________________________________________________________

ifconfig -a

enp5s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.103  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::21f:16ff:fe01:1913  prefixlen 64  scopeid 0x20<link>
        ether 00:1f:16:01:19:13  txqueuelen 1000  (Ethernet)
        RX packets 8352  bytes 1512770 (1.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 10918  bytes 12986653 (12.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 17  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 665  bytes 51706 (51.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 665  bytes 51706 (51.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

tun0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1500
        inet 10.192.0.10  netmask 255.255.255.255  destination 10.192.0.9
        inet6 fe80::e421:c7d9:9bc1:35e3  prefixlen 64  scopeid 0x20<link>
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 100  (UNSPEC)
        RX packets 698  bytes 520932 (520.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 975  bytes 102546 (102.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp6s0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether 00:1f:3c:6c:a2:22  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

________________________________________________________

arp -a

? (192.168.1.100) at 00:24:1d:d0:6e:49 [ether] on enp5s0
_gateway (192.168.1.1) at 10:0d:7f:7d:ad:6b [ether] on enp5s0
? (192.168.1.110) at ac:18:26:56:ea:06 [ether] on enp5s0

________________________________________________________

lsdev

Device            DMA   IRQ  I/O Ports
------------------------------------------------
0000:00:02.0                   0000-0000
0000:00:1a.0                   0000-0000
0000:00:1a.1                   0000-0000
0000:00:1d.0                   0000-0000
0000:00:1d.1                   0000-0000
0000:00:1d.2                   0000-0000
0000:00:1f.0                   0000-0000   0000-0000
0000:00:1f.1                   0000-0000   0000-0000   0000-0000   0000-0000   0000-0000
0000:00:1f.2                   0000-0000   0000-0000   0000-0000   0000-0000   0000-0000
0000:00:1f.3                   0000-0000
ACPI                               0000-0000       0000-0000       0000-0000       0000-0000       0000-0000
acpi                      9 
ahci                             0000-0000     0000-0000     0000-0000     0000-0000     0000-0000
ahci[0000:00:1f.2]         24 
ata_piix              14 15      0000-0000     0000-0000     0000-0000     0000-0000     0000-0000
cascade             4       
dma                            0000-0000
dma1                           0000-0000
dma2                           0000-0000
EC                               0000-0000     0000-0000
enp5s0                   27 
fpu                            0000-0000
i801_smbus               19      0000-0000
i8042                  1 12 
i915                     16 
iTCO_wdt.0.auto                    0000-0000       0000-0000
iwl3945                  25 
keyboard                       0000-0000   0000-0000
PCI                          0000-0000 0000-0000 0000-0000   0000-0000   0000-0000   0000-0000
pic1                           0000-0000
pic2                           0000-0000
pnp                            0000-0000     0000-0000     0000-0000   0000-0000
PNP0C04:00                       0000-0000
PNP0C09:00                     0000-0000   0000-0000
r852                     18 
rtc0                      8    0000-0000
snd_hda_intel:card0         26 
timer                     0 
timer0                         0000-0000
timer1                         0000-0000
uhci_hcd                         0000-0000     0000-0000     0000-0000     0000-0000     0000-0000
uhci_hcd:usb4            21 
uhci_hcd:usb5            23 
vesafb                         0000-0000

--------------------------------------------------------------------------------------

lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Broadcom Limited NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
0a:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0a:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0a:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by mitesh.agrwl on 2018-12-24
From the given data it looks like networking part is not issue! Please post the output from ```
sudo lshw -class network
route -n
```
and mention the program/protocol used for file transfer between devices, i.e. is there a NFS, Samba, ftp or something else.

---

### Post by todd-4 on 2018-12-24
Thanks.  Output from both below.  

I don't know how I would tell what protocol is being used.  All tests are being made using the file manager that comes with Ubuntu 18.04, stock install, nothing changed.  In one test I attempt to transfer from the Ubuntu machine to a Windows network share (on my home office desktop), in the other test I attempt to tranfer to a share managed on my Raspberry Pi OpenElec video server.  I don't know if they're both the same protocol (smb, maybe?) or different because the target in one case is a Windows machine and the other a Linux box...?

lshw

  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: enp5s0
       version: 02
       serial: 00:1f:16:01:19:13
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=sb v3.04 ip=192.168.1.103 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:27 memory:f4200000-f420ffff
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlp6s0
       version: 02
       serial: 00:1f:3c:6c:a2:22
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=4.15.0-42-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:25 memory:f4300000-f4300fff

       
route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp5s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp5s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp5s0

---

### Post by todd-4 on 2018-12-29
Any ideas, anyone?

---


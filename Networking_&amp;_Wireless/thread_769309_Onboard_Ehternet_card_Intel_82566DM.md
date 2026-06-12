---
title: "Onboard Ehternet card Intel 82566DM"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by sijanac on 2008-04-26
Hi,
I have Asus P5E-VM DO motherboard with integrated lan controller : Intel 82566DM PCIe Gigabit LAN Controller that doesn't work.

I have installed Debian 4 version, and although this is Ubuntu forum I hope that you will help me because I think that this has same problem also on Ubuntu distribution, because I noticed few posts with same nic here, and you finally solved problem for them.

I used same notes but I have stuck with following situation. 

After downloading latest driver from Intel site, compiled it and install it I have still this:

```
Mrcina:/home/matija# lshw -C network
  *-network UNCLAIMED
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@00:19.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:fe940000-fe95ffff iomemory:fe979000-fe979fff ioport:bc00-bc1f irq:3
  *-network
       description: Ethernet interface
       product: RTL-8029(AS)
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 00
       serial: 00:c0:df:ef:06:7e
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 ip=192.168.1.15 latency=0 multicast=yes
       resources: ioport:ec00-ec1f irq:201
  *-network DISABLED
       description: IEEE1394 interface
       physical id: 1
       logical name: eth0
       serial: 00:1e:8c:00:00:19
       capabilities: ieee1394 physical
       configuration: broadcast=yes driver=eth1394 ip=192.168.1.14 multicast=yesMrcina:/home/matija#

```

```

Mrcina:/home/matija# lsmod
Module                  Size  Used by
e1000                 165184  0
sg                     40744  0
ppdev                  14088  0
lp                     17736  0
button                 12192  0
ac                     10376  0
battery                15496  0
dm_snapshot            20664  0
dm_mirror              25216  0
dm_mod                 62800  2 dm_snapshot,dm_mirror
sbp2                   28680  0
loop                   20112  0
parport_pc             41640  1
parport                44684  3 ppdev,lp,parport_pc
floppy                 67112  0
i2c_i801               13076  0
i2c_core               27776  1 i2c_i801
serio_raw              12036  0
eth1394                24840  0
tsdev                  13056  0
psmouse                44432  0
pcspkr                  7808  0
evdev                  15360  1
ext3                  138512  1
jbd                    65392  1 ext3
mbcache                14216  1 ext3
sd_mod                 25856  0
ide_cd                 45088  0
cdrom                  40488  1 ide_cd
ide_disk               20608  3
ata_piix               20360  0
libata                106784  1 ata_piix
scsi_mod              153008  4 sg,sbp2,sd_mod,libata
usbhid                 45088  0
ohci1394               38216  0
ieee1394              361976  3 sbp2,eth1394,ohci1394
ne2k_pci               16736  0
8390                   14848  1 ne2k_pci
jmicron                 9344  0 [permanent]
ehci_hcd               36104  0
generic                10500  0 [permanent]
ide_core              147584  4 ide_cd,ide_disk,jmicron,generic
uhci_hcd               28696  0
thermal                20240  0
processor              38248  1 thermal
fan                     9864  0
Mrcina:/home/matija#

```

```

Mrcina:/home/matija# lspci
00:00.0 Host bridge: Intel Corporation Unknown device 29b0 (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Unknown device 29b2 (rev 02)
00:03.0 Communication controller: Intel Corporation Unknown device 29b4 (rev 02)00:03.2 IDE interface: Intel Corporation Unknown device 29b6 (rev 02)
00:03.3 Serial controller: Intel Corporation Unknown device 29b7 (rev 02)
00:19.0 Ethernet controller: Intel Corporation Unknown device 10bd (rev 02)
00:1a.0 USB Controller: Intel Corporation Unknown device 2937 (rev 02)
00:1a.1 USB Controller: Intel Corporation Unknown device 2938 (rev 02)
00:1a.2 USB Controller: Intel Corporation Unknown device 2939 (rev 02)
00:1a.7 USB Controller: Intel Corporation Unknown device 293c (rev 02)
00:1b.0 Audio device: Intel Corporation Unknown device 293e (rev 02)
00:1c.0 PCI bridge: Intel Corporation Unknown device 2940 (rev 02)
00:1c.4 PCI bridge: Intel Corporation Unknown device 2948 (rev 02)
00:1d.0 USB Controller: Intel Corporation Unknown device 2934 (rev 02)
00:1d.1 USB Controller: Intel Corporation Unknown device 2935 (rev 02)
00:1d.2 USB Controller: Intel Corporation Unknown device 2936 (rev 02)
00:1d.7 USB Controller: Intel Corporation Unknown device 293a (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation Unknown device 2914 (rev 02)
00:1f.2 IDE interface: Intel Corporation Unknown device 2920 (rev 02)
00:1f.3 SMBus: Intel Corporation Unknown device 2930 (rev 02)
00:1f.5 IDE interface: Intel Corporation Unknown device 2926 (rev 02)
00:1f.6 Signal processing controller: Intel Corporation Unknown device 2932 (rev 02)
01:00.0 IDE interface: JMicron Technologies, Inc. Unknown device 2368
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
03:02.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
Mrcina:/home/matija#

```

How to make my onboard ehternet card claimed ?!

Thnx and sorry for my english.

---

### Post by sijanac on 2008-04-26
I solved my problem.

After making this post, now as I have forum account I did search on verb 82566 on this forum and noticed that there were a lot of people that solved same problem but with different driver version. 

I downloaded driver version e1000-8.0.1 and it doesn't work for my card, but (after reading various post) I compiled driver version e1000-7.6.5 and it worked perfectly. 

Now I am using this onboard ethernet card and writing this post.

Thnx.

---


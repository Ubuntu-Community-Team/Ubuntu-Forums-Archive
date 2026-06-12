---
title: "No connexion ethernet : Marvell yukon 88E8056 PCI-E Gigabit"
date: 2013-11-22
forum: Networking &amp; Wireless
---

### Post by telendri on 2013-11-22
Hello,

I have read various posts on this subject, unfortunately none of them will not work for me.

My ethernet connection is running in win7. I have a D-link adsl router.

I slowly began to lose hope, given the number of days to try to find a solution.

Also my wifi works randomly, so difficult to make updates.

I post the results of various different commands:

```

lshw -c network
*-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:1e:8c:70:cd:06
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:fe9fc000-fe9fffff ioport:d800(size=256) memory:fe9c0000-fe9dffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:15:af:52:11:30
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.11.0-12-generic firmware=N/A ip=192.168.1.6 link=yes multicast=yes wireless=IEEE 802.11bg

```

```

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1e:8c:70:cd:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7443 (7.4 KB)  TX bytes:7443 (7.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:52:11:30  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe52:1130/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:249 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35446 (35.4 KB)  TX bytes:31257 (31.2 KB)


```

J'ai essayé d'installer un driver sur le site de Marvell sans succès.
J'ai décompressé l'archive, exécuter la commande :

I try to install the driver from Marvell website without success.

I have executed the following commands:

```

./install.sh

1) installation
3)remove driver


Ensuite j'ai le message suivant:
Compile the kernel (error)                                           [ failed ]

 
```

Thanks in advance for your help.

---

### Post by sanderj on 2013-11-23
Advice:

- tell the Ubuntu version you're using
- tell what you have already read and tried, to avoid that you are given advice you've already tried out
- disconnect the ethernet cable, re-connect it, type 'dmesg' and post the page of output here

---

### Post by telendri on 2013-11-24
Hi Sanderj,

The Ubuntu version is 13.10 64-bit

I have read posts telling that the problem came from the driver sky2 and there was a procedure indicating how to install the new driver sky98lin. But as I said I had an issue with the installation of the driver (compile the kernel (error))

dmesg output after disconnecting the ethernet cable, reconnecting it.

```

[    0.607336] AppArmor: AppArmor sha1 policy hashing enabled
[    0.607695]   Magic number: 5:458:490
[    0.607803] rtc_cmos 00:02: setting system clock to 2013-11-24 16:27:07 UTC (1385310427)
[    0.608381] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.608383] EDD information not available.
[    0.898623] ata3: SATA link down (SStatus 0 SControl 300)
[    0.900025] usb 1-3: new high-speed USB device number 2 using ehci-pci
[    1.038415] usb 1-3: New USB device found, idVendor=0bda, idProduct=8187
[    1.038420] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.038423] usb 1-3: Product: RTL8187_Wireless
[    1.038426] usb 1-3: Manufacturer: Manufacturer_Realtek_RTL8187_
[    1.038430] usb 1-3: SerialNumber: 0015AF521130
[    1.040070] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.048159] ata4.00: ATAPI: PIONEER DVD-RW  DVR-212, 1.21, max UDMA/66
[    1.064143] ata4.00: configured for UDMA/66
[    1.222628] ata1.00: SATA link down (SStatus 0 SControl 300)
[    1.222640] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.364115] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.364129] ata2.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.396231] ata2.00: ATA-9: Samsung SSD 840 PRO Series, DXM05B0Q, max UDMA/133
[    1.396235] ata2.00: 250069680 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.396578] ata2.01: ATA-8: SAMSUNG HD501LJ, CR100-12, max UDMA7
[    1.396583] ata2.01: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.404424] ata2.00: configured for UDMA/133
[    1.412261] ata2.01: configured for UDMA/133
[    1.412395] scsi 1:0:0:0: Direct-Access     ATA      Samsung SSD 840  DXM0 PQ: 0 ANSI: 5
[    1.412569] sd 1:0:0:0: [sda] 250069680 512-byte logical blocks: (128 GB/119 GiB)
[    1.412585] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.412639] sd 1:0:0:0: [sda] Write Protect is off
[    1.412643] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.412665] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.412688] scsi 1:0:1:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[    1.412796] sd 1:0:1:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.412859] sd 1:0:1:0: [sdb] Write Protect is off
[    1.412860] sd 1:0:1:0: Attached scsi generic sg1 type 0
[    1.412865] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.412894] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.419255] scsi 3:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-212  1.21 PQ: 0 ANSI: 5
[    1.423064]  sdb: sdb1
[    1.423505]  sda: sda1 sda2 < sda5 >
[    1.423626] sd 1:0:1:0: [sdb] Attached SCSI disk
[    1.423868] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.425569] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.425573] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.425709] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.425794] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    1.427111] Freeing unused kernel memory: 1364K (ffffffff81d10000 - ffffffff81e65000)
[    1.427114] Write protecting the kernel read-only data: 12288k
[    1.430032] Freeing unused kernel memory: 1040K (ffff8800016fc000 - ffff880001800000)
[    1.432253] Freeing unused kernel memory: 836K (ffff880001b2f000 - ffff880001c00000)
[    1.445598] systemd-udevd[126]: starting version 204
[    1.460952] floppy: module verification failed: signature and/or required key missing - tainting kernel
[    1.461609] Floppy drive(s): fd0 is 1.44M
[    1.470506] ahci 0000:03:00.0: version 3.0
[    1.473115] sky2: driver version 1.30
[    1.473196] sky2 0000:02:00.0: Yukon-2 EC Ultra chip revision 3
[    1.473253] sky2 0000:02:00.0: irq 44 for MSI/MSI-X
[    1.473716] sky2 0000:02:00.0 eth0: addr 00:1e:8c:70:cd:06
[    1.479911] FDC 0 is a post-1991 82077
[    1.484056] firewire_ohci 0000:05:03.0: added OHCI v1.0 device as card 0, 8 IR + 8 IT contexts, quirks 0x80
[    1.484165] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.484170] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.484543] scsi4 : ahci
[    1.484660] scsi5 : ahci
[    1.484748] ata5: SATA max UDMA/133 abar m8192@0xfeafe000 port 0xfeafe100 irq 16
[    1.484752] ata6: SATA max UDMA/133 abar m8192@0xfeafe000 port 0xfeafe180 irq 16
[    1.484779] pata_jmicron 0000:03:00.1: enabling device (0000 -> 0001)
[    1.484856] pata_jmicron 0000:03:00.1: setting latency timer to 64
[    1.485238] scsi6 : pata_jmicron
[    1.485534] scsi7 : pata_jmicron
[    1.485725] ata7: PATA max UDMA/100 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 17
[    1.485728] ata8: PATA max UDMA/100 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 17
[    1.500028] tsc: Refined TSC clocksource calibration: 2405.454 MHz
[    1.694533] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.796029] usb 7-1: new full-speed USB device number 2 using uhci_hcd
[    1.804078] ata5: SATA link down (SStatus 0 SControl 300)
[    1.804113] ata6: SATA link down (SStatus 0 SControl 300)
[    1.990566] usb 7-1: New USB device found, idVendor=046d, idProduct=c52b
[    1.990570] usb 7-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.990573] usb 7-1: Product: USB Receiver
[    1.990575] usb 7-1: Manufacturer: Logitech
[    1.992084] firewire_core 0000:05:03.0: created device fw0: GUID 001e8c000019ab71, S400
[    2.236145] usb 7-2: new full-speed USB device number 3 using uhci_hcd
[    2.252719] Adding 4192252k swap on /dev/sda5.  Priority:-1 extents:1 across:4192252k SSFS
[    2.304402] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.332620] systemd-udevd[301]: starting version 204
[    2.361366] lp: driver loaded but no devices found
[    2.409783] [drm] Initialized drm 1.1.0 20060810
[    2.416777] wmi: Mapper loaded
[    2.430048] usb 7-2: New USB device found, idVendor=046d, idProduct=c24e
[    2.430053] usb 7-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.430055] usb 7-2: Product: G500s Laser Gaming Mouse
[    2.430058] usb 7-2: Manufacturer: Logitech
[    2.430060] usb 7-2: SerialNumber: 9F527EDB060008
[    2.436634] nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0x084200a2
[    2.436638] nouveau  [  DEVICE][0000:01:00.0] Chipset: G84 (NV84)
[    2.436640] nouveau  [  DEVICE][0000:01:00.0] Family : NV50
[    2.438720] nouveau  [   VBIOS][0000:01:00.0] checking PRAMIN for image...
[    2.469527] microcode: CPU0 sig=0x6fb, pf=0x10, revision=0xb6
[    2.475284] type=1400 audit(1385310429.363:2): apparmor="STATUS" operation="profile_load" parent=350 profile="unconfined" name="/sbin/dhclient" pid=355 comm="apparmor_parser"
[    2.475292] type=1400 audit(1385310429.363:3): apparmor="STATUS" operation="profile_load" parent=350 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=355 comm="apparmor_parser"
[    2.475297] type=1400 audit(1385310429.363:4): apparmor="STATUS" operation="profile_load" parent=350 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=355 comm="apparmor_parser"
[    2.475858] type=1400 audit(1385310429.363:5): apparmor="STATUS" operation="profile_replace" parent=350 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=355 comm="apparmor_parser"
[    2.475865] type=1400 audit(1385310429.363:6): apparmor="STATUS" operation="profile_replace" parent=350 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=355 comm="apparmor_parser"
[    2.476163] type=1400 audit(1385310429.367:7): apparmor="STATUS" operation="profile_replace" parent=350 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=355 comm="apparmor_parser"
[    2.482079] nouveau  [   VBIOS][0000:01:00.0] ... appears to be valid
[    2.482083] nouveau  [   VBIOS][0000:01:00.0] using image from PRAMIN
[    2.482190] nouveau  [   VBIOS][0000:01:00.0] BIT signature found
[    2.482193] nouveau  [   VBIOS][0000:01:00.0] version 60.84.41.00.00
[    2.500094] hidraw: raw HID events driver (C) Jiri Kosina
[    2.505694] nouveau  [     PFB][0000:01:00.0] RAM type: GDDR3
[    2.505699] nouveau  [     PFB][0000:01:00.0] RAM size: 256 MiB
[    2.505701] nouveau  [     PFB][0000:01:00.0]    ZCOMP: 1892 tags
[    2.509536] cfg80211: Calling CRDA to update world regulatory domain
[    2.509727] Switched to clocksource tsc
[    2.524778] usbcore: registered new interface driver usbhid
[    2.524782] usbhid: USB HID core driver
[    2.527398] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[    2.537397] nouveau  [  PTHERM][0000:01:00.0] FAN control: none / external
[    2.537408] nouveau  [  PTHERM][0000:01:00.0] fan management: disabled
[    2.537412] nouveau  [  PTHERM][0000:01:00.0] internal sensor: yes
[    2.537432] nouveau E[  PTHERM][0000:01:00.0] unhandled intr 0x000001e1
[    2.537686] [TTM] Zone  kernel: Available graphics memory: 2024014 kiB
[    2.537688] [TTM] Initializing pool allocator
[    2.537692] [TTM] Initializing DMA pool allocator
[    2.537702] nouveau  [     DRM] VRAM: 256 MiB
[    2.537704] nouveau  [     DRM] GART: 1048576 MiB
[    2.537708] nouveau  [     DRM] TMDS table version 2.0
[    2.537710] nouveau  [     DRM] DCB version 4.0
[    2.537712] nouveau  [     DRM] DCB outp 00: 02000300 00000028
[    2.537715] nouveau  [     DRM] DCB outp 01: 01000302 00000030
[    2.537717] nouveau  [     DRM] DCB outp 02: 04011310 00000028
[    2.537719] nouveau  [     DRM] DCB outp 03: 02011312 00000030
[    2.537721] nouveau  [     DRM] DCB outp 04: 010223f1 00c0c080
[    2.537723] nouveau  [     DRM] DCB conn 00: 1030
[    2.537725] nouveau  [     DRM] DCB conn 01: 2130
[    2.537727] nouveau  [     DRM] DCB conn 02: 0210
[    2.537729] nouveau  [     DRM] DCB conn 03: 0211
[    2.537731] nouveau  [     DRM] DCB conn 04: 0213
[    2.549091] nouveau W[     DRM] failed to create encoder 0/1/0: -19
[    2.549094] nouveau W[     DRM] TV-1 has no encoders, removing
[    2.549120] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.549121] [drm] No driver support for vblank timestamp query.
[    2.549249] nouveau  [     DRM] 1 available performance level(s)
[    2.549252] nouveau  [     DRM] 0: core 540MHz shader 1188MHz memory 700MHz fanspeed 100%
[    2.549255] nouveau  [     DRM] c: core 540MHz shader 1188MHz memory 702MHz voltage 1320mV
[    2.561351] nouveau  [     DRM] MM: using CRYPT for buffer copies
[    2.608795] nouveau  [     DRM] allocated 1920x1080 fb: 0x70000, bo ffff8801258cd000
[    2.608905] fbcon: nouveaufb (fb0) is primary device
[    2.688752] Console: switching to colour frame buffer device 240x67
[    2.690232] nouveau 0000:01:00.0: fb0: nouveaufb frame buffer device
[    2.690246] nouveau 0000:01:00.0: registered panic notifier
[    2.690252] [drm] Initialized nouveau 1.1.1 20120801 for 0000:01:00.0 on minor 0
[    2.710839] gpio_ich: GPIO from 195 to 255 on gpio_ich
[    2.716521] microcode: CPU1 sig=0x6fb, pf=0x10, revision=0xb6
[    2.720279] input: Logitech G500s Laser Gaming Mouse as /devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input2
[    2.721046] hid-generic 0003:046D:C24E.0004: input,hidraw0: USB HID v1.11 Mouse [Logitech G500s Laser Gaming Mouse] on usb-0000:00:1d.1-2/input0
[    2.722449] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-1/input2
[    2.726331] input: Logitech Unifying Device. Wireless PID:2010 as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.2/0003:046D:C52B.0003/input/input3
[    2.726430] logitech-djdevice 0003:046D:C52B.0006: input,hidraw2: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:2010] on usb-0000:00:1d.1-1:1
[    2.726715] input: Logitech G500s Laser Gaming Mouse as /devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/input/input4
[    2.727797] hid-generic 0003:046D:C24E.0005: input,hiddev0,hidraw3: USB HID v1.11 Keyboard [Logitech G500s Laser Gaming Mouse] on usb-0000:00:1d.1-2/input1
[    2.732308] microcode: CPU2 sig=0x6fb, pf=0x10, revision=0xb6
[    2.743189] microcode: CPU3 sig=0x6fb, pf=0x10, revision=0xb6
[    2.743768] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    2.748752] cfg80211: World regulatory domain updated:
[    2.748756] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    2.748758] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    2.748761] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    2.748763] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    2.748764] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    2.748766] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    2.753717] coretemp coretemp.0: Using relative temperature scale!
[    2.753733] coretemp coretemp.0: Using relative temperature scale!
[    2.753743] coretemp coretemp.0: Using relative temperature scale!
[    2.753752] coretemp coretemp.0: Using relative temperature scale!
[    2.765784] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    2.766010] ieee80211 phy0: hwaddr 00:15:af:52:11:30, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[    2.784051] rtl8187: Customer ID is 0x00
[    2.785659] rtl8187: wireless switch is on
[    2.785789] usbcore: registered new interface driver rtl8187
[    2.975063] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    3.171000] init: failsafe main process (606) killed by TERM signal
[    3.280691] Bluetooth: Core ver 2.16
[    3.280715] NET: Registered protocol family 31
[    3.280716] Bluetooth: HCI device and connection manager initialized
[    3.280727] Bluetooth: HCI socket layer initialized
[    3.280730] Bluetooth: L2CAP socket layer initialized
[    3.280735] Bluetooth: SCO socket layer initialized
[    3.284546] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.284549] Bluetooth: BNEP filters: protocol multicast
[    3.284556] Bluetooth: BNEP socket layer initialized
[    3.315504] Bluetooth: RFCOMM TTY layer initialized
[    3.315522] Bluetooth: RFCOMM socket layer initialized
[    3.315524] Bluetooth: RFCOMM ver 1.11
[    3.354911] ppdev: user-space parallel port driver
[    3.371383] init: avahi-cups-reload main process (740) terminated with status 1
[    3.392124] type=1400 audit(1385310430.281:8): apparmor="STATUS" operation="profile_load" parent=754 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=776 comm="apparmor_parser"
[    3.392134] type=1400 audit(1385310430.281:9): apparmor="STATUS" operation="profile_load" parent=754 profile="unconfined" name="/usr/sbin/cupsd" pid=776 comm="apparmor_parser"
[    3.392765] type=1400 audit(1385310430.281:10): apparmor="STATUS" operation="profile_replace" parent=754 profile="unconfined" name="/usr/sbin/cupsd" pid=776 comm="apparmor_parser"
[    5.512835] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.513316] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.520379] sky2 0000:02:00.0 eth0: enabling interface
[    5.520582] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.521409] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.221991] sky2 0000:02:00.0 eth0: speed/duplex mismatch
[    9.100627] wlan0: authenticate with 00:1c:f0:e3:13:82
[    9.309734] wlan0: send auth to 00:1c:f0:e3:13:82 (try 1/3)
[    9.311553] wlan0: authenticated
[    9.311683] rtl8187 1-3:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[    9.311688] rtl8187 1-3:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[    9.311691] rtl8187 1-3:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[    9.312201] wlan0: associate with 00:1c:f0:e3:13:82 (try 1/3)
[    9.316291] wlan0: RX AssocResp from 00:1c:f0:e3:13:82 (capab=0x471 status=0 aid=2)
[    9.317170] wlan0: associated
[    9.317181] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    9.872214] sky2 0000:02:00.0 eth0: speed/duplex mismatch
[   12.435943] sky2 0000:02:00.0 eth0: speed/duplex mismatch
[   14.962986] sky2 0000:02:00.0 eth0: speed/duplex mismatch
[   17.571215] sky2 0000:02:00.0 eth0: speed/duplex mismatch
[   20.208336] sky2 0000:02:00.0 eth0: speed/duplex mismatch
[   23.131227] sky2 0000:02:00.0 eth0: speed/duplex mismatch
[   25.854839] sky2 0000:02:00.0 eth0: speed/duplex mismatch
[   28.421215] sky2 0000:02:00.0 eth0: speed/duplex mismatch
[   31.205129] sky2 0000:02:00.0 eth0: speed/duplex mismatch
[   33.808134] sky2 0000:02:00.0 eth0: speed/duplex mismatch
[   36.592041] sky2 0000:02:00.0 eth0: speed/duplex mismatch
[   39.176725] sky2 0000:02:00.0 eth0: speed/duplex mismatch
[   41.832232] sky2 0000:02:00.0 eth0: speed/duplex mismatch
[   44.450974] sky2 0000:02:00.0 eth0: speed/duplex mismatch
[   47.172006] sky2 0000:02:00.0 eth0: speed/duplex mismatch
[   48.537541] systemd-hostnamed[2097]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[   49.764572] sky2 0000:02:00.0 eth0: speed/duplex mismatch

```

---

### Post by sanderj on 2013-11-24
If you Google ...

```
sky2 0000:02:00.0 eth0: speed/duplex mismatch
```

... it looks like a known bug in 2009/2010. It is suggested to update the firmware of the Marvell card.

If that doesn't help, I would try some different, forced speed/duplex settings as described here: [http://www.ubuntugeek.com/how-to-change-ethernet-network-card-speed-and-duplex-settings-in-ubuntu.html](http://www.ubuntugeek.com/how-to-change-ethernet-network-card-speed-and-duplex-settings-in-ubuntu.html)

---

### Post by telendri on 2013-11-25
As I said in my first post, I have already tried to update the firmware of the Marvell card and I had the following issue on install:
Compile the kernel (error)                                           [ failed ]

-----------

I have no internet connection so how can I install "sudo apt-get install ethtool" from Ubuntu.

Is it possible to download it from Win7 and then install it into Ubuntu?

---

### Post by chili555 on 2013-11-25
Your dmesg suggests that your wireless has a connection. Is that no longer true?

You can download ethtool here: [http://packages.ubuntu.com/saucy/ethtool](http://packages.ubuntu.com/saucy/ethtool) I believe its only dependency libc6 is already installed. Transfer it on a USB stick or similar and drag and drop it to your desktop. Then, in a terminal:```
cd Desktop
sudo dpkg -i ethtool*.deb
sudo ethtool -s eth0 speed 100 duplex full 
``` Now can you connect? If so, we can make the change persistent.

---

### Post by sanderj on 2013-11-25
> **telendri said:**
> As I said in my first post, I have already tried to update the firmware of the Marvell card and I had the following issue on install:
Compile the kernel (error)                                           [ failed ]


Compile the kernel to install *firmware* to a hardware device? I think you're mixing up firmware and Linux driver. Which instructions did you use?

---

### Post by telendri on 2013-11-25
@chili555

I succeed to install ethtool
the command "sudo ethtool eth0" gives the following:

```

sudo ethtool eth0

Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  100baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: Unknown!
    Duplex: Unknown! (255)
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pg
    Wake-on: g
    Current message level: 0x000000ff (255)
                   drv probe link timer ifdown ifup rx_err tx_err
    Link detected: no

```


the command "sudo ethtool -s eth0 autoneg off" gives :

```

Cannot set new settings: Invalid argument
  not setting autoneg


```

the command "sudo ethtool -s eth0 speed 100 duplex full" gives :

```

Cannot set new settings: Invalid argument
  not setting speed
  not setting duplex

```

---

### Post by telendri on 2013-11-25
@sanderj

Yes you're right I mix up firmware and linux driver.

I think I had tried to install the marvell linux driver with the instructions from the Marvell website 
and what to do.

```

./install.sh

1) installation
3)remove driver


```

Thus can you explain me the difference between the two concepts.

Thanks.

---

### Post by sanderj on 2013-11-25
What if you use:

```
ethtool -s eth0 autoneg off speed 100 duplex full
```


PS:

For completeness: here's a *firmware* upgrade: [http://www.neowin.net/forum/topic/890294-marvell-yukon-88e8056-issue/page-2](http://www.neowin.net/forum/topic/890294-marvell-yukon-88e8056-issue/page-2) (go to "This 88E8056 firmware update"), but I wouldn't advice you that right noew, unless your motherboard / ethernetcard is at least a few years old.

---

### Post by telendri on 2013-12-03
[COLOR=#000000]_@sanderj_[/COLOR],

I have tried the following:

ethtool -s eth0 autoneg off speed 100 duplex full

the router led was blinking after that.

Afterwards, I tried:

```

sudo ethtool -s eth0 speed 10 duplex half

```

And it works, the router led is now lighting and I have access to my router via 192.168.1.1 and to internet.

Except that when I restart the speed duplex configuration was lost, so I edit the following file like that:

```

sudo gedit etc/network/interfaces

```

```

auto lo eth0
iface lo inet loopback
up sleep -5; ethtool -s eth0 speed 10 duplex half

```



Thanks a lot to all for your help.

---


---
title: "Fresh 10.10 USB hard drive keeps unmounting"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by andyzammy on 2011-04-01
Hi all,

I've recently reconfigured my laptop to dual boot windows 7 and ubuntu 10.10. I've not done much to ubuntu apart from install the big batch of updates that usually come after you do a clean install. Not even move my movies back to the laptop. I backed everything up onto a USB hd, and several times during each of the two films I've watched from the hd so far, the hd unmounts.

Could someone please help me out in troubleshooting this because it is extremely irritating to have to cycle power to the hd just to get it back on again (last time not even that did it, had to restart the laptop). Would love to get this fixed asap otherwise I'll probably go down to 10.04.

Thanks for your time!

---

### Post by sanguinoso on 2011-04-01
Is there anything in /var/log/messages? I had a problem like that with an older, failing, hard drive; does the hard drive work fine with windows 7 and 10.04?

---

### Post by Keozon on 2011-04-01
JUst so we have more to work with, please open a new terminal (Applications -> Accessories -> Terminal) and type the following once you have the harddrive plugged in and working:

```
uname -a
sudo fdisk -l
sudo cat /etc/mtab | grep /dev
lsusb
```

and please post the results of each line here. We probably won't need a lot of that information, but it can't hurt.

---

### Post by andyzammy on 2011-04-02
Sure thing, there is so much in /var/log/messages though I can't paste it all because ubuntuforums times out trying to process it all (i guess).. here's the most recent stuff.. if that's not looking helpful i'll get some more:
```
Apr  2 11:05:13 zammy kernel: [    5.316358] ata5.00: configured for UDMA/100
Apr  2 11:05:13 zammy kernel: [    5.328270] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-6 01.0 PQ: 0 ANSI: 5
Apr  2 11:05:13 zammy kernel: [    5.328392] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  2 11:05:13 zammy kernel: [    5.328457] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Apr  2 11:05:13 zammy kernel: [    5.328492] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-6 01.0 PQ: 0 ANSI: 5
Apr  2 11:05:13 zammy kernel: [    5.328511] sd 0:0:0:0: [sda] Write Protect is off
Apr  2 11:05:13 zammy kernel: [    5.328532] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  2 11:05:13 zammy kernel: [    5.328607] sd 1:0:0:0: Attached scsi generic sg1 type 0
Apr  2 11:05:13 zammy kernel: [    5.328691]  sda:
Apr  2 11:05:13 zammy kernel: [    5.328858] sd 1:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Apr  2 11:05:13 zammy kernel: [    5.328975] sd 1:0:0:0: [sdb] Write Protect is off
Apr  2 11:05:13 zammy kernel: [    5.329022] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  2 11:05:13 zammy kernel: [    5.329160]  sdb:
Apr  2 11:05:13 zammy kernel: [    5.333671] scsi 4:0:0:0: CD-ROM            Optiarc  BD ROM BC-5500S  1.83 PQ: 0 ANSI: 5
Apr  2 11:05:13 zammy kernel: [    5.335175] sr0: scsi3-mmc drive: 31x/31x writer dvd-ram cd/rw xa/form2 cdda tray
Apr  2 11:05:13 zammy kernel: [    5.335179] Uniform CD-ROM driver Revision: 3.20
Apr  2 11:05:13 zammy kernel: [    5.335335] sr 4:0:0:0: Attached scsi generic sg2 type 5
Apr  2 11:05:13 zammy kernel: [    5.356122] firewire_core: created device fw0: GUID 893f0200183740d9, S400
Apr  2 11:05:13 zammy kernel: [    5.373468]  sdb1 sdb2 < sdb5 >
Apr  2 11:05:13 zammy kernel: [    5.398291] sd 1:0:0:0: [sdb] Attached SCSI disk
Apr  2 11:05:13 zammy kernel: [    5.625574]  sda1 sda2
Apr  2 11:05:13 zammy kernel: [    5.625916] sd 0:0:0:0: [sda] Attached SCSI disk
Apr  2 11:05:13 zammy kernel: [    5.636040] usb 5-2: new low speed USB device using uhci_hcd and address 2
Apr  2 11:05:13 zammy kernel: [    5.824555] usbcore: registered new interface driver hiddev
Apr  2 11:05:13 zammy kernel: [    5.837175] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input5
Apr  2 11:05:13 zammy kernel: [    5.837253] generic-usb 0003:045E:0083.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.0-2/input0
Apr  2 11:05:13 zammy kernel: [    5.837266] usbcore: registered new interface driver usbhid
Apr  2 11:05:13 zammy kernel: [    5.837267] usbhid: USB HID core driver
Apr  2 11:05:13 zammy kernel: [    6.059456] EXT4-fs (sdb1): INFO: recovery required on readonly filesystem
Apr  2 11:05:13 zammy kernel: [    6.059460] EXT4-fs (sdb1): write access will be enabled during recovery
Apr  2 11:05:13 zammy kernel: [   10.058834] EXT4-fs (sdb1): orphan cleanup on readonly fs
Apr  2 11:05:13 zammy kernel: [   10.059113] EXT4-fs (sdb1): 4 orphan inodes deleted
Apr  2 11:05:13 zammy kernel: [   10.059116] EXT4-fs (sdb1): recovery complete
Apr  2 11:05:13 zammy kernel: [   10.674947] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
Apr  2 11:05:13 zammy kernel: [   22.827988] udev[396]: starting version 163
Apr  2 11:05:13 zammy kernel: [   23.029338] lp: driver loaded but no devices found
Apr  2 11:05:13 zammy kernel: [   23.036978] Adding 9936892k swap on /dev/sdb5.  Priority:-1 extents:1 across:9936892k 
Apr  2 11:05:13 zammy kernel: [   23.064419] Linux agpgart interface v0.103
Apr  2 11:05:13 zammy kernel: [   23.158528] jmb38x_ms 0000:06:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  2 11:05:13 zammy kernel: [   23.158898] lirc_dev: IR Remote Control driver registered, major 249 
Apr  2 11:05:13 zammy kernel: [   23.158964] lirc_ene0100: module is from the staging directory, the quality is unknown, you have been warned.
Apr  2 11:05:13 zammy kernel: [   23.159531] enecir 00:0a: lirc_dev: driver enecir registered at minor = 0
Apr  2 11:05:13 zammy kernel: [   23.159590] enecir: KB3926C detected, driver support is not complete!
Apr  2 11:05:13 zammy kernel: [   23.159599] enecir: hardware features:
Apr  2 11:05:13 zammy kernel: [   23.159600] enecir: learning and tx off, gpio40_learn off, fan_in off
Apr  2 11:05:13 zammy kernel: [   23.159601] enecir: driver has been succesfully loaded
Apr  2 11:05:13 zammy kernel: [   23.159853] lis3lv02d: hardware type DV7 found.
Apr  2 11:05:13 zammy kernel: [   23.160575] lis3lv02d: 8 bits sensor found
Apr  2 11:05:13 zammy kernel: [   23.222166] Bluetooth: Core ver 2.15
Apr  2 11:05:13 zammy kernel: [   23.222202] NET: Registered protocol family 31
Apr  2 11:05:13 zammy kernel: [   23.222204] Bluetooth: HCI device and connection manager initialized
Apr  2 11:05:13 zammy kernel: [   23.222207] Bluetooth: HCI socket layer initialized
Apr  2 11:05:13 zammy kernel: [   23.224637] Bluetooth: Generic Bluetooth USB driver ver 0.6
Apr  2 11:05:13 zammy kernel: [   23.229971] cfg80211: Calling CRDA to update world regulatory domain
Apr  2 11:05:13 zammy kernel: [   23.235983] usbcore: registered new interface driver btusb
Apr  2 11:05:13 zammy kernel: [   23.264640] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input6
Apr  2 11:05:13 zammy kernel: [   23.264746] lis3lv02d driver loaded.
Apr  2 11:05:13 zammy kernel: [   23.265132] input: HP WMI hotkeys as /devices/virtual/input/input7
Apr  2 11:05:13 zammy kernel: [   23.271345] Linux video capture interface: v2.00
Apr  2 11:05:13 zammy kernel: [   23.276752] uvcvideo: Found UVC 1.00 device HP Webcam  (046d:09b8)
Apr  2 11:05:13 zammy kernel: [   23.289382] cfg80211: World regulatory domain updated:
Apr  2 11:05:13 zammy kernel: [   23.289384]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr  2 11:05:13 zammy kernel: [   23.289387]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 11:05:13 zammy kernel: [   23.289390]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  2 11:05:13 zammy kernel: [   23.289392]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  2 11:05:13 zammy kernel: [   23.289394]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 11:05:13 zammy kernel: [   23.289396]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 11:05:13 zammy kernel: [   23.293010] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
Apr  2 11:05:13 zammy kernel: [   23.296799] input: HP Webcam  as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input8
Apr  2 11:05:13 zammy kernel: [   23.297085] usbcore: registered new interface driver uvcvideo
Apr  2 11:05:13 zammy kernel: [   23.297087] USB Video Class driver (v0.1.0)
Apr  2 11:05:13 zammy kernel: [   23.335741] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
Apr  2 11:05:13 zammy kernel: [   23.335744] iwlagn: Copyright(c) 2003-2010 Intel Corporation
Apr  2 11:05:13 zammy kernel: [   23.335798] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  2 11:05:13 zammy kernel: [   23.335835] iwlagn 0000:02:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
Apr  2 11:05:13 zammy kernel: [   23.355356] type=1400 audit(1301738712.446:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=648 comm="apparmor_parser"
Apr  2 11:05:13 zammy kernel: [   23.355926] type=1400 audit(1301738712.446:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=648 comm="apparmor_parser"
Apr  2 11:05:13 zammy kernel: [   23.356266] type=1400 audit(1301738712.450:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=648 comm="apparmor_parser"
Apr  2 11:05:13 zammy kernel: [   23.357431] type=1400 audit(1301738712.450:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=677 comm="apparmor_parser"
Apr  2 11:05:13 zammy kernel: [   23.358009] type=1400 audit(1301738712.450:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=677 comm="apparmor_parser"
Apr  2 11:05:13 zammy kernel: [   23.358324] type=1400 audit(1301738712.450:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=677 comm="apparmor_parser"
Apr  2 11:05:13 zammy kernel: [   23.360995] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Apr  2 11:05:13 zammy kernel: [   23.381119] acpi device:06: registered as cooling_device3
Apr  2 11:05:13 zammy kernel: [   23.382955] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input9
Apr  2 11:05:13 zammy kernel: [   23.383001] ACPI: Video Device [EVGA] (multi-head: yes  rom: no  post: no)
Apr  2 11:05:13 zammy kernel: [   23.440114] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
Apr  2 11:05:13 zammy kernel: [   23.447917] iwlagn 0000:02:00.0: loaded firmware version 8.24.2.12
Apr  2 11:05:13 zammy kernel: [   23.480602] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
Apr  2 11:05:13 zammy kernel: [   23.480615] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 22 (level, low) -> IRQ 22
Apr  2 11:05:13 zammy kernel: [   23.556439] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Apr  2 11:05:13 zammy kernel: [   23.556554] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
Apr  2 11:05:13 zammy kernel: [   23.868423] nvidia: module license 'NVIDIA' taints kernel.
Apr  2 11:05:13 zammy kernel: [   23.868428] Disabling lock debugging due to kernel taint
Apr  2 11:05:13 zammy kernel: [   23.949172] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
Apr  2 11:05:13 zammy kernel: [   24.024802] type=1400 audit(1301738713.118:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=969 comm="apparmor_parser"
Apr  2 11:05:13 zammy kernel: [   24.029764] type=1400 audit(1301738713.122:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=970 comm="apparmor_parser"
Apr  2 11:05:13 zammy kernel: [   24.030337] type=1400 audit(1301738713.122:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=970 comm="apparmor_parser"
Apr  2 11:05:13 zammy kernel: [   24.030655] type=1400 audit(1301738713.122:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=970 comm="apparmor_parser"
Apr  2 11:05:13 zammy kernel: [   24.757093] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  2 11:05:13 zammy kernel: [   24.757125] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Apr  2 11:05:13 zammy kernel: [   24.757242] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010
Apr  2 11:05:13 zammy kernel: [   24.835860] Bluetooth: L2CAP ver 2.14
Apr  2 11:05:13 zammy kernel: [   24.835863] Bluetooth: L2CAP socket layer initialized
Apr  2 11:05:13 zammy kernel: [   24.837970] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1a0b1, caps: 0xd04751/0xa00000/0x20000
Apr  2 11:05:13 zammy kernel: [   24.841666] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr  2 11:05:13 zammy kernel: [   24.841669] Bluetooth: BNEP filters: protocol multicast
Apr  2 11:05:13 zammy kernel: [   24.845332] Bluetooth: SCO (Voice Link) ver 0.6
Apr  2 11:05:13 zammy kernel: [   24.845334] Bluetooth: SCO socket layer initialized
Apr  2 11:05:14 zammy kernel: [   24.929057] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  2 11:05:14 zammy kernel: [   24.930529] r8169 0000:05:00.0: eth0: link down
Apr  2 11:05:14 zammy kernel: [   24.930678] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  2 11:05:14 zammy kernel: [   24.962342] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input12
Apr  2 11:05:14 zammy kernel: [   24.974191] Bluetooth: RFCOMM TTY layer initialized
Apr  2 11:05:14 zammy kernel: [   24.974195] Bluetooth: RFCOMM socket layer initialized
Apr  2 11:05:14 zammy kernel: [   24.974197] Bluetooth: RFCOMM ver 1.11
Apr  2 11:05:14 zammy kernel: [   25.603205] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro,commit=0
Apr  2 11:05:17 zammy kernel: [   28.538896] audit_printk_skb: 18 callbacks suppressed
Apr  2 11:05:17 zammy kernel: [   28.538899] type=1400 audit(1301738717.630:18): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1227 comm="apparmor_parser"
Apr  2 11:05:17 zammy kernel: [   28.539599] type=1400 audit(1301738717.630:19): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1227 comm="apparmor_parser"
Apr  2 11:05:17 zammy kernel: [   28.583494] ppdev: user-space parallel port driver
Apr  2 11:05:28 zammy kernel: [   39.473045] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro,commit=0
Apr  2 11:05:30 zammy kernel: [   41.695707] UDF-fs: Partition marked readonly; forcing readonly mount
Apr  2 11:05:30 zammy kernel: [   41.818198] UDF-fs INFO UDF: Mounting volume 'NEU', timestamp 2010/09/23 14:34 (103c)
Apr  2 11:05:31 zammy kernel: [   42.792345] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr  2 11:05:32 zammy kernel: [   43.235262] padlock: VIA PadLock not detected.
Apr  2 11:05:50 zammy kernel: [   60.960101] usb 2-1: new high speed USB device using ehci_hcd and address 4
Apr  2 11:05:51 zammy kernel: [   61.162902] Initializing USB Mass Storage driver...
Apr  2 11:05:51 zammy kernel: [   61.163084] scsi6 : usb-storage 2-1:1.0
Apr  2 11:05:51 zammy kernel: [   61.163201] usbcore: registered new interface driver usb-storage
Apr  2 11:05:51 zammy kernel: [   61.163203] USB Mass Storage support registered.
Apr  2 11:05:54 zammy kernel: [   64.204009] scsi 6:0:0:0: Direct-Access     SAMSUNG  HD103SI               PQ: 0 ANSI: 2 CCS
Apr  2 11:05:54 zammy kernel: [   64.204481] sd 6:0:0:0: Attached scsi generic sg3 type 0
Apr  2 11:05:59 zammy kernel: [   69.571065] sd 6:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Apr  2 11:05:59 zammy kernel: [   69.571866] sd 6:0:0:0: [sdc] Write Protect is off
Apr  2 11:05:59 zammy kernel: [   69.573668]  sdc: unknown partition table
Apr  2 11:05:59 zammy kernel: [   69.591909] sd 6:0:0:0: [sdc] Attached SCSI disk
Apr  2 11:05:59 zammy kernel: [   70.079818] EXT3-fs: barriers not enabled
Apr  2 11:06:00 zammy kernel: [   70.413730] kjournald starting.  Commit interval 5 seconds
Apr  2 11:06:00 zammy kernel: [   70.414910] EXT3-fs (sdc): using internal journal
Apr  2 11:06:00 zammy kernel: [   70.414915] EXT3-fs (sdc): recovery complete
Apr  2 11:06:00 zammy kernel: [   70.415409] EXT3-fs (sdc): mounted filesystem with ordered data mode
```



uname -a:
```
Linux zammy 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux
```

sudo fdisk -l:
```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6b2a6b2a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       30402   244093952    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000503a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29165   234259456   83  Linux
/dev/sdb2           29165       30402     9936897    5  Extended
/dev/sdb5           29165       30402     9936896   82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

```

sudo cat /etc/mtab | grep /dev:
```
/dev/sdb1 / ext4 rw,errors=remount-ro,commit=0 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
/dev/sr0 /media/NEU udf ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077 0 0
/dev/sdc /media/EXTHD1TB ext3 rw,nosuid,nodev,uhelper=udisks 0 0
/dev/sda2 /media/7802D98402D947B0 fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0

```

lsusb:
```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. transcend storejet 25P
Bus 002 Device 003: ID 046d:09b8 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

If you need any more info just ask. Thanks for the help with this! :)

P.S. i sure would love confirmation that it's not my HD dying on me, its not exactly brand new (year old maybe.. 2?) but i haven't used it much at all..

---

### Post by Keozon on 2011-04-04
Interesting. I apologize for taking so long to reply. Academia has me swamped at the moment (and hence this reply won't be as helpful as it probably should be, but I'll get back to you again when things calm down in a bit). 

I'm guessing that the USB drive is 1TB? Considering its the only thing that looks like its not a boot device. See, the interesting thing is, when I plug in my external HD, and most others, I would think, the applicable line in lsusb looks like this:
```
Bus 001 Device 003: ID 1058:1010 Western Digital Technologies, Inc. 
```

Compare that to yours, and you'll notice that your drive actually shows the USB to SATA adapter:
```
Bus 002 Device 004: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. transcend storejet 25P
```

 This probably just means its an off brand, but it could mean its not a standard mass storage driver it uses (which would be odd). Is it by chance one of those new Seagate drives that adapts formats to the OS that is accessing it? 

A really quick google search of that adapter came up with [this.]("http://ubuntuforums.org/showthread.php?t=966321") Everyone there seems to have problems (although varying) with JMicron adapters. I don't have time at the moment to read through all the posts.

Notice, however, that fdisk -l only listed the physical drive -- no partitions! This is not normal for initialized disks. Also, mtab only lists the device again. My guess, although unhelpful at the moment, is that different software is conflicting with the drive. Something in Ubuntu works with it, recognizes all the partitions, etc, and, obviously, certain parts don't.

Is the format of the drive ext3 as listed in mtab?

---

### Post by rosencrantz on 2011-04-04
Does the drive have an independent power supply? Sometimes USB power just doesn't cut the mustard.

---


---
title: "How to mount a Sd card Acer aspire"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by DMKryl on 2010-12-28
Hi i'm trying to mount a sd card but i'm a total noob in linux, i have not the slightest idea how to do it, and google didn't help, so how do i mount the sd card, i found some commands but i'm not able to understand it

```
kryl@Sasha:~$ dmesg | tail
[ 9815.933846] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9817.171823] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 9826.016042] wlan0: no IPv6 routers present
[10863.800572] usb 3-1: new low speed USB device using uhci_hcd and address 2
[10864.236753] usbcore: registered new interface driver hiddev
[10864.250736] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input8
[10864.250887] generic-usb 0003:0458:003A.0001: input,hidraw0: USB HID v1.11 Mouse [Genius Optical Mouse] on usb-0000:00:1a.0-1/input0
[10864.250920] usbcore: registered new interface driver usbhid
[10864.250923] usbhid: USB HID core driver
[14896.643086] ACPI: EC: GPE storm detected, transactions will use polling mode
kryl@Sasha:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
04:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
05:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
07:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
07:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
07:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
07:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
```

---

### Post by garvinrick4 on 2010-12-28
Put card in and run this in a termial:
```
sudo fdisk -l
``` (lower case L)
Now post results here.

---

### Post by garvinrick4 on 2010-12-28
You must have figured it out. But to mount something in linux you have to make a directory in media and then mount in directory.
sudo mkdir /media/card
sudo mount /dev/sdc1 /media/card
or flash drives or whatever. 
In configuration editor there is a setting to auto mount and auto open at boot.
Apps/Nautilus/preferences/

---

### Post by DMKryl on 2010-12-29
I created a dir calle sdcard an this is the terminal output with an external usb disc (has a wsbf hidden partition) and the sd

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1fea0fd5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11432    91826176   83  Linux
/dev/sda2           11749       30401   149830222+   7  HPFS/NTFS
/dev/sda4           11433       11748     2538270   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x15f44953

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       41679   334783488    7  HPFS/NTFS
/dev/sdb2           41679       60802   153600000    7  HPFS/NTFS

Disk /dev/sdc: 8188 MB, 8188329984 bytes
252 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 15624 * 512 = 7999488 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?       49804      122866   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(49803, 223, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(122865, 44, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?       10797      134711   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(10796, 206, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(134710, 140, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?      119681      243594   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(119680, 18, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(243593, 203, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?      184696      184699       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(184695, 104, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(184698, 243, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```

---

### Post by DMKryl on 2011-02-07
it's been a while but i believe i found the problem but i don't know what this means:
this was the error output when i put dmesg | tail
mmc0: error -110 whilst initialising SD card
anyone knows what this means?

---

### Post by degarb on 2012-03-13
No sdc1.  I see the light on when inserting the card.

fdisk -l :

isk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b8541

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29165   234259456   83  Linux
/dev/sda2           29165       30402     9936897    5  Extended
/dev/sda5           29165       30402     9936896   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2ef25992

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       57154   459088867+   7  HPFS/NTFS
/dev/sdb2           57155       60802    29295617    5  Extended
/dev/sdb4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.
/dev/sdb5           57155       60802    29294592   83  Linux

---


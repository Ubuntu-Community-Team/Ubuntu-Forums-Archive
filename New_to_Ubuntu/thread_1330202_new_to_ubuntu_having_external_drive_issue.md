---
title: "new to ubuntu having external drive issue"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by corky748 on 2009-11-18
we i plug in my 60gb external hard drive nothing happens
i tried lsusb but it's not there!!!
any ideas???

laptop:~$ lsusb
Bus 004 Device 003: ID 0846:4260 NetGear, Inc. WG111v3 54 Mbps Wireless [realtek RTL8187B]
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 062a:0000 Creative Labs Optical mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by diablo75 on 2009-11-18
What kind of HD is it?  (The make and model number would be great).

---

### Post by corky748 on 2009-11-18
it is a western digital Scorpio (wd1600bevs)

---

### Post by carniola on 2009-11-18
Have you tried plugging it into a usb port at the back of the computer? I have a WD external drive that doesn't show up if plugged into a USB hub or in the front panel.

---

### Post by corky748 on 2009-11-18
I had it pluged into the back and put it into a pci card and got a different responce when i tried lsusb in the terminal

laptop:~$ lsusb
Bus 004 Device 005: ID 0dc4:00d4 Macpower Peripherals, Ltd 
Bus 004 Device 004: ID 0846:4260 NetGear, Inc. WG111v3 54 Mbps Wireless [realtek RTL8187B]
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by corky748 on 2009-11-18
i found this command a another forum sudo fdisk -l  but the external drive  isn't there so it can't see my drive, how do i force it to look for it???

adam@adam-laptop:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd478bc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2341    18804051   83  Linux
/dev/sda2            2342        2432      730957+   5  Extended
/dev/sda5            2342        2432      730926   82  Linux swap / Solaris

---

### Post by nothingspecial on 2009-11-18
Unplug it, then plug it back in again then type ```
dmesg | tail -n 25
```

Then post the output back here.

---

### Post by corky748 on 2009-11-18
adam@adam-laptop:~$ dmesg | tail -n 25
[ 7412.028497] sd 103:0:0:0: [sdb] Attached SCSI disk
[ 7412.028714] sd 103:0:0:0: Attached scsi generic sg2 type 0
[ 7425.005642] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7441.757578] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7454.853405] wlan0: authenticate with AP 00:0f:cc:9a:8e:74
[ 7454.854915] wlan0: authenticated
[ 7454.854922] wlan0: associate with AP 00:0f:cc:9a:8e:74
[ 7454.857070] wlan0: RX AssocResp from 00:0f:cc:9a:8e:74 (capab=0x451 status=0 aid=1)
[ 7454.857080] wlan0: associated
[ 7454.875994] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7465.416077] wlan0: no IPv6 routers present
[ 8893.504158] usb 1-1: new low speed USB device using uhci_hcd and address 105
[ 8893.659432] usb 1-1: configuration #1 chosen from 1 choice
[ 8893.686705] input: HID 062a:0000 as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input10
[ 8893.717443] generic-usb 0003:062A:0000.0002: input,hidraw0: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:1d.0-1/input0
[10453.155438] usb 4-1: USB disconnect, address 5
[10476.024104] usb 4-1: new high speed USB device using ehci_hcd and address 6
[10476.164517] usb 4-1: configuration #1 chosen from 1 choice
[10476.181654] scsi104 : SCSI emulation for USB Mass Storage devices
[10476.187018] usb-storage: device found at 6
[10476.187026] usb-storage: waiting for device to settle before scanning
[10481.185056] usb-storage: device scan complete
[10481.186210] scsi 104:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[10481.194686] sd 104:0:0:0: [sdb] Attached SCSI disk
[10481.194848] sd 104:0:0:0: Attached scsi generic sg2 type 0
adam@adam-laptop:~$

---

### Post by nothingspecial on 2009-11-18
> **corky748 said:**
> 
[10453.155438] usb 4-1: USB disconnect, address 5
[10476.024104] usb 4-1: new high speed USB device using ehci_hcd and address 6
[10476.164517] usb 4-1: configuration #1 chosen from 1 choice
[10476.181654] scsi104 : SCSI emulation for USB Mass Storage devices
[10476.187018] usb-storage: device found at 6
[10476.187026] usb-storage: waiting for device to settle before scanning
[10481.185056] usb-storage: device scan complete
[10481.186210] scsi 104:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[10481.194686] sd 104:0:0:0: [sdb] Attached SCSI disk
[10481.194848] sd 104:0:0:0: Attached scsi generic sg2 type 0
adam@adam-laptop:~$

Strange. As you can see from the first line I`ve quoted, Ubuntu registered that you had unplugged it and then, from the lines after that, that you plugged it back in again.

What`s the drives file system?

---

### Post by corky748 on 2009-11-18
what do you mean by file system?

---

### Post by nothingspecial on 2009-11-18
fat32, ntfs, ext3 etc etc

---

### Post by philinux on 2009-11-18
Does the drive show up under System>admin>disk utility?

---

### Post by corky748 on 2009-11-18
no i can't find it anywhere

---

### Post by corky748 on 2009-11-18
i don't know what system file it is, it was on windows xp i think it's fat32 or ntfs

---

### Post by philinux on 2009-11-18
Try installing gparted from synaptic then run it from system>admin>partition editor. See if the disk shows up there.

Or install by clicking the link below.

[apt:gparted]("apt:gparted")

---

### Post by corky748 on 2009-11-18
I tried "partition editor" and nothing came up. i also tried "mount manager"  which saw when i plugged it out and notified me when i plugged it back in.
but it still can't see it any where (it called it dev/sdb)

---


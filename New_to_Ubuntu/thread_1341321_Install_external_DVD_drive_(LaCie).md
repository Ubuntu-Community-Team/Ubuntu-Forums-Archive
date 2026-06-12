---
title: "Install external DVD drive (LaCie)"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by mwybo on 2009-11-29
Hi,
I am unable to install an external LaCie DVD drive on my ubuntu netbook remix Dell mini9. The drive does not mount. The drivers fom LaCie are but a set of folders and files, I have no idea what to do with them.

I have spent several hours already trying to find a solution. I just want to use a USB DVD drive. Is it supposed to be this hard?

Thanks for any help. 

Mwy

---

### Post by halitech on 2009-11-29
with the drive disconnected run
```
lsusb
```
first digit is a lower case L, not the number 1
plug the drive in, wait 30 seconds and run the command again. Also run 
```
dmesg | tail
```
post the results of all 3 so we can see whats going on

---

### Post by mwybo on 2009-11-29
Hi,

mdw@Red:~$ lsusb
Bus 005 Device 002: ID 413c:02b0 Dell Computer Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
mdw@Red:~$ 

After plugging in the drive
mdw@Red:~$ lsusb
Bus 005 Device 002: ID 413c:02b0 Dell Computer Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 059f:0643 LaCie, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
mdw@Red:~$

dmesg | tail
[  852.721303] usb 1-1: configuration #1 chosen from 1 choice
[  852.737588] scsi4 : SCSI emulation for USB Mass Storage devices
[  852.746268] usb-storage: device found at 7
[  852.746276] usb-storage: waiting for device to settle before scanning
[  857.744559] usb-storage: device scan complete
[  879.112174] usb 1-1: reset high speed USB device using ehci_hcd and address 7
[  880.534653] scsi 4:0:0:0: CD-ROM            TSSTcorp CDDVDW SN-S082N  LA00 PQ: 0 ANSI: 0
[  880.976706] sr0: scsi3-mmc drive: 8x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[  880.977179] sr 4:0:0:0: Attached scsi CD-ROM sr0
[  880.977492] sr 4:0:0:0: Attached scsi generic sg1 type 5
mdw@Red:~$

---

### Post by halitech on 2009-11-29
I don't see any issues with any of the info. Have you tried putting a cd in and see what happens?

---

### Post by mwybo on 2009-11-29
hi,
it just keeps grinding away trying to read the cd. I have installed it on a windows machine and the drive is functional.

---

### Post by mwybo on 2009-11-29
I downloaded drivers from the LaCie site.

One folder etc with a file lightscribe.rc whose contents is:

ResourceDir=/usr/lib/lightscribe/res;
UpdateScriptDir=/usr/lib/lightscribe/updates;


and another folder usr containing many other folders and files.

---

### Post by SunnyRabbiera on 2009-11-29
Try a restart with the drive plugged in, its obvious the drive works if you can read files from it but maybe a restart is needed to ensure the kernel sees and mounts the device properly.
I had a issue like this with a USB external HD drive.

---

### Post by mwybo on 2009-11-29
On restart with drive plugged in it hangs at the DELL screen with the drive grinding away as usual.

---


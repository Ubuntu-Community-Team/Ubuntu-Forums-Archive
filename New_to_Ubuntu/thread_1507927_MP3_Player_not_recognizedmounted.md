---
title: "MP3 Player not recognized/mounted"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by Sly1972 on 2010-06-12
I have recently installed 10.04 on an old laptop (Fujitsu-Siemens Amilo L7310). The USB ports of this pc are 1.1, not 2.0. I don't know if there is a link but it takes ages between the moment you plug a USB hardware (USB stick, printer...), even one that has been plugged in before, and the moment you can use it. For instance, for a USB Stick, it takes quite a bit of time for the system to detect that something has been pluggeg in (4-5 min), detect what it is (4-5 min), mount it (2-3 min) and display the content in nautilus (2-3 min).
 
It is a pain and difficult to live with. It gets even weirder with the 2 MP3 players I have. The first is an MP3/4 player with a Micro SD slot.
 
lsusb indicates:
~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0402:5668 ALi Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
dmesg indicates:
[ 3565.732039] usb 1-3: new high speed USB device using ehci_hcd and address 2
[ 3570.732054] ehci_hcd 0000:00:10.3: Unlink after no-IRQ? Controller is probably using the wrong IRQ.
[ 3581.288047] usb 1-3: device not accepting address 2, error -110
[ 3581.400036] usb 1-3: new high speed USB device using ehci_hcd and address 3
[ 3596.956033] usb 1-3: device not accepting address 3, error -110
[ 3597.068056] usb 1-3: new high speed USB device using ehci_hcd and address 4
[ 3607.500043] usb 1-3: device not accepting address 4, error -110
[ 3607.612043] usb 1-3: new high speed USB device using ehci_hcd and address 5
[ 3618.044038] usb 1-3: device not accepting address 5, error -110
[ 3618.044069] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 3785.052044] usb 3-1: new full speed USB device using uhci_hcd and address 2
[ 3786.136054] usb 3-1: not running at top speed; connect to a high speed hub
[ 3788.616259] usb 3-1: configuration #1 chosen from 1 choice
[ 3788.941266] Initializing USB Mass Storage driver...
[ 3789.061314] scsi2 : SCSI emulation for USB Mass Storage devices
[ 3789.061614] usbcore: registered new interface driver usb-storage
[ 3789.061619] USB Mass Storage support registered.
[ 3789.078557] usb-storage: device found at 2
[ 3789.078563] usb-storage: waiting for device to settle before scanning
[ 3794.320140] usb-storage: device scan complete
[ 3795.064149] scsi 2:0:0:0: Direct-Access Audio Player PQ: 0 ANSI: 0 CCS
[ 3795.808128] scsi 2:0:0:1: Direct-Access SD/MMC CARD PQ: 0 ANSI: 0 CCS
[ 3795.811681] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 3795.813131] sd 2:0:0:1: Attached scsi generic sg3 type 0
[ 3798.288101] sd 2:0:0:0: [sdb] 1992448 512-byte logical blocks: (1.02 GB/972 MiB)
[ 3800.272073] sd 2:0:0:0: [sdb] Write Protect is off
[ 3800.272083] sd 2:0:0:0: [sdb] Mode Sense: 3b 00 00 00
[ 3800.272087] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3810.192260] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3810.192276] sdb: sdb1
[ 3819.616102] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3819.616115] sd 2:0:0:0: [sdb] Attached SCSI removable disk
 
In Nautilus, only the MicroSD (even if none is inserted) is available, Nothing is displayed/avaialble for the intenal memory. Any idea what is happening?
 
The second is a simple MP3 player with flash memory.
 
lsusb indicates:
~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0603:b5d3 Novatek Microelectronics Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
dmesg indicates:
[ 7347.964093] usb 1-3: new high speed USB device using ehci_hcd and address 6
[ 7363.520045] usb 1-3: device not accepting address 6, error -110
[ 7363.632041] usb 1-3: new high speed USB device using ehci_hcd and address 7
[ 7379.236039] usb 1-3: device not accepting address 7, error -110
[ 7379.348041] usb 1-3: new high speed USB device using ehci_hcd and address 8
[ 7389.780044] usb 1-3: device not accepting address 8, error -110
[ 7389.892053] usb 1-3: new high speed USB device using ehci_hcd and address 9
[ 7400.324048] usb 1-3: device not accepting address 9, error -110
[ 7400.324084] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 7864.300044] usb 3-1: new full speed USB device using uhci_hcd and address 3
[ 7869.300034] uhci_hcd 0000:00:10.1: Unlink after no-IRQ? Controller is probably using the wrong IRQ.
[ 7870.696063] usb 3-1: not running at top speed; connect to a high speed hub
[ 7873.176272] usb 3-1: configuration #1 chosen from 1 choice
[ 7873.430427] scsi3 : SCSI emulation for USB Mass Storage devices
[ 7873.437236] usb-storage: device found at 3
[ 7873.437242] usb-storage: waiting for device to settle before scanning
[ 7878.632133] usb-storage: device scan complete
[ 7879.376143] scsi 3:0:0:0: Direct-Access General Flash Disk Drive 2.05 PQ: 0 ANSI: 2 CCS
[ 7879.379408] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 7880.616112] sd 3:0:0:0: [sdb] 4008960 512-byte logical blocks: (2.05 GB/1.91 GiB)
[ 7881.360114] sd 3:0:0:0: [sdb] Write Protect is off
[ 7881.360122] sd 3:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 7881.360127] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 7884.336106] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 7884.336122] sdb:
[ 7888.552128] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 7888.552142] sd 3:0:0:0: [sdb] Attached SCSI removable disk
 
Nautilus shows 2 entries (image 1). One called USB0 allows to navigate the content of the memory, but not to add to it (image 2). The other, when you select it, is unusable (image 3).
 
Any idea what is happening here?

---

### Post by cariboo on 2010-06-12
I have an inexpensive RCA/Audiovox mp3 player, it has selectable modes, check to see if you can set yours to MPT.

---

### Post by Sly1972 on 2010-06-14
Thanks for the feedback.

Unfortunately, the info I gave you is wrong: the problem happens not only with the MP3 player, but also with any other flash-based hardware (e.g. USB stick) with exactly the same messages from lsusb and dmeg. 

Any idea what I am missing?

---

### Post by cariboo on 2010-06-14
It looks like your devices are being detected, it's just that they aren't being auto-mount. Can you mount the device manually?

```
sudo mount /dev/sdb1 /mnt
```

It also looks like your flash drive doesn't have a partition on it.

---

### Post by Chronon on 2010-06-14
Some devices don't use a partition table.  I don't think this is a problem, you just need to mount the device directly rather than trying to mount a partition.

I have no useful feedback on OP's general USB problems, I'm afraid.

---

### Post by Sly1972 on 2010-06-16
Hi,
 
Should I do this before or after pluggin the device? Tried after it was plugged and recognized: it did not work. Had a look at the ETC folder: no sdb1 entry, only sdb.
 
I had a look at the following thread: [http://ubuntuforums.org/showthread.php?t=1470918&page=3](http://ubuntuforums.org/showthread.php?t=1470918&page=3) and implemented both suggestions.
 
Now here is the interresting thing: when the USB device is plugged in at boot time, it is mounted correctly(:p), but the permissions are set to root(:confused:), so no normal users can modify the content of the device.
 
If the device is plugged in after boot-up, then then issue is still here.
 
Interrestingly, in both cases, the messages from dmesg has changed:
[ 172.796038] usb 2-1: new full speed USB device using uhci_hcd and address 2
[ 176.232269] usb 2-1: configuration #1 chosen from 1 choice
[ 176.549636] Initializing USB Mass Storage driver...
[ 176.549824] scsi2 : SCSI emulation for USB Mass Storage devices
[ 176.550078] usbcore: registered new interface driver usb-storage
[ 176.550082] USB Mass Storage support registered.
[ 176.564197] usb-storage: device found at 2
[ 176.564203] usb-storage: waiting for device to settle before scanning
[ 181.688124] usb-storage: device scan complete
[ 182.432135] scsi 2:0:0:0: Direct-Access General Flash Disk Drive 2.05 PQ: 0 ANSI: 2 CCS
[ 182.435486] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 183.672097] sd 2:0:0:0: [sdb] 4008960 512-byte logical blocks: (2.05 GB/1.91 GiB)
[ 184.416105] sd 2:0:0:0: [sdb] Write Protect is off
[ 184.416115] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 184.416119] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 187.392108] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 187.392123] sdb:
[ 191.608111] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 191.608126] sd 2:0:0:0: [sdb] Attached SCSI removable disk
 
 
Any idea that could help me?
 
Thanks in advance
 
By the way, when trying to unmount the device, I get messages indicating that the device is not listed in fstab. Any idea what this means? How can I access what information are stored in fstab?

---

### Post by Sly1972 on 2010-06-18
Right. I got fed-up. I wiped everything out and reinstalled everything. Net result:
1/ Simple USB Flash devices are being mounted correctly (but still takes ages)
2/ MountManager does not detect the device, but it is available in Nautilus
3/ The internal memory of the player with  the Micro-sd slot is still not mounted (but the card reader is!)
Thanks for any insight anyone can provide.

---


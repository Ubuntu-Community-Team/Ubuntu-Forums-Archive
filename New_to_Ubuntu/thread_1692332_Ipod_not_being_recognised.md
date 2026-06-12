---
title: "Ipod not being recognised"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by Blue Summer on 2011-02-21
I ran a lsusb that I saw in another older thread and got this:


Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1532:0001 Razer USA, Ltd RZ01-020300 Optical Mouse [Diamondback]
Bus 002 Device 002: ID 1532:010b Razer USA, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 05ac:1260 Apple, Inc. iPod Nano 2.Gen
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


So it seems like it's finding it, but I've not got an icon anywere to open it and it's not being seen in Rhythmbox

---

### Post by fooman on 2011-02-21
in your top panel....go to places > home folder

does it show up as a device in the left hand column along with your other drives/partitions/folders?

---

### Post by Blue Summer on 2011-02-21
Nope, nothing like that in my home folder but I know what you mean and it's not appearing as a device like my dvd drive and my partitions

---

### Post by philinux on 2011-02-21
> **Blue Summer said:**
> Nope, nothing like that in my home folder but I know what you mean and it's not appearing as a device like my dvd drive and my partitions

Have a look in the /media folder when it's plugged in.

---

### Post by Blue Summer on 2011-02-21
> **philinux said:**
> Have a look in the /media folder when it's plugged in.

Nope.

It used to ocme up automatically but it's not appearing anywere at all now

---

### Post by philinux on 2011-02-21
> **Blue Summer said:**
> Nope.

It used to ocme up automatically but it's not appearing anywere at all now

To find out why look in /var/log/messages or system-admin-log file viewer for the messages log. 

Plug it in and then look for the systems messages.

Also check through this you may have altered a system setting accidentally.
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by Blue Summer on 2011-02-21
Heya, thanks for the help so far mate, appreciate it. This is taken from when I unplugged it to when I plugged it back in:

```
Feb 21 16:53:45 Rej3kt kernel: [14039.257340] usb 1-3: USB disconnect, address 6
Feb 21 16:54:08 Rej3kt kernel: [14062.176523] usb 1-3: new high speed USB device using ehci_hcd and address 7
Feb 21 16:54:08 Rej3kt kernel: [14062.309776] usb 1-3: configuration #1 chosen from 2 choices
Feb 21 16:54:08 Rej3kt kernel: [14062.310179] scsi7 : SCSI emulation for USB Mass Storage devices
Feb 21 16:54:13 Rej3kt kernel: [14067.310849] scsi 7:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Feb 21 16:54:13 Rej3kt kernel: [14067.311520] sd 7:0:0:0: Attached scsi generic sg4 type 0
Feb 21 16:54:13 Rej3kt kernel: [14067.317585] sd 7:0:0:0: [sdf] 1982464 2048-byte logical blocks: (4.06 GB/3.78 GiB)
Feb 21 16:54:13 Rej3kt kernel: [14067.318573] sd 7:0:0:0: [sdf] Write Protect is off
Feb 21 16:54:13 Rej3kt kernel: [14067.320591] sd 7:0:0:0: [sdf] 1982464 2048-byte logical blocks: (4.06 GB/3.78 GiB)
Feb 21 16:54:13 Rej3kt kernel: [14067.322492]  sdf: sdf1 sdf2
Feb 21 16:54:13 Rej3kt kernel: [14067.327237] sd 7:0:0:0: [sdf] 1982464 2048-byte logical blocks: (4.06 GB/3.78 GiB)
Feb 21 16:54:13 Rej3kt kernel: [14067.328454] sd 7:0:0:0: [sdf] Attached SCSI removable disk
Feb 21 16:54:13 Rej3kt kernel: [14068.001968] VFS: Can't find a valid FAT filesystem on dev sdf1.
```

Don't understand why it did work and now it doesn't though :/

---

### Post by philinux on 2011-02-21
This:-

```
4068.001968] VFS: Can't find a valid FAT filesystem on dev sdf1.
```

Did you unplug it without ejecting or safely remove?

With it plugged it goto system>admin>disk utility and see what it says about the device.

---

### Post by Blue Summer on 2011-02-21
Yeah I probably did that a fair few times, I'll try reformatting it. Thanks alot mate!!

---

### Post by philinux on 2011-02-21
> **Blue Summer said:**
> Yeah I probably did that a fair few times, I'll try reformatting it. Thanks alot mate!!

That will knacker it up I'm afraid. Get used to using safely remove.

;)

---

### Post by The Nutcrackin' Squirrel on 2011-02-21
Can I simply format it with FAT32?

---

### Post by philinux on 2011-02-21
> **The Nutcrackin' Squirrel said:**
> Can I simply format it with FAT32?

Yes you can or ntfs.

---

### Post by Keiran230 on 2011-02-21
Did you try mounting the drive manually? It's a more technical fix, but it might fix it without reformatting.

```
mkdir ~/Desktop/ipod
mount /dev/**XXX#** ~/Desktop/ipod
```
This will mount the iPod, but you need to know what the device file is. XXX# should be replaced with the device file corresponding to the partition, like /dev/sdb1
```
sudo fdisk -l| grep dev
```
This will list the device files for all partitions and drives the system sees. Use information from fdisk to find out which device to mount.

---


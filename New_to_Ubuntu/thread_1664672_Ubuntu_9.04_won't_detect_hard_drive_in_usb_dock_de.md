---
title: "Ubuntu 9.04 won't detect hard drive in usb dock device"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by servelan on 2011-01-11
Hello! I have an (what was an) external maxtor 500gig drive, which ubuntu wasn't detecting after a fresh install.. I bought a hard drive usb dock thingy for it thinking that would help..no joy. It is full of data so I want to recover it. The drive is spinning up okay.:confused:

---

### Post by servelan on 2011-01-12
sudo lshw -C disk shows this:

> 

 *-disk                  
       description: ATA Disk
       product: WDC WD20EARS-00J
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 80.0
       serial: WD-WCAYY0225163
       size: 1863GiB (2TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=c285161e-e858-4582-ad03-816c5816fd1b
  *-cdrom
       description: DVD-RAM writer
       product: DVDRRW GSA-H30L
       vendor: HL-DT-ST
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: S755
       serial: [HL-DT-STDVDRRW GSA-H30L S75506/12/26&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk:0
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
  *-disk:1
       description: SCSI Disk
       physical id: 0.0.1
       bus info: scsi@2:0.0.1
       logical name: /dev/sdc
  *-disk:2
       description: SCSI Disk
       physical id: 0.0.2
       bus info: scsi@2:0.0.2
       logical name: /dev/sdd
  *-disk:3
       description: SCSI Disk
       physical id: 0.0.3
       bus info: scsi@2:0.0.3
       logical name: /dev/sde
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdf
  *-disk UNCLAIMED
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0


---

### Post by Mark Phelps on 2011-01-12
IF it's a SATA drive/dock, can't help you.  

If it's a PATA drive/dock, I encountered a similar problem and had to keep experimenting with the jumper settings until Ubuntu finally saw the drive.

---

### Post by blind2314 on 2011-01-12
```
mount /dev/sdb /mnt
cd /mnt
ls -l
```
 
Do you see any of your data?

---

### Post by servelan on 2011-01-12
> **Mark Phelps said:**
> IF it's a SATA drive/dock, can't help you.  

If it's a PATA drive/dock, I encountered a similar problem and had to keep experimenting with the jumper settings until Ubuntu finally saw the drive.

It's an IDE drive, was an external drive and it stopped showing up so I took it out of the casing and docked it thinking that might help :/

---

### Post by servelan on 2011-01-12
> **blind2314 said:**
> ```
mount /dev/sdb /mnt
cd /mnt
ls -l
```Do you see any of your data?
> 
mount: /dev/sdb: unknown device
gehenna@malengine:~$ cd /mnt
gehenna@malengine:/mnt$ ls -l
total 12
drwxr-xr-x 2 root root 4096 2010-12-31 08:41 extdisk
drwxr-xr-x 2 root root 4096 2010-12-30 22:22 USB
drwxr-xr-x 2 root root 4096 2011-01-11 13:54 usbdrv


that's what comes up

dmesg shows:
> [ 1972.672584] sd 15:0:0:0: Attached scsi generic sg7 type 0
[ 2003.076106] usb 1-2.4: reset high speed USB device using ehci_hcd and address 18
[ 2013.184473] usb 1-2.4: device firmware changed
[ 2013.184654] sd 15:0:0:0: Device offlined - not ready after error recovery
[ 2013.184698] sd 15:0:0:0: rejecting I/O to offline device
[ 2013.184716] sd 15:0:0:0: rejecting I/O to offline device
[ 2013.184726] usb 1-2.4: USB disconnect, address 18
[ 2013.184733] sd 15:0:0:0: rejecting I/O to offline device
[ 2013.184745] sd 15:0:0:0: [sdg] READ CAPACITY failed
[ 2013.184749] sd 15:0:0:0: [sdg] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 2013.184755] sd 15:0:0:0: [sdg] Sense not available.
[ 2013.184764] sd 15:0:0:0: rejecting I/O to offline device
[ 2013.184772] sd 15:0:0:0: [sdg] Write Protect is off
[ 2013.184777] sd 15:0:0:0: [sdg] Mode Sense: 00 00 00 00
[ 2013.184781] sd 15:0:0:0: [sdg] Assuming drive cache: write through
[ 2013.184971] sd 15:0:0:0: [sdg] Attached SCSI disk
[ 2013.264123] usb 1-2.4: new high speed USB device using ehci_hcd and address 19
[ 2013.357117] usb 1-2.4: configuration #1 chosen from 1 choice
[ 2013.357744] scsi16 : SCSI emulation for USB Mass Storage devices
[ 2013.357916] usb-storage: device found at 19
[ 2013.357922] usb-storage: waiting for device to settle before scanning
[ 2028.356613] usb-storage: device scan complete
[ 2033.699565] scsi 16:0:0:0: Direct-Access     ST350063 0A                    PQ: 0 ANSI: 2 CCS
[ 2033.700336] sd 16:0:0:0: Attached scsi generic sg7 type 0
[ 2045.461114] sd 16:0:0:0: [sdg] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[ 2068.661135] sd 16:0:0:0: [sdg] Write Protect is off
[ 2068.661143] sd 16:0:0:0: [sdg] Mode Sense: 28 00 00 00
[ 2068.661148] sd 16:0:0:0: [sdg] Assuming drive cache: write through
[ 2068.662115] sd 16:0:0:0: [sdg] 976748592 512-byte logical blocks: (500 GB/465 GiB)
[ 2068.663042] sd 16:0:0:0: [sdg] Assuming drive cache: write through
[ 2068.663050] sdg: detected capacity change from 500107862016 to 500095279104
[ 2068.663056]  sdg: sdg1
[ 2068.723593] sdg: p1 size 976768002 exceeds device capacity, limited to end of disk
[ 2068.744271] sd 16:0:0:0: [sdg] Assuming drive cache: write through
[ 2068.744281] sd 16:0:0:0: [sdg] Attached SCSI disk

I've tried ddrescue and it just came up with "too many files" ..its a 500gig drive and I'm trying to rescue it to a 2TB drive thats got about 1600gig spare

---

### Post by blind2314 on 2011-01-12
Possibly a stupid question, but is there anything under the usbdrv directory that you showed under /mnt?

---

### Post by servelan on 2011-01-12
> **blind2314 said:**
> Possibly a stupid question, but is there anything under the usbdrv directory that you showed under /mnt?

nope.. and those three directories are all empty anyway :/

It comes up "disk unclaimed" with sudo lshw -C disk

---


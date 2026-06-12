---
title: "No USB or CDROM devices mounting"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by mykdeen on 2011-01-12
This is my second attempt at Lucid, and probably fifth attempt at Ubuntu over the years. Despite having some knowledge of Linux, this has boggled my mind for days:

After a fresh install of Lucid, all of my drives worked perfectly. (1) DVD-RW, (1) CD-RW, (8) Memory Card Reader (via USB), and my many USB drives were accessible from Places>Computer, but had horrible problems from my Netgear WG111v2 USB Wireless Card. I installed the Netgear drivers with ndiswrapper, rebooted, and wireless working like a charm...but now I don't have easy access to drives from Places>Computer! 

I've been drinking, smoking, and digging through forums and have had no luck in getting to my media. I can mount anything from the Terminal thanks to [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB) , but frankly it sucks. Here's what I'm working with...

lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 1058:071a Western Digital Technologies, Inc. 
Bus 001 Device 003: ID 0846:6a00 NetGear, Inc. WG111(v2) 54 Mbps Wireless [RealTek RTL8187L]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

sudo fdisk -l
[sudo] password for mike: 

Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e52ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19697   158210048   83  Linux
/dev/sda2           19697       20024     2623489    5  Extended
/dev/sda5           19697       20024     2623488   82  Linux swap / Solaris

Disk /dev/sdf: 500.1 GB, 500079525888 bytes
223 heads, 33 sectors/track, 132724 cylinders
Units = cylinders of 7359 * 512 = 3767808 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000320d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      132725   488357888    7  HPFS/NTFS


DISCOVERY:
I unplugged my external HD (/dev/sdf), waited, plugged back in, then ran dmesg in Terminal. I'm not sure what I'm staring at, but the tail-end of the log shows:

[  588.956054] scsi 7:0:0:0: Direct-Access     WD       My Passport 071A 2011 PQ: 0 ANSI: 4
[  589.004040] scsi 7:0:0:1: Enclosure         WD       SES Device       2011 PQ: 0 ANSI: 4
[  589.006324] sd 7:0:0:0: Attached scsi generic sg7 type 0
[  589.006976] scsi 7:0:0:1: Attached scsi generic sg8 type 13
[  589.080062] sd 7:0:0:0: [sdf] 976717824 512-byte logical blocks: (500 GB/465 GiB)
[  589.132037] sd 7:0:0:0: [sdf] Write Protect is off
[  589.132042] sd 7:0:0:0: [sdf] Mode Sense: 2b 00 10 08
[  589.132045] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[  589.292023] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[  589.292028]  sdf: sdf1
[  589.620071] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[  589.620078] sd 7:0:0:0: [sdf] Attached SCSI disk
[  591.216051] ses 7:0:0:1: Attached Enclosure device
[ 2725.924243] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 2741.020284] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 3095.096317] ndiswrapper (iw_set_auth:1602): invalid cmd 12

Are those last three lines a clue?

---


---
title: "Slow File Operations (Read/Write) and slow Network"
date: 2013-11-18
forum: Networking &amp; Wireless
---

### Post by sondo2121 on 2013-11-18
I'm not sure what is causing this new problem yet so I figured I'd post it here to see if anybody else is having the same problem.  I have not experienced these problems before, this is a new and recent occurrence which started within the last week or so.

All of a sudden I am getting slow transfers and reads to/from my ubuntu box.  File operations are going around 600-700 k/s when they previously were going 30+ Mb/s.

Here are some things I am now experiencing (didn't before):
[LIST]
[*]Slow network file transfers (local and remote) with samba or SFTP
[*]Slow browsing of my samba share on my windows box, slow directory refresh times
[*]PS3 Mediaserver is lagging and the video is glitching (if it would actually play)
[/LIST]


[SIZE=3]Is anybody else seeing these same symptoms as I am????  Maybe a recent update or kernel update has caused this to happen??  Again, these problems didn't start happening until this past week.
[/SIZE]

I am running Ubuntu 12.04 LTS:

```
xxxx@xxxx:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:        12.04
Codename:       precise
```

RAID-6 Array is in normal operation:

```
xxxx@xxxx:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Sat Jun  8 00:10:38 2013
     Raid Level : raid6
     Array Size : 17580801024 (16766.36 GiB 18002.74 GB)
  Used Dev Size : 2930133504 (2794.39 GiB 3000.46 GB)
   Raid Devices : 8
  Total Devices : 8
    Persistence : Superblock is persistent

    Update Time : Mon Nov 18 07:41:07 2013
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : xxxx:0  (local to host xxxx)
           UUID : e102e4b7:a00d0615:1cb38620:3cfad34a
         Events : 85

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1
       5       8       97        5      active sync   /dev/sdg1
       6       8      113        6      active sync   /dev/sdh1
       7       8      129        7      active sync   /dev/sdi1
```

---

### Post by SaturnusDJ on 2013-11-18
For all drives:
```
smartctl -a /dev/sda
```

A disk might be dying.


Did you test the speed locally?

---

### Post by sondo2121 on 2013-11-18
I have not had the chance to test locally, but that was on my list to try tonight.  Will do that and report back.

Full SMART Report from all 9 disks are linked below.  Doesn't look like that anything is starting to fail.  Do you notice anything SaturnusDJ?

/dev/sda : [http://pastebin.com/D5zAJZ1R](http://pastebin.com/D5zAJZ1R) (root drive ; SSD)
/dev/sdb : [http://pastebin.com/fDeXsYFt](http://pastebin.com/fDeXsYFt)
/dev/sdc : [http://pastebin.com/n9pKuaTg](http://pastebin.com/n9pKuaTg)
/dev/sdd : [http://pastebin.com/iwNrt3J7](http://pastebin.com/iwNrt3J7)
/dev/sde : [http://pastebin.com/qBwUNtFi](http://pastebin.com/qBwUNtFi)
/dev/sdf : [http://pastebin.com/FvFqHfmk](http://pastebin.com/FvFqHfmk)
/dev/sdg : [http://pastebin.com/3ExZXkbs](http://pastebin.com/3ExZXkbs)
/dev/sdh : [http://pastebin.com/NxRjy7GC](http://pastebin.com/NxRjy7GC)
/dev/sdi : [http://pastebin.com/4F1TzqS0](http://pastebin.com/4F1TzqS0)

---

### Post by SaturnusDJ on 2013-11-18
Looks fine to me.

---

### Post by sondo2121 on 2013-11-18
Ok, I have determined that the transfers locally to and from my RAID array or my root drive are not having issues.  50-75 mb/s (normal speed) is what I'm seeing.

SERVER --> CLIENT is slow (25-150 kb/s)
CLIENT   --> SERVER is NOT slow 50-75 mb/s (normal speed)

Still investigating but I'm guessing a recent update broke this as I have not touched this file server except updates.

EDIT:

Below are the results of the iperf tests I ran:

[B]Server to Client (Win 7) - 321 _K_bits/sec
Client (Win 7) to Server - 358 _M_bits/sec[/B]

**sudo lshw -C network:**

```
xxxx@xxxx:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: **eth0**
       version: 00
       serial: 60:a4:xx:xx:xx:x5
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k duplex=full firmware=2.1-3 ip=192.168.1.200 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:17 memory:f7d00000-f7d1ffff ioport:d000(size=32) memory:f7d20000-f7d23fff
```

**sudo modinfo e1000e:**

```
xxxxx@xxxxx:~$ sudo modinfo e1000e
filename:       /lib/modules/3.5.0-43-generic/kernel/drivers/net/ethernet/intel/e1000e/e1000e.ko
version:        2.0.0-k
license:        GPL
description:    Intel(R) PRO/1000 Network Driver
author:         Intel Corporation, <linux.nics@intel.com>
srcversion:     8BE4A65E2266A2193761AAA
alias:          pci:v00008086d00001559sv*sd*bc*sc*i*
alias:          pci:v00008086d0000155Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000153Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000153Asv*sd*bc*sc*i*
alias:          pci:v00008086d00001503sv*sd*bc*sc*i*
alias:          pci:v00008086d00001502sv*sd*bc*sc*i*
alias:          pci:v00008086d000010F0sv*sd*bc*sc*i*
alias:          pci:v00008086d000010EFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010EBsv*sd*bc*sc*i*
alias:          pci:v00008086d000010EAsv*sd*bc*sc*i*
alias:          pci:v00008086d00001525sv*sd*bc*sc*i*
alias:          pci:v00008086d000010DFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010DEsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CEsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CDsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CCsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CBsv*sd*bc*sc*i*
alias:          pci:v00008086d000010F5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010E5sv*sd*bc*sc*i*
alias:          pci:v00008086d0000294Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010BDsv*sd*bc*sc*i*
alias:          pci:v00008086d000010C3sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C2sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C0sv*sd*bc*sc*i*
alias:          pci:v00008086d00001501sv*sd*bc*sc*i*
alias:          pci:v00008086d00001049sv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Asv*sd*bc*sc*i*
alias:          pci:v00008086d000010C4sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C5sv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010BBsv*sd*bc*sc*i*
alias:          pci:v00008086d00001098sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BAsv*sd*bc*sc*i*
alias:          pci:v00008086d00001096sv*sd*bc*sc*i*
alias:          pci:v00008086d0000150Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010F6sv*sd*bc*sc*i*
alias:          pci:v00008086d000010D3sv*sd*bc*sc*i*
alias:          pci:v00008086d0000109Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000108Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000108Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Dsv*sd*bc*sc*i*
alias:          pci:v00008086d000010B9sv*sd*bc*sc*i*
alias:          pci:v00008086d000010D5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010DAsv*sd*bc*sc*i*
alias:          pci:v00008086d000010D9sv*sd*bc*sc*i*
alias:          pci:v00008086d00001060sv*sd*bc*sc*i*
alias:          pci:v00008086d000010A5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BCsv*sd*bc*sc*i*
alias:          pci:v00008086d000010A4sv*sd*bc*sc*i*
alias:          pci:v00008086d0000105Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000105Esv*sd*bc*sc*i*
depends:
intree:         Y
vermagic:       3.5.0-43-generic SMP mod_unload modversions
parm:           debug:Debug level (0=none,...,16=all) (int)
parm:           eeprom_bad_csum_allow:Allow bad EEPROM checksums (int)
parm:           copybreak:Maximum size of packet that is copied to a new buffer on receive (uint)
parm:           TxIntDelay:Transmit Interrupt Delay (array of int)
parm:           TxAbsIntDelay:Transmit Absolute Interrupt Delay (array of int)
parm:           RxIntDelay:Receive Interrupt Delay (array of int)
parm:           RxAbsIntDelay:Receive Absolute Interrupt Delay (array of int)
parm:           InterruptThrottleRate:Interrupt Throttling Rate (array of int)
parm:           IntMode:Interrupt Mode (array of int)
parm:           SmartPowerDownEnable:Enable PHY smart power down (array of int)
parm:           KumeranLockLoss:Enable Kumeran lock loss workaround (array of int)
parm:           WriteProtectNVM:Write-protect NVM [WARNING: disabling this can lead to corrupted NVM] (array of int)
parm:           CrcStripping:Enable CRC Stripping, disable if your BMC needs the CRC (array of int)

```

---


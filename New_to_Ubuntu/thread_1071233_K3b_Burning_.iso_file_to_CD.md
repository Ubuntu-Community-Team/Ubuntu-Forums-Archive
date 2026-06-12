---
title: "K3b Burning .iso file to CD"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by hifly1231 on 2009-02-15
I tried burning an .iso file to CD using K3b, and I got this error.  Did I do something wrong?

System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.27-11-generic
Devices
-----------------------
CyberDrv CW058D CD-R/RW 15HD (/dev/scd0, ) [CD-R, CD-RW, CD-ROM] [CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

Used versions
-----------------------
cdrecord: 1.1.8

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.8
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=32 -dao driveropts=burnfree -eject -data -tsize=320113s -

---

### Post by SunnyRabbiera on 2009-02-15
Unsure from that post, but try a slower speed.

---

### Post by hifly1231 on 2009-02-16
OK, it's telling me:

No CD/DVD writer found.
K3b did not find an optical writing device in your system. Thus, you will not be able to burn CDs or DVDs. However, you can still use other K3b features like audio track extraction or audio transcoding or ISO9660 image creation.

How do I fix this?

---

### Post by SunnyRabbiera on 2009-02-16
thart is strange, did you try brasero?
Brasero is alright and will do the same basic job.

---

### Post by cariboo on 2009-02-16
Start k3b and go to Settings-->Configure K3b-->Devices, and make sure your drive is detected properly.

Jim

---

### Post by hifly1231 on 2009-02-16
OK, it's detected the CD writing device, and now it's telling me:

Cdrecord has no permission to open the device.

---

### Post by SunnyRabbiera on 2009-02-16
again I suggest try brasero

---

### Post by mc4man on 2009-02-16
> Warning: Cannot raise RLIMIT_MEMLOCK limits

That's basically saying it's unable to set needed buffer size for who knows what reason (unable to reserve memory for exclusive access (system and or device buffer

What I forgot to mention is that error in conjunction with a dma error *sometimes* is due to not having an 80 wire ide cable
```

grep 'UDMA' /var/log/dmesg
```
or
```
grep 'UDMA' /var/log/kern.log
```

---

### Post by hifly1231 on 2009-02-16
> **SunnyRabbiera said:**
> again I suggest try brasero

I tried Brasero, K3b, Gnomebaker, all with the same results.  I even tried just burning a song to CD, and that didn't work either.  There must be something wrong in my settings somewhere.  I know that my computer is capable of doing this, because when I (God forbid) was still using Windows XP last summer, I burned many, many songs to CD through Windows Media Player.  I've figured out how to work just about everything else since I've started using Ubuntu, and this is the only thing I can think of right now that I can't get working.

---

### Post by hifly1231 on 2009-02-16
Does anybody have any ideas as to how I can get one of my CD burners to work?

---

### Post by hifly1231 on 2009-02-16
Just to let everyone know, apparently the problem is with Intrepid Ibex.  No CD's would burn in Intrepid Ibex, but I downloaded DeepBurner for Windows in WINE, and now I'm able to burn CD's.  I hope they correct this problem with Jaunty Jackaloupe.  I don't like having any more programs in WINE than I have to.

---

### Post by TransitMan on 2009-02-17
I am using Intrepid and have used K3B without issue. 
While the latest Intrepid version is using KDE 4.x.x, K3B is at version 1.05 under KDE 3.5.10.
Also, with you having issues with all the burning apps under *buntu, but yet can burn under WINE, it seems that a package or library is missing for you to successfully burn in *buntu.
If you could follow the suggestions from above in regards to ```
grep 'UDMA' /var/log/dmesg
``` and ```
grep 'UDMA' /var/log/kern.log
``` we might be able to better help you get the *buntu burning programs running, thereby eliminating DeepBurner in WINE.

---

### Post by hifly1231 on 2009-02-17
> **TransitMan said:**
> I am using Intrepid and have used K3B without issue. 
While the latest Intrepid version is using KDE 4.x.x, K3B is at version 1.05 under KDE 3.5.10.
Also, with you having issues with all the burning apps under *buntu, but yet can burn under WINE, it seems that a package or library is missing for you to successfully burn in *buntu.
If you could follow the suggestions from above in regards to ```
grep 'UDMA' /var/log/dmesg
``` and ```
grep 'UDMA' /var/log/kern.log
``` we might be able to better help you get the *buntu burning programs running, thereby eliminating DeepBurner in WINE.

If you could tell me exactly what to do, I would GREATLY appreciate it.  I really like K3b, and would LOVE to use it instead of having a Windows program on my Ubuntu!!!  Do you want me to run those commands in Terminal and tell you what they say, or what?  Thanks a lot for your response!!!

---

### Post by TransitMan on 2009-02-17
Yes, run those comands from a console window and then post the results here.

---

### Post by hifly1231 on 2009-02-17
***OK.  I've uninstalled DeepBurner from WINE, and reinstalled K3b.  First of all, here's the debugging report:***

System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.27-11-generic
Devices
-----------------------
CyberDrv CW058D CD-R/RW 15HD (/dev/scd0, ) [CD-R, CD-RW, CD-ROM] [CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

K3bIsoImager
-----------------------
mkisofs print size result: 2527 (5175296 bytes)
Pipe throughput: 126976 bytes read, 114432 bytes written.

Used versions
-----------------------
mkisofs: 1.1.8
cdrecord: 1.1.8

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.8
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'CyberDrv'
Identification : 'CW058D CD-R/RW  '
Revision       : '15HD'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009 (CD-R)
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1806336 = 1764 KB
FIFO size      : 12582912 = 12288 KB
Errno: 5 (Input/output error), read buffer scsi sendcmd: no error
CDB:  3C 00 00 00 00 00 00 FC 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 02 00 00
Sense Key: 0x0 No Additional Sense, Segment 11
Sense Code: 0x00 Qual 0x02 (end-of-partition/medium detected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 110.130s timeout 40s
/usr/bin/wodim: Cannot load media.
/usr/bin/wodim: Cannot eject media.
Track 01: data     4 MB        
Total size:        5 MB (00:33.72) = 2529 sectors
Lout start:        6 MB (00:35/54) = 2529 sectors

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=32 -tao driveropts=burnfree -eject -multi -xa -tsize=2527s - 

mkisofs
-----------------------
2527
I: -input-charset not specified, using utf-8 (detected in locale settings)

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid Michel Camilo - Miami Afternoon -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-hifly1231/k3bXmHBba.tmp -rational-rock -hide-list /tmp/kde-hifly1231/k3bWqelub.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-hifly1231/k3bWnOtZa.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-hifly1231/k3beSW0aa.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid Michel Camilo - Miami Afternoon -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-hifly1231/k3bIlaQOa.tmp -rational-rock -hide-list /tmp/kde-hifly1231/k3baBQg3a.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-hifly1231/k3bP8c3na.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-hifly1231/k3be6kdpc.tmp 

[B][I]Now, here's what I get when I run the suggested commands in Terminal:
[/I][/B]
hifly1231@hifly1231-desktop:~$ **grep 'UDMA' /var/log/dmesg**

[    3.906528] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
[    3.906533] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
[    4.069394] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
[    4.085212] ata1.00: configured for UDMA/100
[    4.248752] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
[    4.264382] ata2.00: configured for UDMA/33

hifly1231@hifly1231-desktop:~$ **grep 'UDMA' /var/log/kern.log**

Feb 14 02:38:39 hifly1231-desktop kernel: [    4.022379] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 14 02:38:39 hifly1231-desktop kernel: [    4.022384] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 14 02:38:39 hifly1231-desktop kernel: [    4.185402] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 14 02:38:39 hifly1231-desktop kernel: [    4.201264] ata1.00: configured for UDMA/100
Feb 14 02:38:39 hifly1231-desktop kernel: [    4.364548] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 14 02:38:39 hifly1231-desktop kernel: [    4.380820] ata2.00: configured for UDMA/33
Feb 14 02:41:43 hifly1231-desktop kernel: [    4.018049] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 14 02:41:43 hifly1231-desktop kernel: [    4.018054] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 14 02:41:43 hifly1231-desktop kernel: [    4.181426] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 14 02:41:43 hifly1231-desktop kernel: [    4.197224] ata1.00: configured for UDMA/100
Feb 14 02:41:43 hifly1231-desktop kernel: [    4.360490] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 14 02:41:43 hifly1231-desktop kernel: [    4.376307] ata2.00: configured for UDMA/33
Feb 14 02:47:06 hifly1231-desktop kernel: [    4.018334] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 14 02:47:06 hifly1231-desktop kernel: [    4.018339] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 14 02:47:06 hifly1231-desktop kernel: [    4.181430] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 14 02:47:06 hifly1231-desktop kernel: [    4.198105] ata1.00: configured for UDMA/100
Feb 14 02:47:06 hifly1231-desktop kernel: [    4.360449] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 14 02:47:06 hifly1231-desktop kernel: [    4.376302] ata2.00: configured for UDMA/33
Feb 14 03:23:42 hifly1231-desktop kernel: [    4.002090] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 14 03:23:42 hifly1231-desktop kernel: [    4.002095] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 14 03:23:42 hifly1231-desktop kernel: [    4.165359] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 14 03:23:42 hifly1231-desktop kernel: [    4.181275] ata1.00: configured for UDMA/100
Feb 14 03:23:42 hifly1231-desktop kernel: [    4.344521] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 14 03:23:42 hifly1231-desktop kernel: [    4.360370] ata2.00: configured for UDMA/33
Feb 14 03:31:11 hifly1231-desktop kernel: [    4.006836] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 14 03:31:11 hifly1231-desktop kernel: [    4.006841] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 14 03:31:11 hifly1231-desktop kernel: [    4.169431] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 14 03:31:11 hifly1231-desktop kernel: [    4.185263] ata1.00: configured for UDMA/100
Feb 14 03:31:11 hifly1231-desktop kernel: [    4.348449] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 14 03:31:11 hifly1231-desktop kernel: [    4.364366] ata2.00: configured for UDMA/33
Feb 14 07:14:32 hifly1231-desktop kernel: [    4.018100] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 14 07:14:32 hifly1231-desktop kernel: [    4.018105] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 14 07:14:32 hifly1231-desktop kernel: [    4.181392] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 14 07:14:32 hifly1231-desktop kernel: [    4.197233] ata1.00: configured for UDMA/100
Feb 14 07:14:32 hifly1231-desktop kernel: [    4.360470] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 14 07:14:32 hifly1231-desktop kernel: [    4.376307] ata2.00: configured for UDMA/33
Feb 14 11:26:10 hifly1231-desktop kernel: [    4.006095] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 14 11:26:10 hifly1231-desktop kernel: [    4.006100] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 14 11:26:10 hifly1231-desktop kernel: [    4.169367] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 14 11:26:10 hifly1231-desktop kernel: [    4.185250] ata1.00: configured for UDMA/100
Feb 14 11:26:10 hifly1231-desktop kernel: [    4.348523] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 14 11:26:10 hifly1231-desktop kernel: [    4.364339] ata2.00: configured for UDMA/33
Feb 14 12:46:00 hifly1231-desktop kernel: [    4.010100] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 14 12:46:00 hifly1231-desktop kernel: [    4.010105] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 14 12:46:00 hifly1231-desktop kernel: [    4.173388] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 14 12:46:00 hifly1231-desktop kernel: [    4.189256] ata1.00: configured for UDMA/100
Feb 14 12:46:00 hifly1231-desktop kernel: [    4.352481] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 14 12:46:00 hifly1231-desktop kernel: [    4.368372] ata2.00: configured for UDMA/33
Feb 14 20:12:42 hifly1231-desktop kernel: [    4.006845] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 14 20:12:42 hifly1231-desktop kernel: [    4.006850] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 14 20:12:42 hifly1231-desktop kernel: [    4.169458] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 14 20:12:42 hifly1231-desktop kernel: [    4.185278] ata1.00: configured for UDMA/100
Feb 14 20:12:42 hifly1231-desktop kernel: [    4.348489] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 14 20:12:42 hifly1231-desktop kernel: [    4.364378] ata2.00: configured for UDMA/33
Feb 15 01:56:54 hifly1231-desktop kernel: [    3.922522] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 15 01:56:54 hifly1231-desktop kernel: [    3.922527] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 15 01:56:54 hifly1231-desktop kernel: [    4.085404] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 15 01:56:54 hifly1231-desktop kernel: [    4.101276] ata1.00: configured for UDMA/100
Feb 15 01:56:54 hifly1231-desktop kernel: [    4.264522] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 15 01:56:54 hifly1231-desktop kernel: [    4.280377] ata2.00: configured for UDMA/33
Feb 15 02:01:58 hifly1231-desktop kernel: [    3.906018] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 15 02:01:58 hifly1231-desktop kernel: [    3.906023] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 15 02:01:58 hifly1231-desktop kernel: [    4.069392] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 15 02:01:58 hifly1231-desktop kernel: [    4.077245] ata1.00: configured for UDMA/100
Feb 15 02:01:58 hifly1231-desktop kernel: [    4.240485] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 15 02:01:58 hifly1231-desktop kernel: [    4.256386] ata2.00: configured for UDMA/33
Feb 15 02:35:27 hifly1231-desktop kernel: [    3.934012] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 15 02:35:27 hifly1231-desktop kernel: [    3.934017] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 15 02:35:27 hifly1231-desktop kernel: [    4.097446] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 15 02:35:27 hifly1231-desktop kernel: [    4.113258] ata1.00: configured for UDMA/100
Feb 15 02:35:27 hifly1231-desktop kernel: [    4.276524] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 15 02:35:27 hifly1231-desktop kernel: [    4.292402] ata2.00: configured for UDMA/33
Feb 15 02:42:50 hifly1231-desktop kernel: [    3.935497] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 15 02:42:50 hifly1231-desktop kernel: [    3.935502] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 15 02:42:50 hifly1231-desktop kernel: [    4.097460] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 15 02:42:50 hifly1231-desktop kernel: [    4.113267] ata1.00: configured for UDMA/100
Feb 15 02:42:50 hifly1231-desktop kernel: [    4.276517] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 15 02:42:50 hifly1231-desktop kernel: [    4.292495] ata2.00: configured for UDMA/33
Feb 15 13:40:42 hifly1231-desktop kernel: [    3.886497] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 15 13:40:42 hifly1231-desktop kernel: [    3.886502] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 15 13:40:42 hifly1231-desktop kernel: [    4.049410] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 15 13:40:42 hifly1231-desktop kernel: [    4.065253] ata1.00: configured for UDMA/100
Feb 15 13:40:42 hifly1231-desktop kernel: [    4.228503] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 15 13:40:42 hifly1231-desktop kernel: [    4.244364] ata2.00: configured for UDMA/33
Feb 15 18:35:18 hifly1231-desktop kernel: [    3.922009] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 15 18:35:18 hifly1231-desktop kernel: [    3.922014] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 15 18:35:18 hifly1231-desktop kernel: [    4.085409] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 15 18:35:18 hifly1231-desktop kernel: [    4.101252] ata1.00: configured for UDMA/100
Feb 15 18:35:18 hifly1231-desktop kernel: [    4.264446] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 15 18:35:18 hifly1231-desktop kernel: [    4.280860] ata2.00: configured for UDMA/33
Feb 15 19:55:50 hifly1231-desktop kernel: [    3.926811] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 15 19:55:50 hifly1231-desktop kernel: [    3.926816] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 15 19:55:50 hifly1231-desktop kernel: [    4.089354] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 15 19:55:50 hifly1231-desktop kernel: [    4.105411] ata1.00: configured for UDMA/100
Feb 15 19:55:50 hifly1231-desktop kernel: [    4.268559] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 15 19:55:50 hifly1231-desktop kernel: [    4.284387] ata2.00: configured for UDMA/33
Feb 15 23:20:15 hifly1231-desktop kernel: [    3.893971] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 15 23:20:15 hifly1231-desktop kernel: [    3.893976] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 15 23:20:15 hifly1231-desktop kernel: [    4.057377] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 15 23:20:15 hifly1231-desktop kernel: [    4.073579] ata1.00: configured for UDMA/100
Feb 15 23:20:15 hifly1231-desktop kernel: [    4.236517] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 15 23:20:15 hifly1231-desktop kernel: [    4.252405] ata2.00: configured for UDMA/33
Feb 15 23:34:50 hifly1231-desktop kernel: [    4.010056] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 15 23:34:50 hifly1231-desktop kernel: [    4.010061] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 15 23:34:50 hifly1231-desktop kernel: [    4.173409] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 15 23:34:50 hifly1231-desktop kernel: [    4.189270] ata1.00: configured for UDMA/100
Feb 15 23:34:50 hifly1231-desktop kernel: [    4.352456] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 15 23:34:50 hifly1231-desktop kernel: [    4.368323] ata2.00: configured for UDMA/33
Feb 15 23:51:03 hifly1231-desktop kernel: [    4.013944] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 15 23:51:03 hifly1231-desktop kernel: [    4.013949] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 15 23:51:03 hifly1231-desktop kernel: [    4.177434] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 15 23:51:03 hifly1231-desktop kernel: [    4.193305] ata1.00: configured for UDMA/100
Feb 15 23:51:03 hifly1231-desktop kernel: [    4.356494] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 15 23:51:03 hifly1231-desktop kernel: [    4.372361] ata2.00: configured for UDMA/33
Feb 16 01:01:39 hifly1231-desktop kernel: [    4.026097] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 16 01:01:39 hifly1231-desktop kernel: [    4.026102] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 16 01:01:39 hifly1231-desktop kernel: [    4.189380] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 16 01:01:39 hifly1231-desktop kernel: [    4.205238] ata1.00: configured for UDMA/100
Feb 16 01:01:39 hifly1231-desktop kernel: [    4.368500] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 16 01:01:39 hifly1231-desktop kernel: [    4.384309] ata2.00: configured for UDMA/33
Feb 16 01:15:20 hifly1231-desktop kernel: [    3.998089] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 16 01:15:20 hifly1231-desktop kernel: [    3.998093] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 16 01:15:20 hifly1231-desktop kernel: [    4.161395] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 16 01:15:20 hifly1231-desktop kernel: [    4.177261] ata1.00: configured for UDMA/100
Feb 16 01:15:20 hifly1231-desktop kernel: [    4.340520] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 16 01:15:20 hifly1231-desktop kernel: [    4.356365] ata2.00: configured for UDMA/33
Feb 16 01:25:04 hifly1231-desktop kernel: [    3.890475] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 16 01:25:04 hifly1231-desktop kernel: [    3.890479] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 16 01:25:04 hifly1231-desktop kernel: [    4.053396] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 16 01:25:04 hifly1231-desktop kernel: [    4.069295] ata1.00: configured for UDMA/100
Feb 16 01:25:04 hifly1231-desktop kernel: [    4.232536] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 16 01:25:04 hifly1231-desktop kernel: [    4.248357] ata2.00: configured for UDMA/33
Feb 16 01:32:06 hifly1231-desktop kernel: [    4.006024] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 16 01:32:06 hifly1231-desktop kernel: [    4.006029] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 16 01:32:06 hifly1231-desktop kernel: [    4.169450] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 16 01:32:06 hifly1231-desktop kernel: [    4.185282] ata1.00: configured for UDMA/100
Feb 16 01:32:06 hifly1231-desktop kernel: [    4.348491] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 16 01:32:06 hifly1231-desktop kernel: [    4.364369] ata2.00: configured for UDMA/33
Feb 16 03:47:13 hifly1231-desktop kernel: [    4.019065] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 16 03:47:13 hifly1231-desktop kernel: [    4.019070] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 16 03:47:13 hifly1231-desktop kernel: [    4.181452] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 16 03:47:13 hifly1231-desktop kernel: [    4.197285] ata1.00: configured for UDMA/100
Feb 16 03:47:13 hifly1231-desktop kernel: [    4.360513] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 16 03:47:13 hifly1231-desktop kernel: [    4.376419] ata2.00: configured for UDMA/33
Feb 16 03:52:46 hifly1231-desktop kernel: [    4.007187] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 16 03:52:46 hifly1231-desktop kernel: [    4.007192] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 16 03:52:46 hifly1231-desktop kernel: [    4.169402] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 16 03:52:46 hifly1231-desktop kernel: [    4.185229] ata1.00: configured for UDMA/100
Feb 16 03:52:46 hifly1231-desktop kernel: [    4.348515] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 16 03:52:46 hifly1231-desktop kernel: [    4.364338] ata2.00: configured for UDMA/33
Feb 16 04:04:50 hifly1231-desktop kernel: [    4.018035] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 16 04:04:50 hifly1231-desktop kernel: [    4.018040] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 16 04:04:50 hifly1231-desktop kernel: [    4.181406] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 16 04:04:50 hifly1231-desktop kernel: [    4.197264] ata1.00: configured for UDMA/100
Feb 16 04:04:50 hifly1231-desktop kernel: [    4.360582] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 16 04:04:50 hifly1231-desktop kernel: [    4.376798] ata2.00: configured for UDMA/33
Feb 16 15:21:43 hifly1231-desktop kernel: [    4.014245] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 16 15:21:43 hifly1231-desktop kernel: [    4.014250] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 16 15:21:43 hifly1231-desktop kernel: [    4.177388] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 16 15:21:43 hifly1231-desktop kernel: [    4.193275] ata1.00: configured for UDMA/100
Feb 16 15:21:43 hifly1231-desktop kernel: [    4.356460] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 16 15:21:43 hifly1231-desktop kernel: [    4.372323] ata2.00: configured for UDMA/33
Feb 16 23:08:55 hifly1231-desktop kernel: [    4.023274] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 16 23:08:55 hifly1231-desktop kernel: [    4.023279] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 16 23:08:55 hifly1231-desktop kernel: [    4.185368] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 16 23:08:55 hifly1231-desktop kernel: [    4.201280] ata1.00: configured for UDMA/100
Feb 16 23:08:55 hifly1231-desktop kernel: [    4.364479] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 16 23:08:55 hifly1231-desktop kernel: [    4.380303] ata2.00: configured for UDMA/33
Feb 16 23:18:01 hifly1231-desktop kernel: [    3.925977] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 16 23:18:01 hifly1231-desktop kernel: [    3.925982] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 16 23:18:01 hifly1231-desktop kernel: [    4.089445] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 16 23:18:01 hifly1231-desktop kernel: [    4.105306] ata1.00: configured for UDMA/100
Feb 16 23:18:01 hifly1231-desktop kernel: [    4.268501] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 16 23:18:01 hifly1231-desktop kernel: [    4.284957] ata2.00: configured for UDMA/33
Feb 16 23:27:00 hifly1231-desktop kernel: [    3.922170] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 16 23:27:00 hifly1231-desktop kernel: [    3.922175] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 16 23:27:00 hifly1231-desktop kernel: [    4.085416] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 16 23:27:00 hifly1231-desktop kernel: [    4.101246] ata1.00: configured for UDMA/100
Feb 16 23:27:00 hifly1231-desktop kernel: [    4.264519] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 16 23:27:00 hifly1231-desktop kernel: [    4.280388] ata2.00: configured for UDMA/33
Feb 17 00:10:32 hifly1231-desktop kernel: [    3.934021] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 17 00:10:32 hifly1231-desktop kernel: [    3.934026] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 17 00:10:32 hifly1231-desktop kernel: [    4.097459] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 17 00:10:32 hifly1231-desktop kernel: [    4.113291] ata1.00: configured for UDMA/100
Feb 17 00:10:32 hifly1231-desktop kernel: [    4.276530] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 17 00:10:32 hifly1231-desktop kernel: [    4.292376] ata2.00: configured for UDMA/33
Feb 17 00:27:14 hifly1231-desktop kernel: [    3.999019] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 17 00:27:14 hifly1231-desktop kernel: [    3.999024] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 17 00:27:14 hifly1231-desktop kernel: [    4.161388] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 17 00:27:14 hifly1231-desktop kernel: [    4.177243] ata1.00: configured for UDMA/100
Feb 17 00:27:14 hifly1231-desktop kernel: [    4.340537] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 17 00:27:14 hifly1231-desktop kernel: [    4.356381] ata2.00: configured for UDMA/33
Feb 17 01:58:11 hifly1231-desktop kernel: [    3.939010] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 17 01:58:11 hifly1231-desktop kernel: [    3.939015] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 17 01:58:11 hifly1231-desktop kernel: [    4.101365] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 17 01:58:11 hifly1231-desktop kernel: [    4.117221] ata1.00: configured for UDMA/100
Feb 17 01:58:11 hifly1231-desktop kernel: [    4.280471] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 17 01:58:11 hifly1231-desktop kernel: [    4.296315] ata2.00: configured for UDMA/33
Feb 17 09:37:20 hifly1231-desktop kernel: [    3.929759] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 17 09:37:20 hifly1231-desktop kernel: [    3.929763] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 17 09:37:20 hifly1231-desktop kernel: [    4.093432] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 17 09:37:20 hifly1231-desktop kernel: [    4.109296] ata1.00: configured for UDMA/100
Feb 17 09:37:20 hifly1231-desktop kernel: [    4.272502] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 17 09:37:20 hifly1231-desktop kernel: [    4.288353] ata2.00: configured for UDMA/33
Feb 17 13:30:37 hifly1231-desktop kernel: [    3.902021] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 17 13:30:37 hifly1231-desktop kernel: [    3.902026] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 17 13:30:37 hifly1231-desktop kernel: [    4.065408] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 17 13:30:37 hifly1231-desktop kernel: [    4.081437] ata1.00: configured for UDMA/100
Feb 17 13:30:37 hifly1231-desktop kernel: [    4.244505] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 17 13:30:37 hifly1231-desktop kernel: [    4.260376] ata2.00: configured for UDMA/33
Feb 17 13:39:22 hifly1231-desktop kernel: [    3.906528] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Feb 17 13:39:22 hifly1231-desktop kernel: [    3.906533] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Feb 17 13:39:22 hifly1231-desktop kernel: [    4.069394] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Feb 17 13:39:22 hifly1231-desktop kernel: [    4.085212] ata1.00: configured for UDMA/100
Feb 17 13:39:22 hifly1231-desktop kernel: [    4.248752] ata2.00: ATAPI: CW058D ATAPI CD-R/RW, V15HD, max UDMA/33
Feb 17 13:39:22 hifly1231-desktop kernel: [    4.264382] ata2.00: configured for UDMA/33

---

### Post by TransitMan on 2009-02-18
OK, from what I am seeing so far is that the CD burner is being seen.

Now run this from Terminal
```
gksudo gedit /etc/fstab
```
and post the results here.

---

### Post by philinux on 2009-02-18
Post the output of

```
cat /etc/fstab
```

---

### Post by hifly1231 on 2009-02-18
OK, here are the results:

***gksudo gedit /etc/fstab***

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0ed93493-8777-4023-a1a0-9b79ca09623d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d31c1199-4d63-43f9-83d4-e43c258f3d9a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

***cat /etc/fstab***

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0ed93493-8777-4023-a1a0-9b79ca09623d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d31c1199-4d63-43f9-83d4-e43c258f3d9a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by TransitMan on 2009-02-18
OK. The CD drive is being seen.
I have compared some of your information to mine, and I have a question.
Did you upgrade from 8.04 to 8.10 or did you do a fresh install?

Secondly, go to Synaptic, search for "wodim", and re-install the package.

And while this sounds like something you would do in Windows, reboot the computer and try to do a burn with K3B again and let us know the results.

---

### Post by hifly1231 on 2009-02-18
> **TransitMan said:**
> OK. The CD drive is being seen.
I have compared some of your information to mine, and I have a question.
Did you upgrade from 8.04 to 8.10 or did you do a fresh install?

Secondly, go to Synaptic, search for "wodim", and re-install the package.

And while this sounds like something you would do in Windows, reboot the computer and try to do a burn with K3B again and let us know the results.

This is a fresh 8.10 install, not an upgrade.

I reinstalled "wodim", and rebooted.  I attempted to burn the same song that I was able to burn with DeepBurner, but with no luck.  After about 2 minutes, the CD started spinning, then about 15 seconds after that, K3b said ***"Cdrecord does not have permission to open the device"***.

---

### Post by hifly1231 on 2009-02-20
I've installed **Nero Linux[SIZE="3"][/SIZE] 3.5.2.3** (debian package), and it works **_BEAUTIFULLY_**!!!  I'm **SO GLAD** that I don't have to have resort to having my CD burner installed in ***WINE***!!!  Again, ***IT'S GREAT TO BE FREE FROM WINDOWS XP!!!!!***\\:D/

---

### Post by TransitMan on 2009-02-20
Glad you have your solution, for now.

Good luck.

---


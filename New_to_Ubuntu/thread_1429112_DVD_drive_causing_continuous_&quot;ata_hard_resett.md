---
title: "DVD drive causing continuous &quot;ata hard resetting link&quot; errors"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by willand1 on 2010-03-13
Hardware:
Motherboard:    ECS GS7160 Ultra
CPU:                AMD Athlon  Socket 754  3200+
HDD:               Western Digital WD3200AAKS 312GB SATAII 7200 rpm  16Mb Cache                       OEM Caviar Blue
DVD:               Samsung SH-S223 X22 SATA
RAM:               1Gb (2X 512Mb) Kingston DDR PC3200/400Mhz Non-ECC CL3                 UnBuffered 2.6V
All Hardware is new.

Software:

1    Ubuntu 9.10 karmic Desktop for AMD 64 bit downloaded and burnt to cd-r on    another machine. 
Inserted cd into the newly built machine and powered on. Install went ok. Updated with update manager.

2    LAMP Server Stack. Installed with "sudo apt-get install"

Install booted fine from the DVD drive and initially everything seemed fine. Left PC running for a couple of days and returned to notice the HDD Led flashing almost continually. Found the Log files "messages" was over 586Mb.


On inspection of messages
Lots of this:-

Mar  9 19:58:22 ubuntu-z kernel: [   55.923368] ata2: hard resetting link
Mar  9 19:58:22 ubuntu-z kernel: [   56.270052] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  9 19:58:23 ubuntu-z kernel: [   56.330235] ata2.00: configured for UDMA/100
Mar  9 19:58:23 ubuntu-z kernel: [   56.331331] ata2: EH complete


Tried swapping SATA cables and channels to find that it is the DVD drive that seems to cause the problem.
Disconnected the DVD Drive and all is well (except there's no DVD/CD drive)

Reconnected the DVD and the errors restart. I tried opening the drive and it immediately closes itself.

Managed to insert a data cd containing jpeg files and get the following:-

Mar  9 20:03:44 ubuntu-z kernel: [  378.224945] VFS: busy inodes on changed media or resized disk sr0


Inserted a blank CD-R and rebooted. System came up fine and a "CD-R" Icon appeared on desktop and an entry in messages :-

Mar  9 21:38:19 ubuntu-z kernel: [   20.430319] ata2.00: configured for UDMA/100
Mar  9 21:38:19 ubuntu-z kernel: [   20.431507] ata2: EH complete
Mar  9 21:38:19 ubuntu-z kernel: [   20.431590] cdrom: This disc doesn't have any tracks I recognize!
Mar  9 21:38:19 ubuntu-z kernel: [   20.446054] ata2: hard resetting link
Mar  9 21:38:19 ubuntu-z kernel: [   20.800059] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  9 21:38:19 ubuntu-z kernel: [   20.880254] ata2.00: configured for UDMA/100
Mar  9 21:38:19 ubuntu-z kernel: [   20.890158] ata2: EH complete

System now stable with no messages being produced.
Opened DVD drive and inserted an Audio CD. More messages :-

Mar  9 21:45:45 ubuntu-z kernel: [  466.792317] ata2: hard resetting link
Mar  9 21:45:45 ubuntu-z kernel: [  467.140110] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  9 21:45:45 ubuntu-z kernel: [  467.660275] ata2.00: configured for UDMA/100
Mar  9 21:45:45 ubuntu-z kernel: [  467.662229] ata2: EH complete

Followed by:-

Mar  9 21:52:36 ubuntu-z kernel: [  877.897910] ata2: hard resetting link
Mar  9 21:52:36 ubuntu-z kernel: [  878.240087] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  9 21:52:36 ubuntu-z kernel: [  878.300271] ata2.00: configured for UDMA/100
Mar  9 21:52:36 ubuntu-z kernel: [  878.301810] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar  9 21:52:36 ubuntu-z kernel: [  878.301818] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar  9 21:52:36 ubuntu-z kernel: [  878.301826] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar  9 21:52:36 ubuntu-z kernel: [  878.301863] ata2: EH complete
Mar  9 21:52:36 ubuntu-z kernel: [  878.303975] ata2: hard resetting link
Mar  9 21:52:36 ubuntu-z kernel: [  878.650085] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  9 21:52:36 ubuntu-z kernel: [  878.710272] ata2.00: configured for UDMA/100
Mar  9 21:52:36 ubuntu-z kernel: [  878.711843] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar  9 21:52:36 ubuntu-z kernel: [  878.711851] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar  9 21:52:36 ubuntu-z kernel: [  878.711860] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar  9 21:52:36 ubuntu-z kernel: [  878.711900] ata2: EH complete
Mar  9 21:52:38 ubuntu-z kernel: [  880.219275] ata2: hard resetting link
Mar  9 21:52:38 ubuntu-z kernel: [  880.560077] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  9 21:52:38 ubuntu-z kernel: [  880.620266] ata2.00: configured for UDMA/100
Mar  9 21:52:38 ubuntu-z kernel: [  880.622017] ata2: EH complete

Audio player then launched and no further errors.

It seems that as long as there is a disc in the dvd drive all is ok.
Any help would be greatly appreciated.

---


---
title: "gnomebaker burn keeps failing"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by mystmaiden on 2009-08-19
Once I got gnome baker I thought my disc burning issues were over, seems I was mistaken. Always before I needed to choose the slowest speed but the burn would work. Now I am getting a fail about mid burn each time with this error output
 ```
odim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr1'
devname: '/dev/sr1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.9
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'SONY    '
Identification : 'CD-RW  CRX175E  '
Revision       : '1.1b'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 1821440 = 1778 KB
Drive DMA Speed: 2517 kB/s 14x CD 1x DVD
FIFO size      : 12582912 = 12288 KB
Speed set to 706 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 0F 80 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 12 00 00 00 00 24 00 00 C0
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid) error refers to command part, bit ptr 0 (not valid) field ptr 0
cmd finished after 4.222s timeout 40s
wodim: A write error occured.
wodim: Please properly read the error message above.

write track data: error after 8126464 bytes
Writing  time:   28.578s
Average write speed  32.7x.
Min drive buffer fill was 95%
Fixating...
Fixating time:   61.762s
wodim: fifo had 320 puts and 129 gets.
wodim: fifo was 0 times empty and 98 times full, min fill was 98%.

```

I tried using an iso of puppy linux I know is good, same deal. I wonder if its the discs or the burner. Any insight would be appreciated.

mystmaiden

---


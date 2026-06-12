---
title: "K3b gives error code 254"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Joe Soap on 2009-01-21
Since quite recently k3b has been giving problems.  

I am running Intrepid.  Today I wanted to burn an audio cd and, as usual, fired up k3b.  The first problem I encountered was a permission problem.  A google or two later, that was solved.  

The second problem was this "code 254"error - "cdrecord returned an unknown error (code 254)" to be exact.

Several googles later, I am at the end of my tether.  K3b worked fine until recently.  I'm pretty sure that I was able to burn cd's without problems even after the upgrade to Intrepid.  The problems started about two weeks ago (iirc).

Anyway, here's the debugging output from k3b:
```
System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.27-11-generic
Devices
-----------------------
LITE-ON DVDRW LH-20A1H LL0A (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Used versions
-----------------------
cdrecord: 1.1.8

cdrecord
-----------------------
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.8
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'LITE-ON '
Identification : 'DVDRW LH-20A1H  '
Revision       : 'LL0A'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 988416 = 965 KB
FIFO size      : 12582912 = 12288 KB
pregap1: -1
Track 01: audio   41 MB (04:07.09) no preemp swab copy
Track 02: audio   43 MB (04:19.34) no preemp swab copy
Track 03: audio   43 MB (04:21.41) no preemp swab copy
Track 04: audio   46 MB (04:34.48) no preemp swab copy
Track 05: audio   31 MB (03:07.32) no preemp swab copy
Track 06: audio   45 MB (04:33.09) no preemp swab copy
Track 07: audio   39 MB (03:55.46) no preemp swab copy
Track 08: audio   43 MB (04:15.74) no preemp swab copy
Track 09: audio   39 MB (03:52.40) no preemp swab copy
Track 10: audio   39 MB (03:55.10) no preemp swab copy
Track 11: audio   46 MB (04:35.49) no preemp swab copy
Track 12: audio   33 MB (03:22.00) no preemp swab copy
Track 13: audio   34 MB (03:27.30) no preemp swab copy
Track 14: audio   51 MB (05:04.85) no preemp swab copy
Track 15: audio   52 MB (05:09.24) no preemp swab copy
Track 16: audio   59 MB (05:53.78) no preemp swab copy
Track 17: audio   39 MB (03:53.70) no preemp swab copy
Track 18: audio   64 MB (06:24.84) no preemp swab copy
Speed set to 2822 KB/s
Total size:      801 MB (79:26.69) = 357502 sectors
Lout start:      802 MB (79:28/52) = 357502 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -11834 (97:24/16)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 24
Manufacturer: SONY Corporation
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 2347
Forcespeed is OFF.
Starting to write CD/DVD at speed  16.0 in dummy TAO mode for single session.
Last chance to quit, starting dummy write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Starting new track at sector: 0
Track 01:    0 of   41 MB written.
Track 01:    1 of   41 MB written (fifo 100%) [buf  99%]   1.3x.
Track 01:    2 of   41 MB written (fifo 100%) [buf  99%]  17.6x.
Track 01:    3 of   41 MB written (fifo 100%) [buf  99%]  18.3x.
Track 01:    4 of   41 MB written (fifo 100%) [buf  99%]  17.8x.
Track 01:    5 of   41 MB written (fifo 100%) [buf  99%]  18.4x.
Track 01:    6 of   41 MB written (fifo 100%) [buf  99%]  17.9x.
Track 01:    7 of   41 MB written (fifo 100%) [buf  99%]  18.6x.
Track 01:    8 of   41 MB written (fifo 100%) [buf  99%]  18.1x.
Track 01:    9 of   41 MB written (fifo 100%) [buf  99%]  18.7x.
Track 01:   10 of   41 MB written (fifo  99%) [buf  99%]  18.2x.
Track 01:   11 of   41 MB written (fifo 100%) [buf  99%]  18.9x.
Track 01:   12 of   41 MB written (fifo  99%) [buf  99%]  18.4x.
Track 01:   13 of   41 MB written (fifo  99%) [buf  99%]  19.1x.
Track 01:   14 of   41 MB written (fifo 100%) [buf  99%]  18.6x.
Track 01:   15 of   41 MB written (fifo 100%) [buf  99%]  19.2x.
Track 01:   16 of   41 MB written (fifo 100%) [buf  99%]  18.7x.
Track 01:   17 of   41 MB written (fifo 100%) [buf  99%]  19.4x.
Track 01:   18 of   41 MB written (fifo  99%) [buf  99%]  18.9x.
Track 01:   19 of   41 MB written (fifo 100%) [buf  99%]  19.6x.
Track 01:   20 of   41 MB written (fifo 100%) [buf  99%]  19.1x.
Track 01:   21 of   41 MB written (fifo 100%) [buf  99%]  19.7x.
Track 01:   22 of   41 MB written (fifo 100%) [buf  99%]  19.2x.
Track 01:   23 of   41 MB written (fifo 100%) [buf  99%]  19.9x.
Track 01:   24 of   41 MB written (fifo  99%) [buf  99%]  19.4x.
Track 01:   25 of   41 MB written (fifo 100%) [buf  99%]  20.1x.
Track 01:   26 of   41 MB written (fifo 100%) [buf  99%]  19.5x.
Track 01:   27 of   41 MB written (fifo 100%) [buf  99%]  20.2x.
Track 01:   28 of   41 MB written (fifo  99%) [buf  97%]  19.4x.
Track 01:   29 of   41 MB written (fifo 100%) [buf  99%]  20.7x.
Track 01:   30 of   41 MB written (fifo 100%) [buf  99%]  19.8x.
Track 01:   31 of   41 MB written (fifo 100%) [buf  99%]  20.6x.
Track 01:   32 of   41 MB written (fifo 100%) [buf  99%]  20.0x.
Track 01:   33 of   41 MB written (fifo  99%) [buf  99%]  20.7x.
Track 01:   34 of   41 MB written (fifo  99%) [buf  99%]  20.1x.
Track 01:   35 of   41 MB written (fifo 100%) [buf  99%]  20.8x.
Track 01:   36 of   41 MB written (fifo  99%) [buf  99%]  20.2x.
Track 01:   37 of   41 MB written (fifo  99%) [buf  99%]  20.9x.
Track 01:   38 of   41 MB written (fifo  99%) [buf  99%]  20.2x.
Track 01:   39 of   41 MB written (fifo 100%) [buf  99%]  20.9x.
Track 01:   40 of   41 MB written (fifo 100%) [buf  99%]  20.3x.
Track 01:   41 of   41 MB written (fifo 100%) [buf  99%]  21.0x.
Track 01: Total bytes read/written: 43587264/43587264 (18532 sectors).
Starting new track at sector: 18684
Track 02:    0 of   43 MB written.
Track 02:    1 of   43 MB written (fifo 100%) [buf  99%]   5.1x.
Track 02:    2 of   43 MB written (fifo 100%) [buf  99%]  21.0x.
Track 02:    3 of   43 MB written (fifo 100%) [buf  99%]  21.7x.
Track 02:    4 of   43 MB written (fifo 100%) [buf  99%]  21.1x.
Track 02:    5 of   43 MB written (fifo 100%) [buf  99%]  21.7x.
Track 02:    6 of   43 MB written (fifo 100%) [buf  99%]  21.1x.
Track 02:    7 of   43 MB written (fifo  99%) [buf  99%]  21.8x.
Track 02:    8 of   43 MB written (fifo 100%) [buf  99%]  21.2x.
Track 02:    9 of   43 MB written (fifo  99%) [buf  99%]  21.9x.
Track 02:   10 of   43 MB written (fifo 100%) [buf  99%]  21.2x.
Track 02:   11 of   43 MB written (fifo  99%) [buf  99%]  21.9x.
Track 02:   12 of   43 MB written (fifo 100%) [buf  99%]  21.3x.
Track 02:   13 of   43 MB written (fifo  99%) [buf  98%]  22.1x.
Track 02:   14 of   43 MB written (fifo  99%) [buf  99%]  21.4x.
Track 02:   15 of   43 MB written (fifo  99%) [buf  99%]  22.1x.
Track 02:   16 of   43 MB written (fifo 100%) [buf  99%]  21.4x.
Track 02:   17 of   43 MB written (fifo 100%) [buf  99%]  22.1x.
Track 02:   18 of   43 MB written (fifo 100%) [buf  99%]  21.5x.
Track 02:   19 of   43 MB written (fifo  99%) [buf  99%]  22.2x.
Track 02:   20 of   43 MB written (fifo 100%) [buf  95%]  21.0x.
Track 02:   21 of   43 MB written (fifo 100%) [buf  99%]  22.9x.
Track 02:   22 of   43 MB written (fifo 100%) [buf  99%]  21.6x.
Track 02:   23 of   43 MB written (fifo  99%) [buf  99%]  22.3x.
Track 02:   24 of   43 MB written (fifo 100%) [buf  99%]  21.7x.
Track 02:   25 of   43 MB written (fifo  99%) [buf  99%]  22.4x.
Track 02:   26 of   43 MB written (fifo 100%) [buf  99%]  21.7x.
Track 02:   27 of   43 MB written (fifo  99%) [buf  99%]  22.5x.
Track 02:   28 of   43 MB written (fifo 100%) [buf  99%]  21.8x.
Track 02:   29 of   43 MB written (fifo  99%) [buf  99%]  22.5x.
Track 02:   30 of   43 MB written (fifo  99%) [buf  99%]  21.9x.
Track 02:   31 of   43 MB written (fifo  99%) [buf  99%]  22.6x.
Track 02:   32 of   43 MB written (fifo 100%) [buf  99%]  21.9x.
Track 02:   33 of   43 MB written (fifo 100%) [buf  99%]  22.6x.
Track 02:   34 of   43 MB written (fifo  99%) [buf  99%]  21.9x.
Track 02:   35 of   43 MB written (fifo 100%) [buf  99%]  22.7x.
Track 02:   36 of   43 MB written (fifo  99%) [buf  99%]  22.0x.
Track 02:   37 of   43 MB written (fifo 100%) [buf  99%]  22.7x.
Track 02:   38 of   43 MB written (fifo  99%) [buf  99%]  22.1x.
Track 02:   39 of   43 MB written (fifo 100%) [buf  99%]  22.8x.
Track 02:   40 of   43 MB written (fifo  99%) [buf  99%]  22.1x.
Track 02:   41 of   43 MB written (fifo  99%) [buf  99%]  22.9x.
Track 02:   42 of   43 MB written (fifo 100%) [buf  98%]  22.2x.
Track 02:   43 of   43 MB written (fifo 100%) [buf  99%]  22.9x.
Track 02: Total bytes read/written: 45748752/45748752 (19451 sectors).
Starting new track at sector: 38287
Track 03:    0 of   43 MB written.
Track 03:    1 of   43 MB written (fifo 100%) [buf  99%]   5.3x.
Track 03:    2 of   43 MB written (fifo 100%) [buf  99%]  23.0x.
Track 03:    3 of   43 MB written (fifo  99%) [buf  99%]  23.7x.
Track 03:    4 of   43 MB written (fifo  99%) [buf  99%]  23.0x.
Track 03:    5 of   43 MB written (fifo 100%) [buf  99%]  23.8x.
Track 03:    6 of   43 MB written (fifo 100%) [buf  99%]  23.1x.
Track 03:    7 of   43 MB written (fifo  99%) [buf  99%]  23.9x.
Track 03:    8 of   43 MB written (fifo 100%) [buf  99%]  23.1x.
Track 03:    9 of   43 MB written (fifo 100%) [buf  99%]  23.9x.
Track 03:   10 of   43 MB written (fifo  99%) [buf  98%]  23.2x.
Track 03:   11 of   43 MB written (fifo 100%) [buf  98%]  23.9x.
Track 03:   12 of   43 MB written (fifo 100%) [buf  98%]  23.2x.
Track 03:   13 of   43 MB written (fifo  99%) [buf  99%]  24.0x.
Track 03:   14 of   43 MB written (fifo 100%) [buf  99%]  23.3x.
Track 03:   15 of   43 MB written (fifo 100%) [buf  99%]  24.1x.
Track 03:   16 of   43 MB written (fifo 100%) [buf  99%]  23.3x.
Track 03:   17 of   43 MB written (fifo 100%) [buf  99%]  24.1x.
Track 03:   18 of   43 MB written (fifo 100%) [buf  99%]  23.4x.
Track 03:   19 of   43 MB written (fifo 100%) [buf  99%]  24.2x.
Track 03:   20 of   43 MB written (fifo 100%) [buf  99%]  23.4x.
Track 03:   21 of   43 MB written (fifo 100%) [buf  99%]  24.2x.
Track 03:   22 of   43 MB written (fifo 100%) [buf  99%]  23.5x.
Track 03:   23 of   43 MB written (fifo 100%) [buf  98%]  24.2x.
Track 03:   24 of   43 MB written (fifo 100%) [buf  99%]  23.6x.
Track 03:   25 of   43 MB written (fifo 100%) [buf  98%]  24.3x.
Track 03:   26 of   43 MB written (fifo  99%) [buf  98%]  23.6x.
Track 03:   27 of   43 MB written (fifo 100%) [buf  98%]  24.3x.
Track 03:   28 of   43 MB written (fifo 100%) [buf  98%]  23.6x.
Track 03:   29 of   43 MB written (fifo  99%) [buf  99%]  24.4x.
Track 03:   30 of   43 MB written (fifo 100%) [buf  98%]  23.7x.
Track 03:   31 of   43 MB written (fifo 100%) [buf  99%]  24.5x.
Track 03:   32 of   43 MB written (fifo 100%) [buf  99%]  23.7x.
Track 03:   33 of   43 MB written (fifo 100%) [buf  99%]  24.5x.
Track 03:   34 of   43 MB written (fifo 100%) [buf  99%]  23.8x.
Track 03:   35 of   43 MB written (fifo  99%) [buf  99%]  24.6x.
Track 03:   36 of   43 MB written (fifo 100%) [buf  99%]  23.8x.
Track 03:   37 of   43 MB written (fifo 100%) [buf  99%]  24.6x.
Track 03:   38 of   43 MB written (fifo 100%) [buf  99%]  23.9x.
Track 03:   39 of   43 MB written (fifo  99%) [buf  99%]  24.6x.
Track 03:   40 of   43 MB written (fifo  99%) [buf  99%]  23.9x.
Track 03:   41 of   43 MB written (fifo 100%) [buf  98%]  24.7x.
Track 03:   42 of   43 MB written (fifo  99%) [buf  99%]  24.0x.
Track 03:   43 of   43 MB written (fifo 100%) [buf  99%]  24.7x.
Track 03: Total bytes read/written: 46113312/46113312 (19606 sectors).
Starting new track at sector: 58045
Track 04:    0 of   46 MB written.
Track 04:    1 of   46 MB written (fifo 100%) [buf  98%]   5.5x.
Track 04:    2 of   46 MB written (fifo 100%) [buf  98%]  24.8x.
Track 04:    3 of   46 MB written (fifo 100%) [buf  91%]  24.1x.
Track 04:    4 of   46 MB written (fifo 100%) [buf  98%]  26.4x.
Track 04:    5 of   46 MB written (fifo 100%) [buf  99%]  25.7x.
Track 04:    6 of   46 MB written (fifo  99%) [buf  99%]  24.9x.
Track 04:    7 of   46 MB written (fifo  99%) [buf  99%]  25.7x.
Track 04:    8 of   46 MB written (fifo  99%) [buf  99%]  24.9x.
Track 04:    9 of   46 MB written (fifo 100%) [buf  98%]  25.7x.
Track 04:   10 of   46 MB written (fifo 100%) [buf  89%]  23.3x.
Track 04:   11 of   46 MB written (fifo 100%) [buf  98%]  27.9x.
Track 04:   12 of   46 MB written (fifo  99%) [buf  99%]  25.0x.
Track 04:   13 of   46 MB written (fifo 100%) [buf  98%]  25.8x.
Track 04:   14 of   46 MB written (fifo  99%) [buf  98%]  25.1x.
Track 04:   15 of   46 MB written (fifo 100%) [buf  98%]  25.9x.
Track 04:   16 of   46 MB written (fifo  99%) [buf  98%]  25.1x.
Track 04:   17 of   46 MB written (fifo  99%) [buf  98%]  25.9x.
Track 04:   18 of   46 MB written (fifo  99%) [buf  98%]  25.2x.
Track 04:   19 of   46 MB written (fifo 100%) [buf  98%]  26.0x.
Track 04:   20 of   46 MB written (fifo 100%) [buf  98%]  25.2x.
Track 04:   21 of   46 MB written (fifo  99%) [buf  98%]  26.0x.
Track 04:   22 of   46 MB written (fifo 100%) [buf  98%]  25.2x.
Track 04:   23 of   46 MB written (fifo  99%) [buf  98%]  26.0x.
Track 04:   24 of   46 MB written (fifo  99%) [buf  98%]  25.3x.
Track 04:   25 of   46 MB written (fifo  99%) [buf  98%]  26.1x.
Track 04:   26 of   46 MB written (fifo 100%) [buf  98%]  25.3x.
Track 04:   27 of   46 MB written (fifo 100%) [buf  98%]  26.1x.
Track 04:   28 of   46 MB written (fifo 100%) [buf  98%]  25.3x.
Track 04:   29 of   46 MB written (fifo  99%) [buf  98%]  26.0x.
Track 04:   30 of   46 MB written (fifo  99%) [buf  98%]  25.6x.
Track 04:   31 of   46 MB written (fifo  99%) [buf  98%]  26.2x.
Track 04:   32 of   46 MB written (fifo  99%) [buf  98%]  25.4x.
Track 04:   33 of   46 MB written (fifo 100%) [buf  98%]  26.2x.
Track 04:   34 of   46 MB written (fifo 100%) [buf  98%]  25.4x.
Track 04:   35 of   46 MB written (fifo 100%) [buf  98%]  26.3x.
Track 04:   36 of   46 MB written (fifo 100%) [buf  98%]  25.5x.
Track 04:   37 of   46 MB written (fifo  99%) [buf  98%]  26.3x.
Track 04:   38 of   46 MB written (fifo 100%) [buf  98%]  25.5x.
Track 04:   39 of   46 MB written (fifo  99%) [buf  98%]  26.3x.
Track 04:   40 of   46 MB written (fifo  99%) [buf  98%]  25.6x.
Track 04:   41 of   46 MB written (fifo 100%) [buf  98%]  26.4x.
Track 04:   42 of   46 MB written (fifo  99%) [buf  98%]  25.7x.
Track 04:   43 of   46 MB written (fifo 100%) [buf  98%]  26.4x.
Track 04:   44 of   46 MB written (fifo  99%) [buf  98%]  27.3x.
Track 04:   45 of   46 MB written (fifo  99%) [buf  98%]  26.4x.
Track 04:   46 of   46 MB written (fifo  99%) [buf  98%]  27.3x.
Track 04: Total bytes read/written: 48418272/48418272 (20586 sectors).
Starting new track at sector: 78783
Track 05:    0 of   31 MB written.
Track 05:    1 of   31 MB written (fifo 100%) [buf  98%]   5.7x.
Track 05:    2 of   31 MB written (fifo 100%) [buf  98%]  26.6x.
Track 05:    3 of   31 MB written (fifo 100%) [buf  98%]  27.5x.
Track 05:    4 of   31 MB written (fifo 100%) [buf  98%]  26.6x.
Track 05:    5 of   31 MB written (fifo 100%) [buf  98%]  27.5x.
Track 05:    6 of   31 MB written (fifo 100%) [buf  98%]  26.6x.
Track 05:    7 of   31 MB written (fifo 100%) [buf  98%]  27.6x.
Track 05:    8 of   31 MB written (fifo  99%) [buf  98%]  26.7x.
Track 05:    9 of   31 MB written (fifo  99%) [buf  93%]  26.5x.
Track 05:   10 of   31 MB written (fifo  99%) [buf  98%]  27.8x.
Track 05:   11 of   31 MB written (fifo 100%) [buf  98%]  27.6x.
Track 05:   12 of   31 MB written (fifo  99%) [buf  98%]  26.7x.
Track 05:   13 of   31 MB written (fifo 100%) [buf  98%]  27.7x.
Track 05:   14 of   31 MB written (fifo  99%) [buf  98%]  26.8x.
Track 05:   15 of   31 MB written (fifo  99%) [buf  98%]  27.7x.
Track 05:   16 of   31 MB written (fifo 100%) [buf  98%]  26.8x.
Track 05:   17 of   31 MB written (fifo  99%) [buf  98%]  27.7x.
Track 05:   18 of   31 MB written (fifo 100%) [buf  98%]  26.9x.
Track 05:   19 of   31 MB written (fifo 100%) [buf  98%]  27.8x.
Track 05:   20 of   31 MB written (fifo  99%) [buf  98%]  26.9x.
Track 05:   21 of   31 MB written (fifo 100%) [buf  98%]  27.8x.
Track 05:   22 of   31 MB written (fifo  99%) [buf  98%]  26.9x.
Track 05:   23 of   31 MB written (fifo 100%) [buf  98%]  27.8x.
Track 05:   24 of   31 MB written (fifo  99%) [buf  98%]  27.0x.
Track 05:   25 of   31 MB written (fifo  99%) [buf  98%]  27.9x.
Track 05:   26 of   31 MB written (fifo 100%) [buf  98%]  27.0x.
Track 05:   27 of   31 MB written (fifo  99%) [buf  98%]  27.9x.
Track 05:   28 of   31 MB written (fifo 100%) [buf  98%]  27.0x.
Track 05:   29 of   31 MB written (fifo  99%) [buf  98%]  27.9x.
Track 05:   30 of   31 MB written (fifo  99%) [buf  98%]  27.1x.
Track 05:   31 of   31 MB written (fifo 100%) [buf  98%]  28.0x.
Track 05: Total bytes read/written: 33043248/33043248 (14049 sectors).
Starting new track at sector: 92984
Track 06:    0 of   45 MB written.
Track 06:    1 of   45 MB written (fifo 100%) [buf  98%]   5.9x.
Track 06:    2 of   45 MB written (fifo 100%) [buf  98%]  27.8x.
Track 06:    3 of   45 MB written (fifo  99%) [buf  98%]  28.7x.
Track 06:    4 of   45 MB written (fifo  99%) [buf  98%]  27.8x.
Track 06:    5 of   45 MB written (fifo  99%) [buf  98%]  28.7x.
Track 06:    6 of   45 MB written (fifo 100%) [buf  98%]  27.8x.
Track 06:    7 of   45 MB written (fifo 100%) [buf  98%]  28.8x.
Track 06:    8 of   45 MB written (fifo  99%) [buf  98%]  27.9x.
Track 06:    9 of   45 MB written (fifo 100%) [buf  98%]  28.7x.
Track 06:   10 of   45 MB written (fifo 100%) [buf  98%]  27.9x.
Track 06:   11 of   45 MB written (fifo 100%) [buf  98%]  28.8x.
Track 06:   12 of   45 MB written (fifo  99%) [buf  98%]  27.9x.
Track 06:   13 of   45 MB written (fifo  99%) [buf  98%]  28.9x.
Track 06:   14 of   45 MB written (fifo 100%) [buf  98%]  28.0x.
Track 06:   15 of   45 MB written (fifo 100%) [buf  98%]  28.8x.
Track 06:   16 of   45 MB written (fifo  99%) [buf  98%]  28.0x.
Track 06:   17 of   45 MB written (fifo  99%) [buf  98%]  28.9x.
Track 06:   18 of   45 MB written (fifo  99%) [buf  98%]  28.0x.
Track 06:   19 of   45 MB written (fifo  99%) [buf  98%]  28.9x.
Track 06:   20 of   45 MB written (fifo  99%) [buf  98%]  28.0x.
Track 06:   21 of   45 MB written (fifo  99%) [buf  98%]  28.9x.
Track 06:   22 of   45 MB written (fifo  99%) [buf  98%]  28.0x.
Track 06:   23 of   45 MB written (fifo  99%) [buf  98%]  28.9x.
Track 06:   24 of   45 MB written (fifo  99%) [buf  98%]  28.1x.
Track 06:   25 of   45 MB written (fifo  99%) [buf  98%]  29.0x.
Track 06:   26 of   45 MB written (fifo  99%) [buf  98%]  28.1x.
Track 06:   27 of   45 MB written (fifo  99%) [buf  98%]  29.0x.
Track 06:   28 of   45 MB written (fifo  99%) [buf  98%]  28.1x.
Track 06:   29 of   45 MB written (fifo  99%) [buf  98%]  29.0x.
Track 06:   30 of   45 MB written (fifo 100%) [buf  98%]  28.2x.
Track 06:   31 of   45 MB written (fifo  99%) [buf  98%]  29.1x.
Track 06:   32 of   45 MB written (fifo  99%) [buf  98%]  28.2x.
Track 06:   33 of   45 MB written (fifo 100%) [buf  98%]  29.1x.
Track 06:   34 of   45 MB written (fifo  99%) [buf  98%]  28.2x.
Track 06:   35 of   45 MB written (fifo 100%) [buf  98%]  29.1x.
Track 06:   36 of   45 MB written (fifo  99%) [buf  98%]  28.3x.
Track 06:   37 of   45 MB written (fifo 100%) [buf  98%]  29.2x.
Track 06:   38 of   45 MB written (fifo 100%) [buf  98%]  28.3x.
Track 06:   39 of   45 MB written (fifo  99%) [buf  98%]  29.2x.
Track 06:   40 of   45 MB written (fifo 100%) [buf  98%]  28.3x.
Track 06:   41 of   45 MB written (fifo 100%) [buf  98%]  29.2x.
Track 06:   42 of   45 MB written (fifo  99%) [buf  98%]  28.4x.
Track 06:   43 of   45 MB written (fifo 100%) [buf  98%]  29.2x.
Track 06:   44 of   45 MB written (fifo  99%) [buf  98%]  30.1x.
Track 06:   45 of   45 MB written (fifo  99%) [buf  98%]  29.2x.
Track 06: Total bytes read/written: 48173664/48173664 (20482 sectors).
Starting new track at sector: 113618
Track 07:    0 of   39 MB written.
Track 07:    1 of   39 MB written (fifo  99%) [buf  98%]   6.0x.
Track 07:    2 of   39 MB written (fifo 100%) [buf  98%]  29.3x.
Track 07:    3 of   39 MB written (fifo 100%) [buf  88%]  28.0x.
Track 07:    4 of   39 MB written (fifo  99%) [buf  98%]  31.8x.
Track 07:    5 of   39 MB written (fifo  99%) [buf  98%]  30.3x.
Track 07:    6 of   39 MB written (fifo  99%) [buf  98%]  29.4x.
Track 07:    7 of   39 MB written (fifo  99%) [buf  98%]  30.4x.
Track 07:    8 of   39 MB written (fifo 100%) [buf  98%]  29.4x.
Track 07:    9 of   39 MB written (fifo  99%) [buf  98%]  30.4x.
Track 07:   10 of   39 MB written (fifo  99%) [buf  98%]  29.4x.
Track 07:   11 of   39 MB written (fifo  99%) [buf  98%]  30.4x.
Track 07:   12 of   39 MB written (fifo 100%) [buf  98%]  29.4x.
Track 07:   13 of   39 MB written (fifo 100%) [buf  98%]  30.4x.
Track 07:   14 of   39 MB written (fifo  99%) [buf  98%]  29.5x.
Track 07:   15 of   39 MB written (fifo  99%) [buf  98%]  30.4x.
Track 07:   16 of   39 MB written (fifo 100%) [buf  98%]  29.5x.
Track 07:   17 of   39 MB written (fifo  99%) [buf  98%]  30.4x.
Track 07:   18 of   39 MB written (fifo  99%) [buf  98%]  29.6x.
Track 07:   19 of   39 MB written (fifo  99%) [buf  98%]  30.5x.
Track 07:   20 of   39 MB written (fifo  99%) [buf  98%]  29.6x.
Track 07:   21 of   39 MB written (fifo 100%) [buf  98%]  30.5x.
Track 07:   22 of   39 MB written (fifo  99%) [buf  98%]  29.6x.
Track 07:   23 of   39 MB written (fifo 100%) [buf  98%]  30.5x.
Track 07:   24 of   39 MB written (fifo  99%) [buf  98%]  29.6x.
Track 07:   25 of   39 MB written (fifo  99%) [buf  98%]  30.6x.
Track 07:   26 of   39 MB written (fifo  99%) [buf  98%]  29.6x.
Track 07:   27 of   39 MB written (fifo 100%) [buf  98%]  30.6x.
Track 07:   28 of   39 MB written (fifo  99%) [buf  98%]  29.7x.
Track 07:   29 of   39 MB written (fifo  99%) [buf  98%]  30.6x.
Track 07:   30 of   39 MB written (fifo  99%) [buf  98%]  29.7x.
Track 07:   31 of   39 MB written (fifo 100%) [buf  98%]  30.6x.
Track 07:   32 of   39 MB written (fifo  99%) [buf  98%]  29.7x.
Track 07:   33 of   39 MB written (fifo 100%) [buf  98%]  30.6x.
Track 07:   34 of   39 MB written (fifo  99%) [buf  98%]  29.7x.
Track 07:   35 of   39 MB written (fifo  99%) [buf  98%]  30.7x.
Track 07:   36 of   39 MB written (fifo 100%) [buf  98%]  29.8x.
Track 07:   37 of   39 MB written (fifo  99%) [buf  98%]  30.7x.
Track 07:   38 of   39 MB written (fifo  99%) [buf  98%]  29.8x.
Track 07:   39 of   39 MB written (fifo  99%) [buf  98%]  30.7x.
Track 07: Total bytes read/written: 41536320/41536320 (17660 sectors).
Starting new track at sector: 131430
Track 08:    0 of   43 MB written.
Track 08:    1 of   43 MB written (fifo  99%) [buf  93%]   6.2x.
Track 08:    2 of   43 MB written (fifo  99%) [buf  98%]  31.9x.
Track 08:    3 of   43 MB written (fifo  99%) [buf  98%]  31.7x.
Track 08:    4 of   43 MB written (fifo  99%) [buf  98%]  30.7x.
Track 08:    5 of   43 MB written (fifo 100%) [buf  98%]  31.6x.
Track 08:    6 of   43 MB written (fifo  99%) [buf  98%]  30.7x.
Track 08:    7 of   43 MB written (fifo 100%) [buf  98%]  31.7x.
Track 08:    8 of   43 MB written (fifo 100%) [buf  98%]  30.7x.
Track 08:    9 of   43 MB written (fifo  99%) [buf  98%]  31.7x.
Track 08:   10 of   43 MB written (fifo  99%) [buf  98%]  30.7x.
Track 08:   11 of   43 MB written (fifo  99%) [buf  98%]  31.7x.
Track 08:   12 of   43 MB written (fifo 100%) [buf  98%]  30.7x.
Track 08:   13 of   43 MB written (fifo 100%) [buf  98%]  31.8x.
Track 08:   14 of   43 MB written (fifo 100%) [buf  98%]  30.8x.
Track 08:   15 of   43 MB written (fifo  99%) [buf  98%]  31.8x.
Track 08:   16 of   43 MB written (fifo 100%) [buf  98%]  30.8x.
Track 08:   17 of   43 MB written (fifo 100%) [buf  98%]  31.7x.
Track 08:   18 of   43 MB written (fifo  99%) [buf  98%]  30.9x.
Track 08:   19 of   43 MB written (fifo  99%) [buf  98%]  31.9x.
Track 08:   20 of   43 MB written (fifo 100%) [buf  98%]  30.9x.
Track 08:   21 of   43 MB written (fifo 100%) [buf  98%]  31.8x.
Track 08:   22 of   43 MB written (fifo 100%) [buf  98%]  30.9x.
Track 08:   23 of   43 MB written (fifo 100%) [buf  98%]  31.8x.
Track 08:   24 of   43 MB written (fifo  99%) [buf  98%]  30.9x.
Track 08:   25 of   43 MB written (fifo  99%) [buf  98%]  31.9x.
Track 08:   26 of   43 MB written (fifo  99%) [buf  98%]  30.9x.
Track 08:   27 of   43 MB written (fifo  99%) [buf  98%]  31.9x.
Track 08:   28 of   43 MB written (fifo 100%) [buf  98%]  30.9x.
Track 08:   29 of   43 MB written (fifo 100%) [buf  98%]  31.9x.
Track 08:   30 of   43 MB written (fifo  99%) [buf  98%]  31.0x.
Track 08:   31 of   43 MB written (fifo 100%) [buf  98%]  31.9x.
Track 08:   32 of   43 MB written (fifo  99%) [buf  98%]  31.0x.
Track 08:   33 of   43 MB written (fifo  99%) [buf  98%]  31.9x.
Track 08:   34 of   43 MB written (fifo  99%) [buf  98%]  31.0x.
Track 08:   35 of   43 MB written (fifo  99%) [buf  98%]  32.0x.
Track 08:   36 of   43 MB written (fifo 100%) [buf  98%]  31.0x.
Track 08:   37 of   43 MB written (fifo 100%) [buf  98%]  32.0x.
Track 08:   38 of   43 MB written (fifo 100%) [buf  98%]  31.0x.
Track 08:   39 of   43 MB written (fifo  99%) [buf  98%]  32.0x.
Track 08:   40 of   43 MB written (fifo  99%) [buf  98%]  31.0x.
Track 08:   41 of   43 MB written (fifo 100%) [buf  98%]  32.0x.
Track 08:   42 of   43 MB written (fifo  99%) [buf  98%]  31.1x.
Track 08:   43 of   43 MB written (fifo  99%) [buf  98%]  32.1x.
Track 08: Total bytes read/written: 45113712/45113712 (19181 sectors).
Starting new track at sector: 150763
Track 09:    0 of   39 MB written.
Track 09:    1 of   39 MB written (fifo  99%) [buf  98%]   6.3x.
Track 09:    2 of   39 MB written (fifo 100%) [buf  98%]  32.0x.
Track 09:    3 of   39 MB written (fifo 100%) [buf  98%]  33.1x.
Track 09:    4 of   39 MB written (fifo  99%) [buf  98%]  32.0x.
Track 09:    5 of   39 MB written (fifo  99%) [buf  98%]  33.1x.
Track 09:    6 of   39 MB written (fifo  98%) [buf  98%]  32.0x.
Track 09:    7 of   39 MB written (fifo 100%) [buf  98%]  33.1x.
Track 09:    8 of   39 MB written (fifo  99%) [buf  98%]  32.1x.
Track 09:    9 of   39 MB written (fifo  99%) [buf  98%]  33.1x.
Track 09:   10 of   39 MB written (fifo 100%) [buf  98%]  32.1x.
Track 09:   11 of   39 MB written (fifo 100%) [buf  98%]  33.1x.
Track 09:   12 of   39 MB written (fifo  99%) [buf  98%]  32.1x.
Track 09:   13 of   39 MB written (fifo  99%) [buf  98%]  33.2x.
Track 09:   14 of   39 MB written (fifo  98%) [buf  98%]  32.1x.
Track 09:   15 of   39 MB written (fifo  99%) [buf  98%]  33.1x.
Track 09:   16 of   39 MB written (fifo 100%) [buf  98%]  32.1x.
Track 09:   17 of   39 MB written (fifo 100%) [buf  98%]  33.1x.
Track 09:   18 of   39 MB written (fifo 100%) [buf  98%]  32.2x.
Track 09:   19 of   39 MB written (fifo  99%) [buf  98%]  33.2x.
Track 09:   20 of   39 MB written (fifo 100%) [buf  98%]  32.2x.
Track 09:   21 of   39 MB written (fifo 100%) [buf  98%]  33.2x.
Track 09:   22 of   39 MB written (fifo 100%) [buf  98%]  32.2x.
Track 09:   23 of   39 MB written (fifo 100%) [buf  98%]  33.2x.
Track 09:   24 of   39 MB written (fifo  99%) [buf  98%]  32.3x.
Track 09:   25 of   39 MB written (fifo  99%) [buf  98%]  33.3x.
Track 09:   26 of   39 MB written (fifo 100%) [buf  98%]  32.2x.
Track 09:   27 of   39 MB written (fifo  99%) [buf  98%]  33.2x.
Track 09:   28 of   39 MB written (fifo  99%) [buf  98%]  32.1x.
Track 09:   29 of   39 MB written (fifo  99%) [buf  98%]  33.1x.
Track 09:   30 of   39 MB written (fifo  99%) [buf  98%]  32.1x.
Track 09:   31 of   39 MB written (fifo  99%) [buf  98%]  33.1x.
Track 09:   32 of   39 MB written (fifo 100%) [buf  98%]  32.0x.
Track 09:   33 of   39 MB written (fifo 100%) [buf  98%]  33.0x.
Track 09:   34 of   39 MB written (fifo  99%) [buf  98%]  32.0x.
Track 09:   35 of   39 MB written (fifo  99%) [buf  98%]  33.0x.
Track 09:   36 of   39 MB written (fifo  99%) [buf  98%]  32.0x.
Track 09:   37 of   39 MB written (fifo  99%) [buf  98%]  32.9x.
Track 09:   38 of   39 MB written (fifo  99%) [buf  98%]  31.9x.
Track 09:   39 of   39 MB written (fifo  99%) [buf  98%]  32.9x.
Track 09: Total bytes read/written: 40995360/40995360 (17430 sectors).
Starting new track at sector: 168345
Track 10:    0 of   39 MB written.
Track 10:    1 of   39 MB written (fifo  99%) [buf  98%]   2.7x.
Track 10:    2 of   39 MB written (fifo 100%) [buf  98%]  32.9x.
Track 10:    3 of   39 MB written (fifo 100%) [buf  98%]  34.0x.
Track 10:    4 of   39 MB written (fifo  99%) [buf  98%]  32.9x.
Track 10:    5 of   39 MB written (fifo  99%) [buf  98%]  33.9x.
Track 10:    6 of   39 MB written (fifo 100%) [buf  98%]  32.8x.
Track 10:    7 of   39 MB written (fifo  99%) [buf  98%]  33.9x.
Track 10:    8 of   39 MB written (fifo 100%) [buf  98%]  32.8x.
Track 10:    9 of   39 MB written (fifo  99%) [buf  98%]  33.8x.
Track 10:   10 of   39 MB written (fifo  99%) [buf  98%]  32.7x.
Track 10:   11 of   39 MB written (fifo  99%) [buf  98%]  33.7x.
Track 10:   12 of   39 MB written (fifo 100%) [buf  98%]  32.7x.
Track 10:   13 of   39 MB written (fifo  99%) [buf  98%]  33.7x.
Track 10:   14 of   39 MB written (fifo  99%) [buf  98%]  32.7x.
Track 10:   15 of   39 MB written (fifo  99%) [buf  98%]  33.7x.
Track 10:   16 of   39 MB written (fifo  99%) [buf  98%]  32.6x.
Track 10:   17 of   39 MB written (fifo 100%) [buf  98%]  33.6x.
Track 10:   18 of   39 MB written (fifo  99%) [buf  98%]  32.6x.
Track 10:   19 of   39 MB written (fifo  99%) [buf  98%]  33.6x.
Track 10:   20 of   39 MB written (fifo  99%) [buf  98%]  32.5x.
Track 10:   21 of   39 MB written (fifo 100%) [buf  98%]  33.6x.
Track 10:   22 of   39 MB written (fifo  99%) [buf  98%]  32.4x.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 02 B9 77 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 3.501s timeout 40s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 24004512 bytes
Writing  time:  120.077s
Average write speed  40.3x.
Min drive buffer fill was 88%
Fixating...
WARNING: Some drives don't like fixation in dummy mode.
Fixating time:    0.006s
BURN-Free was never needed.
/usr/bin/wodim: fifo had 6760 puts and 6569 gets.
/usr/bin/wodim: fifo was 0 times empty and 3441 times full, min fill was 93%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=16 -tao -dummy driveropts=burnfree -eject -overburn -useinfo -audio /tmp/kde-echo/k3b_audio_1_01.inf /tmp/kde-echo/k3b_audio_1_02.inf /tmp/kde-echo/k3b_audio_1_03.inf /tmp/kde-echo/k3b_audio_1_04.inf /tmp/kde-echo/k3b_audio_1_05.inf /tmp/kde-echo/k3b_audio_1_06.inf /tmp/kde-echo/k3b_audio_1_07.inf /tmp/kde-echo/k3b_audio_1_08.inf /tmp/kde-echo/k3b_audio_1_09.inf /tmp/kde-echo/k3b_audio_1_10.inf /tmp/kde-echo/k3b_audio_1_11.inf /tmp/kde-echo/k3b_audio_1_12.inf /tmp/kde-echo/k3b_audio_1_13.inf /tmp/kde-echo/k3b_audio_1_14.inf /tmp/kde-echo/k3b_audio_1_15.inf /tmp/kde-echo/k3b_audio_1_16.inf /tmp/kde-echo/k3b_audio_1_17.inf /tmp/kde-echo/k3b_audio_1_18.inf 

```

If anybody can suggest a solution, I'd be most grateful.  And if any further info is required, I'd naturally provide it.

---

### Post by blueridgedog on 2009-01-21
This:

```
Sense Key: 0x3 Medium Error, Segment 0
```

Implies it might be a bad disk or a batch of them.  Try a different brand (if you have some of another type) or slower write speeds.

---

### Post by Joe Soap on 2009-01-22
Thanks for the response.

I tried the burn on a different machine, also running Intrepid and it worked.  The differences between the two machines are:

1.  DVD writer     -  CD writer
2.  Min speed 16x  -  Min speed 8x

I used the same disk on both machines - did a simulation on the first machine and it failed.  It worked on the second machine and then I burned it successfully.

SO what's the bottomline here?  That I cannot use K3b on my one PC?

---

### Post by blueridgedog on 2009-01-22
Interesting.  If you are a system building and don't mind swapping a bit of hardware, it would be interesting to see if putting the other drive in the offending machine (if just temporarily, would change the picture.  What was the error on the simulation?  Can you burn a disk with Brasero?

---

### Post by Joe Soap on 2009-01-22
Nah, I have loads of problems with dust where I am and the "offending" :) PC is in a pristine condition, so I'll be leaving my grubby mitts off it.

The error on the simulation was the "code 254" as shown in the first mail.  

Brasero also didn't want to play ball - it kept giving a segmentation fault.  Which reminds me - the drive on which the files to be burned were stored, is a fat32 drive.  Does that matter?

---

### Post by Joe Soap on 2009-03-27
***  bumpity ***

Two months later and I'm still getting the same error :(

Googling does not give any answers...

Is there anybody out there who can help?

---

### Post by mikechant on 2009-03-27
Are you always burning the same track when it fails, if so does it always fail at the same point?
In that case it could be a that the track file is corrupt.

If not, the fact that Brasero fails as well might indicate a hardware problem with the CD writer.

Incidentally the fact that the files you are writing are on a FAT32 partition shouldn't matter.

---

### Post by Joe Soap on 2009-03-29
> **mikechant said:**
> Are you always burning the same track when it fails, if so does it always fail at the same point?
In that case it could be a that the track file is corrupt.

No, this error happens whenever I try to burn a cd.

It does not appear to be a hardwar problem, because I can burn ISO images from the command line, using growisofs.

---


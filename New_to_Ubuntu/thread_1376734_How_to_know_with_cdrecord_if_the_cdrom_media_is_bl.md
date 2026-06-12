---
title: "How to know with cdrecord if the cdrom media is blank or already burnt?"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-01-09
Hello, 

I would like to know distant whether I can burn on the distant pc. I use cdrecord for that usually.
 
**How to know with cdrecord if the cdrom media is blank or already burnt?**
 
```
cdrecord -scanbus
``` is not giving any information about the cdrom media, and man cdrecord is of no info about it. 

Best regards

---

### Post by frenchn00b on 2010-01-10
I guess that wodim can do the job, but it is not written in man pages either.

---

### Post by frenchn00b on 2010-01-11
SOLVED 
 
It works to get the informations of the media: 
with 

**[COLOR="Red"]    # cdrecord  -atip[/COLOR]**
    Device was not specified. Trying to find an appropriate drive...
    Detected CD-R drive: /dev/cdrw
    Using /dev/cdrom of unknown capabilities
    Error trying to open /dev/cdrom exclusively (Device or resource busy)... retrying in 1 second.
    Device type    : Removable CD-ROM
    Version        : 0
    Response Format: 2
    Capabilities   :
    Vendor_info    : 'TOSHIBA '
    Identification : 'DVD-ROM SD-R6112'
    Revision       : '1332'
    Device seems to be: Generic mmc2 DVD-R/DVD-RW.
    Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
    Driver flags   : MMC-3 SWABAUDIO BURNFREE
    Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
    ATIP info from disk:
      Indicated writing power: 5
      Is not unrestricted
      Is not erasable
      Disk sub type: Medium Type A, high Beta category (A+) (3)
      ATIP start of lead in:  -11634 (97:26/66)
      ATIP start of lead out: 359846 (79:59/71)
    Disk type:    Short strategy type (Phthalocyanine or similar)
    Manuf. index: 3
    Manufacturer: CMC Magnetics Corporation

---


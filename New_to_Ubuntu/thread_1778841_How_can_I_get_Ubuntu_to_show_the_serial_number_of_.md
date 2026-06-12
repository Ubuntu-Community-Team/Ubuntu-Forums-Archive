---
title: "How can I get Ubuntu to show the serial number of a drive?"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by adhoclobster on 2011-06-09
Wiping hard drives (SATA and IDE) is part of my job. Most of the time we use DBAN ([http://www.dban.org/](http://www.dban.org/)). What's nice about DBAN 2.2.6 is that it lists the serial number of the drive(s) upon finishing whether successful or failed. This is necessary in my office, because every wipe must be confirmed and signed off on by a witness other than myself. They can check the serial number listed by DBAN against the one on the physical drive to acheive absolute assurance that the drive plugged in is the one that was just been wiped (or failed to wipe). Recently we've been exploring the idea of using either Knoppix or Ubuntu to wipe drives. I use "shred -vfz -n 7" to replicate DBAN's DOD standard wipe. What can I use in the Linux terminal to list the serial number of the drive that's just been wiped?

---

### Post by Irony on 2011-06-09
System > Administration > Disk Utility

---

### Post by adhoclobster on 2011-06-09
> **Irony said:**
> System > Administration > Disk Utility
 
Nothing shows up for serial number.  It's just blank.
 
Also, I'd like to point out that it's not simply a matter of displaying a serial number; it's a matter of displaying the serial number of a drive whilst or DIRECTLY, IMMEDIATELY after being shredded. That's the whole point of the S/N; verification.
 
These same drives display serial numbers in DBAN every single time without fail. When I try "hdparm -i" or "hdparm -I" I get an error in the Linux terminal every single time without fail. SG_IO: bad/missing sense data, sb[]: . . .

---

### Post by Irony on 2011-06-09
```
sudo sginfo -s /dev/sda 
```?

---

### Post by Pazit on 2011-06-09
```
sudo lshw
```

---

### Post by sanderj on 2011-06-09
Both hdparm and Disk Utility work for me:

```

sander@netbook:~$ sudo hdparm -i /dev/sda

/dev/sda:

 Model=WDC WD1600BEVT-22ZCT0, FwRev=11.01A11, SerialNo=WD-WXE509V16360
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=312581808
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

sander@netbook:~$

```

---


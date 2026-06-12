---
title: "Bizzare CD Problem."
date: 2011-04-27
forum: New to Ubuntu
---

### Post by zozza on 2011-04-27
Hello,

I put a blank CD (Verbatim CD-R) into my external CD drive using 10.04 LTS.  

Dmesg shows:

[  255.950512] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  255.950527] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  255.950542] sr 3:0:0:0: [sr0] Add. Sense: Logical block address out of range
[  255.950558] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  255.950589] end_request: I/O error, dev sr0, sector 0

When I go to /media there are no directories that could be the CD-ROM.

I then went into XP.  Windows Explorer could see the blank CD.  I then wrote to it.

I then went back into Ubuntu.  Now when I put the CD into the external drive Dmesg shows:

[97.594505] ISO 9660 Extensions: Microsoft Joliet Level 3
[97.674629] ISO 9660 Extensions: RRIP_1991A

When I go to /media I see the name of the CD.  

Why will XP and Ubuntu see the CD with information on it but only XP can see the blank CD?

Any ideas?  Thanks.

---

### Post by zozza on 2011-04-29
bump...!

---


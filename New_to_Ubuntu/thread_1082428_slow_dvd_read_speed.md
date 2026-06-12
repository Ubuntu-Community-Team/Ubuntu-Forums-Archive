---
title: "slow dvd read speed"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by swong on 2009-02-27
I switched to Ubuntu 8.10 64-bit about 2 months ago (previously using Windows XP) and am very happy with it.  It was only until recently that I needed to make a DVD copy, and this is when I discovered that performing a 1:1 copy takes an absolute age to just read the disc (~30 mins).  In Windows, reading discs was fast (~5 mins).

After reading some forum posts it seems the most likely culprit is that DMA must be enabled on the drive, but I think it already is.  Pls see the output of the 'dmesg' and 'hdparm' commands below (I hope these are the correct commands to check DMA).  In addition, a DVD movie disc has no problem playing on my computer, i.e. no stuttering playback.

I have a Benq 1640 DVD writer, set as master on secondary IDE interface (separate from my hard disk).

$ dmesg | grep DMA
[    4.760488] ata6.00: ATAPI: BENQ    DVD DD DW1640, BSRB, max UDMA/33
[    4.776436] ata6.00: configured for UDMA/33

$ hdparm -i /dev/scd0

/dev/scd0:

 Model=BENQ    DVD DD DW1640                   , FwRev=BSRB    , SerialNo=9JB5U150H452121550SP
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no

 * signifies the current active mode


Any help appreciated.  (I would hate to switch back to Windows just for this one task)  Thanks!

---

### Post by mc4man on 2009-02-27
I have the same drive (sadly showing age, may need to be replaced, though it still 'reads' fast.
What you posted is fine, exactly what you'd expect to see.

Some factors in 'rip' speed may be the method your using and or the media your ripping. (both unmentioned

Here's a screenshot showing a graph of the benq 'ripping' a dvd movie. (aborted slightly after max. speed reached, would have finished at around 5.4x


So it may prove useful to post your method and the type/name of source material

---

### Post by swong on 2009-02-28
Thank you mc4man, your diagnosis was spot on.  I really should have tried another disc for comparison before posting.

I had another Linux distro burned on DVD recently using Taiyo Yuden DVD-R (media id TYG03).  I used Brasero to convert this to an iso, and it took around ~8 mins which is acceptable.  Brasero does not give me the average DVD read speed though.

The earlier problem disc I used before does not have any media id, so I guess it was of dubious quality, hence the slow read speed.

---


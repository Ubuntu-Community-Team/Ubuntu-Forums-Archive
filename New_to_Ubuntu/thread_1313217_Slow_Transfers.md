---
title: "Slow Transfers"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by malahavock on 2009-11-03
I am wondering why my computer takes so long to move or burn a file? I know it is not necessarily my computer, it is homemade with a AMD 3200+ 64 processor and 2 gig of ram. It is a dual boot and I do not have this problem with windows (but I don't want to use that). I want to use Ubuntu as my primary OS but this is driving me crazy. 
The main problem is that when I move from my internal HD to my external usb HD it only runs at about 6 mbps and completely takes over my computer so that I can't do anything else. 
Burning does the same thing. I use Gnome baker because it was faster than 
Brasero with less problems, but it is still really slow (up to an hour for a standard 4.7 Gig dvd)
Any help would be greatly appreciated.

---

### Post by jasonab on 2009-11-04
Not sure this will be of any help but check that DMA is enabled for your both your hard disc and dvd burner using the hdparm command.

> sudo hdparm -i /dev/sr0
[sudo] password for jason: 

/dev/sr0:

 Model=VBOX, FwRev=1.0, SerialNo=VB2-01700376
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=DualPortCache, BuffSize=256kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5 udma6 
 AdvancedPM=no
 Drive conforms to: unknown:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode




Replace sr0 with the device you are quering. If it is enabled read [here.]("http://ubuntuforums.org/showthread.php?t=1142852")
As for the slow copying, if the dma is fine then try the following: when copying to the external drive, open a terminal and type top to check the cpu usage. I somtimes experience a problem with CPU usage when copying to an NTFS partition (can't remember the process name).

---

### Post by 3rdalbum on 2009-11-04
Writing to an NTFS hard disk will be very slow and CPU-intensive, because the people developing the NTFS writing support want to get it all working bug-free before they start optimizing the code.

---


---
title: "a game on wine wants to change dma?"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by rgbargee on 2010-08-04
I have just installed Star Wars republic commando through wine, installation seemed to go fine but running the program i came to a dead end for me.

An error message comes up saying i should insert an original disc and not a backup? and refers me to the securom dot com web site. Well it is the original disc i just entered the ley from the manual to verify this but it is still complaining.

Securom says

**You are trying to start a copy-protected application which requires  the original disc to be in the CD/DVD-ROM drive. Please check to make  sure your disc is an original.**

If this message  occurs, although you are using the original disc, please check if the  correct communication mode is being used with your drive.  Please check if the DMA mode is enabled by using the Device Manager 

[LIST=1]
[*]Open the Device Manager.
[*]Double-click IDE ATA/ATAPI Controllers to display the list of controllers and channels.
[*]Right-click the icon for the channel to which your CD/DVD drive  is connected, select Properties, and then click the Advanced Settings  tab.
[*]In the Current Transfer Mode drop-down box, select "DMA if  Available" if the current setting is "PIO Only." If the drop-down box  already shows "DMA if Available" but the current transfer mode is PIO,  then you must toggle the settings. That is:
[LIST]
[*]Change the selection from "DMA if available" to PIO only, and click OK.
[*]Then repeat the steps above to change the selection to DMA if available.
[/LIST]
 
[/LIST]


Searching around i have found how to dump my drives settings and came up with this

/dev/sda:

 Model=ST3160215AS, FwRev=3.AAC, SerialNo=9RA1LBKN
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=312581808
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode
Soooo now i need help, this says im on udma6 i think but securom say i should be on dma im afraid i am in over my head now The next step anyone? please?

---

### Post by mc4man on 2010-08-04
Most likely relevant - post 6
[http://ubuntuforums.org/showthread.php?p=9531052](http://ubuntuforums.org/showthread.php?p=9531052)

> Searching around i have found how to dump my drives settings and came up with this
/dev/sda:
That's your hard drive, not cdrom drive. Really a moot point, the issue isn't dma

---

### Post by marshmallow1304 on 2010-08-05
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7255](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7255)

Three of the five reports say specifically that a no-CD patch is required.  Using such a patch may be illegal in your area and is not encouraged on this forum, so find and use one at your own risk.

---


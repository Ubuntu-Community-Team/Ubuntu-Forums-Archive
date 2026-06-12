---
title: "DVD burn speed doesn't go above 0.6x"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by Incredible.Pie on 2009-04-05
My DVDs burn very slowly. I'm lucky if my discs burn above 0.3x. This means it takes hours to burn a standard 4.4 Gig DVD. The max speed of the external drive is 16x, and the max speed of the DVDs is 16x as well. I'm using Jaunty 9.04 beta, but this problem is also in 8.10 and 8.04. Burning used to be fine in earlier version of Ubuntu, though (I'm not sure which, specifically, but definitely in the 7.x versions).

---

### Post by logos34 on 2009-04-05
sounds like it's a problem with the usb controller or else the drive is running in super-slow PIO mode

---

### Post by hessczoo on 2009-04-05
Hmm. I would say it is something to do with your USB Controller. I don't know much about configuring them so i can't help too much.

---

### Post by Incredible.Pie on 2009-04-05
> **logos34 said:**
> sounds like it's a problem with the usb controller or else the drive is running in super-slow PIO mode

Any way I can tell whether or not it's running in PIO mode so we can at least rule that out?

---

### Post by logos34 on 2009-04-05
sudo hdparm -i /dev/scd0

or scd1, or whatever the usb drive is recognized as

sudo lshw -C disk

---

### Post by Incredible.Pie on 2009-04-05
sudo lshw -C disk produces this for the drive I'm looking at:

```
  *-cdrom
       description: DVD writer
       product: DVD-RW  DVR-111D
       vendor: PIONEER
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrom1
       logical name: /dev/cdrw
       logical name: /dev/cdrw1
       logical name: /dev/dvd
       logical name: /dev/dvd1
       logical name: /dev/dvdrw
       logical name: /dev/dvdrw1
       logical name: /dev/scd2
       logical name: /dev/sr2
       version: 1.06
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: status=nodisc

```

and for some reason, sudo hdparm -i /dev/scd2 produces:

```
/dev/scd2:
 HDIO_GET_IDENTITY failed: Invalid argument

```

But hdparm -I /dev/scd2 produces:

```
/dev/scd2:
 HDIO_DRIVE_CMD(identify) failed: Input/output error

```

---

### Post by logos34 on 2009-04-05
maybe hdparm has issues with usb, but here's what my internal optical drive shows:

> $ sudo hdparm -i /dev/scd0

/dev/scd0:

 Model=ASUS    DRW-1608P2                      , FwRev=1.41    , SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=13395, BuffSize=64kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-2,3,4,5

 * signifies the current active mode

come to think of it, hdparm might work only with ide devices

---

### Post by Incredible.Pie on 2009-04-06
That's what it looks like... my internal CDs (is that the right term?) can be read just fine.

So is there any other way I can pull info about this drive out?

---

### Post by Incredible.Pie on 2009-04-14
Just a bump/update: If I specify Brasero to burn at a certain speed (like 8.0x), it works fine. But If I want Brasero to run at anything higher, it automatically selects "Max Speed" from the options and burns at 0.6x. I guess that 8.0x speed is a pretty good speed, but it's not as fast as it could go. Can I do anything else now, or am I stuck with 8.0x?

---

### Post by logos34 on 2009-04-15
Hopefully someone has the answer...But I decided to check Brasero on my machine, and oddly enough reports burning speeds in the drop menu that are not supported by the media. i.e. my dvd+r discs support 4x,6x,8,12,16x, but Brasero lists odd numbers 

> 1 x (DVD)
3 x (DVD) 
5 x (DVD)

etc

up to 

15 x (DVD) 

but not 16x! (??)

If you're able to burn at 8x, hey, I'd be satisfied with that if I were you.  Burning at 16x increases the risk of coasters and/or data that fails verification, or even becomes unreadable later on. (happened to me.  I never burn faster than 12x, and usually 4x or 8x...I'd rather spend a few more minutes to get good, durable burns)


add:


However, you might try [growisofs in terminal]("http://www.yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html"), which should automatically burn at the highest (default) speed supported byt he media and drive unless otherwise specified:

growisofs -Z /dev/dvd -R -J /some/folder  (-->single/closed session)

or to start/continue multisession:

growisofs -M /dev/dvd -R -J /some/folder1 /some/folder2

etc.

If drive defaults to lower speed, not sure if the '-speed=N' option will work with high values.  (see link above and manpage for growisofs)

dvd+rw-mediainfo /dev/scd0

for dvd disc specs

but that's assuming the problem is with the burning app and its interaction with hardware, not with the usb controller or something else.

good luck

---

### Post by MakOwner on 2010-01-03
Bumping this thread.  

I have upgraded to 9.10 from 9.04.  
I installed on a fresh new hard drive, so I can swap back to my old installation at will.  Still have my 8.10 around somewhere too.

I could burn Single and Double layer DVDs in 8.10 at the max speed of the media and the drive.  I upgraded to 9.04 and had to select 6 or 8x to prevent creating coasters.  On 9.10 I can get at best 2x. 

I can go back to 9.04 and burn at 6x or 8x.  I go to 9.10 and I get 2X max with the message stating the "media doesn't support" burning at a higher rate.

This is on media from the same batch - on the single layer disks out of the same 100 count spindle.  
  
That said, searching on the forums I see a LOT of queries about burn speed issues.  I see everyone's first response is that it must be a hardware issue.  

Based on my transition back and forth between 9.04 and 9.10 here it ISN'T hardware.

I'm using k3b on both 9.04 and 9.10.

Anyone have any clue what the underlying cause is?


Edit:
So, the overall issue is years old and appears to be getting worse.

[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/149076?comments=all](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/149076?comments=all)


I have brand name media that is rated for 8x and yet I can at best get 2X out of it.

dvd+rw-mediainfo /dev/sr0
INQUIRY:                [PIONEER ][DVD-RW  DVR-111D][1.23]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         2Bh, DVD+R Double Layer
 Media ID:              CMC MAG/D02
 Current Write Speed:   2.4x1385=3324KB/s
 Write Speed #0:        2.4x1385=3324KB/s
 Speed Descriptor#0:    00/4173823 R@2.4x1385=3324KB/s W@2.4x1385=3324KB/s
READ DVD STRUCTURE[#0h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Legacy lead-out at:    2086912*2KB=4273995776
DVD+R DOUBLE LAYER BOUNDARY INFORMATION:
 L0 Data Zone Capacity: 2086912*2KB, can still be set
READ DISC INFORMATION:
 Disc status:           blank
 Number of Sessions:    1
 State of Last Session: empty
 "Next" Track:          1
 Number of Tracks:      1
READ TRACK INFORMATION[#1]:
 Track State:           blank
 Track Start Address:   0*2KB
 Next Writable Address: 0*2KB
 Free Blocks:           4173824*2KB
 Track Size:            4173824*2KB
 ROM Compatibility LBA: 242432
READ CAPACITY:          0*2048=0


I'm going to try switching back to cdrtools but based on the return from dvd+rw-mediainfo above, I don't have high hopes.

---


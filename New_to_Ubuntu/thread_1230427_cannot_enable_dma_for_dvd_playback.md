---
title: "cannot enable dma for dvd playback"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by uncibex on 2009-08-03
Hi!

I've been having problems with jumpy audio and video playback on dvds.  According to this site,
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)
I should enable dma to try to fix the problem.

When I ran this command,
```
karen@karen:~$ mount | egrep 'udf|iso9660'
```
I got this output
```
/dev/sr0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=karen)
```

so I ran this command,
```
sudo hdparm -d1 /dev/sr0
```
and got this:
```
/dev/sr0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

```

I searched around on google a bit longer to see what answers I could find, but I didn't find anything that I hadn't already read.

Here's some information I think might be useful, but let me know if there's anything else I should post:

```

karen@karen:~$ sudo hdparm -i /dev/sr0
[sudo] password for karen: 

/dev/sr0:

 Model=TSSTcorpCD/DVDW TS-L632M                , FwRev=0917    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 *mdma2 
 AdvancedPM=no

 * signifies the current active mode

```

and the version for hdparm is 8.9

I'd appreciate any ideas you have. Thanks!

---

### Post by LowSky on 2009-08-03
can you give your hardware specs..

Also are you running compiz?

have you installed libdvdcss2?

---

### Post by uncibex on 2009-08-04
Hardware specs:
HP DV2000
AMD Turion 64 x2
NVIDIA graphics card (driver version 180.44)
2GB RAM

..hopefully that will be enough

compiz is installed and running, but I only use it for the desktop effects option.  Is this something I'd be better off to uninstall?

And yes, libdvdcss2 is installed and is the newest version

---

### Post by wizard10000 on 2009-08-04
hdparm says DMA is enabled on the drive already.

---

### Post by uncibex on 2009-08-04
then is there another reason that I would be getting choppy video and audio playback that I'm missing?

---

### Post by wizard10000 on 2009-08-04
> **uncibex said:**
> then is there another reason that I would be getting choppy video and audio playback that I'm missing?

I'd open up system monitor while playing a few videos and see what's beating your machine up.  Can you give us some hardware specs?

---

### Post by uncibex on 2009-08-04
I'm not really seeing anything in particular that's using up an enormous amount of resources on my machine.  Other than the system monitor itself which is using about 15% of my resources, VLC is the only other thing running and it's only using about 20% on average.  It shoots up to 40% occasionally, but it doesn't even seem as though this is happening when the video speeds up.  Either way, the video and audio are choppy when the video is moving faster.  This doesn't happen with any other sort of video output on my computer (including hi def streaming videos) so I can't imagine that this is an issue with my graphics card. (?)

I posted some hardware specs in my first reply, if you need more, please tell me what you need/a command to get it easily.  I don't really know which information is necessary.

---

### Post by wizard10000 on 2009-08-04
> **uncibex said:**
> I'm not really seeing anything in particular that's using up an enormous amount of resources on my machine.  Other than the system monitor itself which is using about 15% of my resources, VLC is the only other thing running and it's only using about 20% on average.  It shoots up to 40% occasionally, but it doesn't even seem as though this is happening when the video speeds up.  Either way, the video and audio are choppy when the video is moving faster.  This doesn't happen with any other sort of video output on my computer (including hi def streaming videos) so I can't imagine that this is an issue with my graphics card. (?)

I posted some hardware specs in my first reply, if you need more, please tell me what you need/a command to get it easily.  I don't really know which information is necessary.

Ah.  I see the hardware specs, sorry  :)

I think this machine's got more than enough juice to play videos.  Hard drive is /dev/sda, yes?

Can you post the output of this command, please?

```
sudo hdparm -tT /dev/sda
```

---

### Post by uncibex on 2009-08-04
```
/dev/sda:
 Timing cached reads:   960 MB in  2.00 seconds = 480.11 MB/sec
 Timing buffered disk reads:  132 MB in  3.04 seconds =  43.35 MB/sec

```

---

### Post by wizard10000 on 2009-08-04
> **uncibex said:**
> ```
/dev/sda:
 Timing cached reads:   960 MB in  2.00 seconds = 480.11 MB/sec
 Timing buffered disk reads:  132 MB in  3.04 seconds =  43.35 MB/sec

```

Well, the problem ain't disk throughput  :)

I'm thinking the problem may be VLC.  Is that what you use to play mp3s as well?

---

### Post by uncibex on 2009-08-04
I don't generally speaking, but I'm playing an mp3 through it right now and not having any issues.  I also played a downloaded video through VLC and didn't have issues (even in full screen).  Any other ideas?

(Thanks for helping, btw!)

---

### Post by wizard10000 on 2009-08-04
> **uncibex said:**
> I don't generally speaking, but I'm playing an mp3 through it right now and not having any issues.  I also played a downloaded video through VLC and didn't have issues (even in full screen).  Any other ideas?

(Thanks for helping, btw!)

You're more than welcome.

Run the hdparm test on your DVD player - you'll need a DVD in the drive to do it but here's what I get (DVD burner is new, though) -

```
wizard@wizard-desktop:~$ sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   22678 MB in  2.00 seconds = 11351.35 MB/sec
 Timing buffered disk reads:   84 MB in  3.04 seconds =  27.65 MB/sec
wizard@wizard-desktop:~$ 
```

Also, are the choppy mp3s running from hard drive or optical disk?  Trying to nail down whether it's I/O or processor.

---

### Post by uncibex on 2009-08-04
Here's what I got from the DVD player:

```

/dev/sr0:
 Timing cached reads:   708 MB in  2.00 seconds = 353.74 MB/sec
 Timing buffered disk reads:    6 MB in  3.16 seconds =   1.90 MB/sec

```

and I played the mp3s earlier from the hard drive, but figured I'd burn a disk with some media on there so I could test it from the cd drive, and the burn failed - twice... so I'm wondering if it's a problem with the drive itself.

---

### Post by wizard10000 on 2009-08-04
> **uncibex said:**
> Here's what I got from the DVD player:

```

/dev/sr0:
 Timing cached reads:   708 MB in  2.00 seconds = 353.74 MB/sec
 Timing buffered disk reads:    6 MB in  3.16 seconds =   1.90 MB/sec

```

and I played the mp3s earlier from the hard drive, but figured I'd burn a disk with some media on there so I could test it from the cd drive, and the burn failed - twice... so I'm wondering if it's a problem with the drive itself.

Sure looks like it - and it looks like we've found your problem  :)

---

### Post by uncibex on 2009-08-04
Well, thanks again for the help!

---

### Post by BobvanderPoel on 2009-10-30
I've just upgraded to 9.10 and this thread is the closest I've seen to my problem. Choppy playback of DVDs. Both drives worked perfectly on 8.04, so I'm thinking it's not the drive ... I'm guessing some kind of setting is not right. Just looking at logs:

bob$ grep ATAPI dmesg
[    1.565232] ata6.00: ATAPI: SONY    DVD RW DRU-800A, KY01, max UDMA/66
[    1.565256] ata6.01: ATAPI: _NEC DV-5800A, 1.0A, max UDMA/33

The drives show up as /dev/sr0 and /dev/sr1 ... used to be /dev/hdxx don't know that the srX stuff is.

Throughput seems slow.

sudo hdparm -tT /dev/sr0
[sudo] password for bob: 

/dev/sr0:
 Timing cached reads:   976 MB in  2.00 seconds = 487.71 MB/sec
 Timing buffered disk reads:   12 MB in  3.53 seconds =   3.40 MB/sec

Any ideas? BTW, playback does work ... it's not a matter of installing css, etc. libs. Playback is just jerky, stops, and crashes :(

Thanks!

---

### Post by Velaru on 2009-11-09
I'm also having the same issues with 9.10

/dev/sr0:
 Timing cached reads:   434 MB in  2.00 seconds = 216.52 MB/sec
 Timing buffered disk reads:    8 MB in  3.08 seconds =   2.60 MB/sec

considering I upgraded to 9.10 today from 9.04. in 9.04 DVD play back was fine and peachy. nots its sluggish and not watchable, and it seems to be that the DVD drive isnt spinning up at all when it begins to try to play the dvd. So im gonna switch back to 9.04 and see what happens.

---


---
title: "k3b issues. Why do I even do this to myself."
date: 2011-08-03
forum: New to Ubuntu
---

### Post by Baniita on 2011-08-03
So, after checking other forums and trying everything I know that is relevant, I found myself lost in all the jargon and so here I am. :T I'm in a rush, so fast help would be highly appreciated. C:

I finally figured out how to properly format my DVD+RW until it stopped giving me the "cannot umount" BS.

But that didn't stop the latter BS:
x Unable to fixate the disk.
x The disk might still be readable.

Debugging output:
```
Devices
-----------------------
hp CDDVDW TS-U633F HH05 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

System
-----------------------
K3b Version: 2.0.1
KDE Version: 4.5.5 (KDE 4.5.5)
QT Version:  4.7.0
Kernel:      2.6.35-22-generic

Used versions
-----------------------
cdrecord: 1.1.10

cdrecord
-----------------------
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.10
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'hp      '
Identification : 'CDDVDW TS-U633F '
Revision       : 'HH05'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0014 (DVD-RW sequential recording)
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) (current)
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1406976 = 1374 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 5540 KB/s
Track 01: data     2 MB        
Total size:        3 MB (00:18.14) = 1361 sectors
Lout start:        3 MB (00:20/11) = 1361 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 2298496 Blocks current: 2298496 Blocks remaining: 2297135
Starting to write CD/DVD at speed   4.0 in real SAO mode for single session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Starting new track at sector: 0
Track 01:    0 of    2 MB written.
Track 01:    1 of    2 MB written (fifo 100%) [buf  68%]   0.0x.
Track 01:    2 of    2 MB written (fifo 100%) [buf 100%]   3.6x.
Track 01: Total bytes read/written: 2787328/2787328 (1361 sectors).
Writing  time:   42.489s
Average write speed   0.0x.
Min drive buffer fill was 100%
Fixating...
Errno: 5 (Input/output error), flush cache scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 03 00 00
Sense Key: 0x0 No Additional Sense, Segment 11
Sense Code: 0x00 Qual 0x03 (setmark detected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 200.656s timeout 200s
/usr/bin/wodim: Cannot fixate disk.
Trouble flushing the cache
Fixating time:  200.656s
/usr/bin/wodim: fifo had 44 puts and 44 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=4 -sao driveropts=burnfree -data -tsize=1361s -

```

Ubuntu, I am so upset at you and me right now. I'm eyeing those divorce papers. It's not you, it's just that I feel like I don't even know you anymore.

Ubuntu: "Will you stop with the soap opera melodrama?"

"But it's all I know! I never even knew you at all!! I came to you when Windows 7 left me and--"

"Don't talk about him!! He betrayed us and--

**YEAH. I'M GOING DELUSIONAL. FAST SIGN THAT I NEED INSTENT HALP.**

---

### Post by Baniita on 2011-08-03
Oh, great. It's giving me the "cannot umount" bullyshet again. = A=)"

---

### Post by Baniita on 2011-08-03
B-B-Bu-Bump-Bu-BUMP--

That was not the sound of a bump, but rather a heart attack.

Damn you, my sodium addiction!

---

### Post by jtarin on 2011-08-03
I have found other earlier posts of yours of having issues with K3B. 
Might I suggest an alternative? I have had issues myself with K3B and have found **Gnome Baker** to be a more suitable burner. It's in the repositories.

---

### Post by Baniita on 2011-08-03
Actually, /every/ alternative hates me. k3b is the most reliable (surprisingly) for me. e ___e)" I'll try out Brasero again, since I already have that installed....

I'll try gnome baker next.

---

### Post by Baniita on 2011-08-03
...And this is why I hate Brasero. It's been on "finalizing" for forever.

It worked *supposedly*.

I have it burnt down now, but I'd still like to figure out the problem with K3B. I've had domestic violence issues with Brasero.

---

### Post by jtarin on 2011-08-03
I have had my issues with both of these and have moved on.....you should find something that is more amenable to your system and temperament.

---

### Post by alphacrucis2 on 2011-08-03
Another thing to try is ditching the Debian CDRkit stuff and install CDRTools instead. You may find that k3b and the other burning software work a lot better. Seems to very much depend on particular hardware. You can install the CDRTools via this PPA:

[https://launchpad.net/~brandonsnider/+archive/cdrtools]("https://launchpad.net/~brandonsnider/+archive/cdrtools")

If it doesn't work you can always flush it out and go back to the Debian stuff.

---

### Post by jtarin on 2011-08-03
> **alphacrucis2 said:**
> Another thing to try is ditching the Debian CDRkit stuff and install CDRTools instead. I completely overlooked that. +1 #-o

---

### Post by halibaitor on 2011-08-03
I've had domestic violence issues with both Brasero and K3B. :(

My solution was to install WINE and then use ImgBurn...  No more problems...  :D

YMMV

---

### Post by Baniita on 2011-08-03
1. COMPLETELY OVERLOOKED WINE. /Slaps self.

2. CDRtools... Sounds good! Thanks, I'll go for that. <3

---


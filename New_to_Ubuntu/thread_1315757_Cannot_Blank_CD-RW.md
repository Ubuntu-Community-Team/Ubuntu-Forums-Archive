---
title: "Cannot Blank CD-RW"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by coldReactive on 2009-11-05
My IBM T41 Laptop gives the following output:

```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1848)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_BMR82U.bin toc = none
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_G4S82U.bin toc = none
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_set_output_size_for_current_track
BraseroChecksumImage stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage There is a checksum already 0
BraseroWodim called brasero_job_get_action
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_get_device
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_set_current_action
BraseroWodim got varg:
	wodim
	-v
	dev=/dev/sr0
	blank=fast
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/sr0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsibus: -2 target: -2 lun: -2
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Linux sg driver version: 3.5.27
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Wodim version: 1.1.9
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: SCSI buffer size: 64512
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: communication breaks or freezes immediately after that.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: TOC Type: 1 = CD-ROM
BraseroWodim stdout: Device type    : Removable CD-ROM
BraseroWodim stdout: Version        : 5
BraseroWodim stdout: Response Format: 2
BraseroWodim stdout: Capabilities   : 
BraseroWodim stdout: Vendor_info    : 'MATSHITA'
BraseroWodim stdout: Identification : 'UJDA755zDVD/CDRW'
BraseroWodim stdout: Revision       : '1.20'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-ROM.
BraseroWodim stdout: Current: 0x000A (CD-RW)
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) (current)
BraseroWodim stdout: Profile: 0x0009 (CD-R) 
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
BraseroWodim stdout: Drive buf size : 1433600 = 1400 KB
BraseroWodim stderr: Speed set to 1411 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 3
BraseroWodim stdout:   Reference speed: 6
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is erasable
BraseroWodim stdout:   Disk sub type: High speed Rewritable (CAV) media (1)
BraseroWodim stdout:   ATIP start of lead in:  -11745 (97:25/30)
BraseroWodim stdout:   ATIP start of lead out: 359848 (79:59/73)
BraseroWodim stdout:   1T speed low:  4 1T speed high: 10
BraseroWodim stdout:   2T speed low:  4 2T speed high:  0 (reserved val  6)
BraseroWodim stdout:   power mult factor: 1 5
BraseroWodim stdout:   recommended erase/write power: 5
BraseroWodim stdout:   A1 values: 24 1A D8
BraseroWodim stdout:   A2 values: 26 B2 4A
BraseroWodim stdout: Disk type:    Phase change
BraseroWodim stdout: Manuf. index: 40
BraseroWodim stdout: Manufacturer: INFODISC Technology Co., Ltd.
BraseroWodim stdout: Starting to write CD/DVD at speed   8.0 in real BLANK mode for single session.
BraseroWodim stdout: Last chance to quit, starting real write in    4 seconds.
BraseroWodim called brasero_job_set_dangerous
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    3 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    2 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    1 seconds.
BraseroWodim stdout:    0 seconds. Operation starts.
BraseroWodim stdout: Performing OPC...
BraseroWodim stderr: wodim: OPC failed.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Blanking PMA, TOC, pregap
BraseroWodim stderr: Errno: 5 (Input/output error), blank unit scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  A1 01 00 00 00 00 00 00 00 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x3 Medium Error, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 2.144s timeout 9600s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Cannot blank disk, aborting.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Some drives do not support all blank types.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Try again with wodim blank=all.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: HUP
BraseroWodim process finished with status 255
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroWodim stopping
BraseroWodim got killed
Session error : unknown (brasero_burn_record brasero-burn.c:2811)
```

wodim blank=all gives this output:
```
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
Error trying to open /dev/cdrom exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrom exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrom exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrom exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrom exclusively (Device or resource busy)... giving up.
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.
```

and wodim --devices AND wodim -scanbus gives:
```
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.
```

---

### Post by philinux on 2009-11-05
I think brasero may have a bug.

I use k3b to do this with no errors.

---

### Post by jimmy the saint on 2009-11-05
Last night I got a new version of Brasero pushed down through updates that supposedly fixed a bug with burning CD's.  If you haven't updated in the last 20 hours or so, do so and try again.

---

### Post by Artemis3 on 2009-11-05
My suggest: turn off the machine, turn it on then try wodim again. My experience with Brasero, when it fails, it hoses the drive. Which is why i decided to switch to GnomeBaker (which uses wodim).

---

### Post by coldReactive on 2009-11-05
> **philinux said:**
> I think brasero may have a bug.

I use k3b to do this with no errors.

k3b couldn't blank it either, gave the following errors:

OPC failed. Probably the writer does not like the medium.
Blanking error.
Sorry, no error handling yet.

Even though the drive is CD-RW Capable as it says right on the drive.

---

### Post by coldReactive on 2009-11-05
restarted machine, tried wodim again:

```
ian@ian-laptop:~$ wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'	rwrw-- : 'MATSHITA' 'UJDA755zDVD/CDRW'
-------------------------------------------------------------------------
ian@ian-laptop:~$ sudo wodim blank=all
[sudo] password for ian: 
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identification : 'UJDA755zDVD/CDRW'
Revision       : '1.20'
Device seems to be: Generic mmc2 DVD-ROM.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
Speed set to 1411 KB/s
Starting to write CD/DVD at speed   8.0 in real BLANK mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
wodim: OPC failed.
Errno: 5 (Input/output error), blank unit scsi sendcmd: no error
CDB:  A1 00 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 1.933s timeout 9600s
wodim: Cannot blank disk, aborting.
```

---

### Post by philinux on 2009-11-05
I remember I had a problem with a dvd that would not overwrite and I used this. Maybe it might work on a cdrw

growisofs -Z /dev/dvd=/dev/zero

Change dvd to cdrom

Or you could have a coaster.

---

### Post by coldReactive on 2009-11-05
> **philinux said:**
> I remember I had a problem with a dvd that would not overwrite and I used this. Maybe it might work on a cdrw

growisofs -Z /dev/dvd=/dev/zero

Change dvd to cdrom

Outputs:

```
ian@ian-laptop:~$ growisofs -Z /dev/cdrom=/dev/zero
:-( /dev/cdrom: media is not recognized as recordable DVD: A
```

---

### Post by philinux on 2009-11-05
> **coldReactive said:**
> Outputs:

```
ian@ian-laptop:~$ growisofs -Z /dev/cdrom=/dev/zero
:-( /dev/cdrom: media is not recognized as recordable DVD: A
```

My mistake for not checking man growisofs. There must be something similar for cdrws.

---

### Post by KeLa on 2009-11-05
Try to erase it in different computer (even in Win machine) if you still get error the media is gone to bit heaven. I had that kind of problems in past and always media was dead not the hw or sw.

---

### Post by philinux on 2009-11-05
I've got a couple of cdrw coasters somewhere that wont play ball. I'll dig em out and try this approach.

[http://www.cyberciti.biz/faq/howto-linux-format-cdrw-dvdrw/](http://www.cyberciti.biz/faq/howto-linux-format-cdrw-dvdrw/)

---

### Post by coldReactive on 2009-11-05
It won't even burn a blank cd-rw, yes, I have the updates from the update manager.

K3B says this:
```
Devices
-----------------------
MATSHITA UJDA755zDVD/CDRW 1.20 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM) [DVD-ROM, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R96R] [%7]

System
-----------------------
K3b Version: 1.68.0
KDE Version: 4.3.2 (KDE 4.3.2)
QT Version:  4.5.2
Kernel:      2.6.31-14-generic

Used versions
-----------------------
cdrecord: 1.1.9

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.9
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identification : 'UJDA755zDVD/CDRW'
Revision       : '1.20'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x000A (CD-RW)
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) (current)
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
Drive buf size : 1433600 = 1400 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 1411 KB/s
Track 01: data   118 MB        
Total size:      135 MB (13:28.38) = 60629 sectors
Lout start:      136 MB (13:30/29) = 60629 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 3
  Reference speed: 6
  Is not unrestricted
  Is erasable
  Disk sub type: High speed Rewritable (CAV) media (1)
  ATIP start of lead in:  -11745 (97:25/30)
  ATIP start of lead out: 359848 (79:59/73)
  1T speed low:  4 1T speed high: 10
  2T speed low:  4 2T speed high:  0 (reserved val  6)
  power mult factor: 1 5
  recommended erase/write power: 5
  A1 values: 24 1A D8
  A2 values: 26 B2 4A
Disk type:    Phase change
Manuf. index: 40
Manufacturer: INFODISC Technology Co., Ltd.
Blocks total: 359848 Blocks current: 359848 Blocks remaining: 299219
Starting to write CD/DVD at speed   8.0 in real SAO mode for single session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 4.410s timeout 200s
/usr/bin/wodim: OPC failed.
Writing  time:    4.455s
/usr/bin/wodim: fifo had 192 puts and 0 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=8 -sao driveropts=burnfree -data -tsize=60629s -
```

---

### Post by coldReactive on 2009-11-05
And no, it can't even burn a blank CD-R.

---

### Post by coldReactive on 2009-11-05
I'm guessing no one's going to come back and reply, huh.

Meaning, I'm screwed.

---

### Post by theozzlives on 2009-11-05
> **coldReactive said:**
> And no, it can't even burn a blank CD-R.

If your drive won't burn or blank anything, it's probably the drive. They don't last forever.

---

### Post by ikisham on 2009-11-05
I put the title of this thread in Google and found this forum ( [http://club.myce.com/f61/](http://club.myce.com/f61/) ). They discuss the hardware so maybe there's something you can do before just throwing the drive away.

Like disconnect the drive (with the computer off), connect again and see if it makes any difference or things alike.

---

### Post by coldReactive on 2009-11-05
Well, it seems my drive is faulty.

It can read CDs and CD-RWs (and can detect if they're blank) but it can't write to them. I haven't tried DVDs though.

How do I know this? Thankfully, I had my MULTIPASS TOSHIBA external DVD-+RW and CD-RW Drive, and it successfully blanked the problematic CD-RW.

*sighs* I can't return it  even though I just bought it this week, as-is sucks.

---

### Post by coldReactive on 2009-11-05
I also just updated the firmware to 1.24 from 1.20, but... alas, it still doesn't blank/burn.

---

### Post by Sz__G on 2010-07-28
I agree with KeLa. I have a CD-RW disk. I have erased it many times, everything was good. I always used K3B. On fine day, there was an error in the erase procedure. After this wrong erase, there was no computer which could write this disk again. I changed the disk. The problem disappeared.

I think, sometimes, this bug can be disk bug. This disk will be good for beermat.

---

### Post by Sz__G on 2010-07-28
Funny things happend. I didnt give up the disk. I tried burn again, but now I set the speed of the writing to 4x . And...it worked for me... the bug disappeared.

For you, I dont know... maybe...try to set the speed of the erase? Is it possible?

---

### Post by Iowan on 2010-07-28
OP's last post was 8 months ago - it's doubtful (s)he will benefit from your information, but thanks for contributing!

---


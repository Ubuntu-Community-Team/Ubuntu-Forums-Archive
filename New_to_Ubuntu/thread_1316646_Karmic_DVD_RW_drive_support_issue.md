---
title: "Karmic DVD_RW drive support issue?"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by helamsirrine on 2009-11-06
I am running 32 bit Karmic on a new Acer AMD AthlonIIx2 215 with a DVD-RW drive and I am getting an unknown fault trying to burn the Karmic ISO to a CD-R using Brasero. I am too ignorant to diagnose the problem from the fault log so I am posting it here. Please help.

brasero-session.log

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1799)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_BJXU2U.bin toc = none
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage Dummy operation, skipping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage There is a checksum already 0
BraseroWodim called brasero_job_get_action
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim got varg:
BraseroWodim deactivating
BraseroWodim called brasero_job_get_action
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_get_device
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_speed
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_fd_in
BraseroWodim called brasero_job_get_current_track
BraseroWodim called brasero_job_set_current_action
BraseroWodim got varg:
    wodim
    -v
    dev=/dev/sr0
    -dummy
    speed=40
    driveropts=burnfree
    fs=16m
    -data
    -nopad
    /home/helamsirrine/Desktop/ubuntu-9.10-desktop-i386.iso
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
BraseroWodim stderr: wodim: No write mode specified.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Asuming -tao mode.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Future versions of wodim may have different drive dependent defaults.
BraseroWodim called brasero_job_get_flags
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
BraseroWodim stdout: Driveropts: 'burnfree'
BraseroWodim stdout: Device type    : Removable CD-ROM
BraseroWodim stdout: Version        : 5
BraseroWodim stdout: Response Format: 2
BraseroWodim stdout: Capabilities   : 
BraseroWodim stdout: Vendor_info    : 'HL-DT-ST'
BraseroWodim stdout: Identification : 'DVDRAM GH41N    '
BraseroWodim stdout: Revision       : 'MN01'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x0012 (DVD-RAM) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0015 (DVD-R/DL sequential recording) 
BraseroWodim stdout: Profile: 0x0016 (DVD-R/DL layer jump recording) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Profile: 0x0002 (Removable disk) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
BraseroWodim stdout: Drive buf size : 1053696 = 1029 KB
BraseroWodim stdout: Drive DMA Speed: 15396 kB/s 87x CD 11x DVD
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 7057 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   689 MB        
BraseroWodim stdout: Total size:      792 MB (78:30.24) = 353268 sectors
BraseroWodim stdout: Lout start:      792 MB (78:32/18 ) = 353268 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 5
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is not erasable
BraseroWodim stdout:   Disk sub type: Medium Type A, high Beta category (A+) (3)
BraseroWodim stdout:   ATIP start of lead in:  -11634 (97:26/66)
BraseroWodim stdout:   ATIP start of lead out: 359846 (79:59/71)
BraseroWodim stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
BraseroWodim stdout: Manuf. index: 3
BraseroWodim stdout: Manufacturer: CMC Magnetics Corporation
BraseroWodim stdout: Blocks total: 359846 Blocks current: 359846 Blocks remaining: 6578
BraseroWodim stdout: Starting to write CD/DVD at speed  40.0 in dummy TAO mode for single session.
BraseroWodim stdout: Last chance to quit, starting dummy write in    4 seconds.
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
BraseroWodim stdout:    1 seconds.   0 seconds. Operation starts.
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stdout: 
BraseroWodim stdout: Track 01:    0 of  689 MB written.
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 00 00 02 0F 00 00 1F 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 05 00 00 00 00 0A 2A 30 02 80 21 02 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x5 Illegal Request, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.006s timeout 40s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: The current problem looks like a buffer underrun.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: It looks like 'driveropts=burnfree' does not work for this drive.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Please report.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Make sure that you are root, enable DMA and check your HW/OS set up.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01:    1 of  689 MB written (fifo  99%) [buf  94%]   2.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: write track data: error after 1079296 bytes
BraseroWodim stdout: Writing  time:   11.341s
BraseroWodim stdout: Average write speed 417.1x.
BraseroWodim stdout: Min drive buffer fill was 94%
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: WARNING: Some drives don't like fixation in dummy mode.
BraseroWodim stdout: Fixating time:   19.719s
BraseroWodim stderr: wodim: fifo had 272 puts and 18 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo was 0 times empty and 7 times full, min fill was 97%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: HUP
BraseroWodim process finished with status 254
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroWodim stopping
BraseroWodim got killed
Session error : unknown (brasero_burn_record brasero-burn.c:2769)

---

### Post by fancypiper on 2009-11-06
Did you burn at the fastest speed? That is the major cause of mis-burns.  Before selecting burn, select properties and change max speed to the slowest speed you can select, then try burn.

---

### Post by sh4d0w808 on 2009-11-06
I think it is an error of wodim. As U can see, some functions required to pass to the device with root rights, but the current wodim implementation is unable to do this.

I recommend to try the writing with cdrecord package instead of wodim and of course on lowest available speed.

---

### Post by helamsirrine on 2009-11-06
I tried burning the .iso @ 4x speed and still got a crash at the finalizing of the simulated burn just like before. Speed is not the problem. Nice thought though, I wish it was that simple. 
Hey sh4d0w808, how can i set the package used by Brasero or do you suggest a different program? I am running gnome ubuntu and I cant find the cdrecord package with synaptic.

---

### Post by sh4d0w808 on 2009-11-06
> **helamsirrine said:**
> I tried burning the .iso @ 4x speed and still got a crash at the finalizing of the simulated burn just like before. Speed is not the problem. Nice thought though, I wish it was that simple. 
Hey sh4d0w808, how can i set the package used by Brasero or do you suggest a different program?

The problem is that all the GUI-based programs using the same subsystem - it doesn' matter that U use Brasero, K3b and so on...

I strongly recommend to [read this page]("http://cdrecord.berlios.de/private/cdrecord.html"), if U interesting to change your burning subsystem.

---

### Post by fancypiper on 2009-11-06
Open an x terminal and these commands should work for burning CDs.
# Using cdrecord
# As root, find the device
sudo cdrecord -scanbus
sudo cd /path/to/iso
sudo cdrecord -v dev=4,0,0 speed=0 ubuntu-9.10-desktop-i386.iso

---

### Post by helamsirrine on 2009-11-06
I'm a complete noob in the terminal which is why I posted this question in the beginner forum.

---

### Post by Bunnybugs on 2009-11-06
Have you tried to burn at a very slow speed too?

Sometimes you'r software needs to find out the capabilities of your device!

---

### Post by helamsirrine on 2009-11-06
I tried the following commands based on another post. You can see my device, and that I changed wodim permissions, and tried and failed to use cdrecord to blank a cd.
---------
helamsirrine@helam:~$ ls -l /dev/cdrom
lrwxrwxrwx 1 root root 3 2009-11-03 16:52 /dev/cdrom -> sr0
helamsirrine@helam:~$ sudo chmod +s /usr/bin/wodim
helamsirrine@helam:~$ wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'    rwrw-- : 'HL-DT-ST' 'DVDRAM GH41N'
-------------------------------------------------------------------------
helamsirrine@helam:~$ cdrecord -v speed=4 blank=fast dev=/dev/scd0
TOC Type: 1 = CD-ROM
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.9
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GH41N    '
Revision       : 'MN01'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x001A (DVD+RW) 
Profile: 0x001B (DVD+R) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
Drive buf size : 1053696 = 1029 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Drive DMA Speed: 16373 kB/s 93x CD 11x DVD
Current Secsize: 2048
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
Speed set to 706 KB/s
Starting to write CD/DVD at speed   4.0 in real BLANK mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Performing OPC...
Blanking PMA, TOC, pregap
Errno: 5 (Input/output error), blank unit scsi sendcmd: no error
CDB:  A1 01 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A A1 00 00 80 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 9600s
wodim: Cannot blank disk, aborting.
wodim: Some drives do not support all blank types.
wodim: Try again with wodim blank=all.

---

### Post by clive littlewood on 2009-11-06
Hi

Looks like it does not like your type (manufacturer) of discs.

I would try a different type of disc.

Clive

---

### Post by helamsirrine on 2009-11-06
I realise I did not need to blank a cd-r, oops. I ran the commands below in the terminal changing back wodim permissions and attempting to use cdrecord to burn the karmic iso from my desktop. Again I got these lines:
```
**Sense Key: 0x5 Illegal Request, Segment 0 **
[B]Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 40s

write track data: error after 1079296 bytes
wodim: The current problem looks like a buffer underrun.
wodim: It looks like 'driveropts=burnfree' does not work for this drive.
wodim: Please report.
wodim: Make sure that you are root, enable DMA and check your HW/OS set up.[/B]
```This seems important but I dont know what it means. Someone please help me.

---------
**COPY OF MY TERMINAL**
helamsirrine@helam:~$ sudo chmod -s /usr/bin/wodim
[sudo] password for helamsirrine: 
helamsirrine@helam:~$ cdrecord -v speed=4 driveropts=burnfree dev=/dev/scd0 /home/helamsirrine/Desktop/ubuntu-9.10-desktop-i386.iso
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.9
Driveropts: 'burnfree'
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GH41N    '
Revision       : 'MN01'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x001A (DVD+RW) 
Profile: 0x001B (DVD+R) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
Drive buf size : 1053696 = 1029 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Drive DMA Speed: 16087 kB/s 91x CD 11x DVD
FIFO size      : 12582912 = 12288 KB
Track 01: data   689 MB        
Total size:      792 MB (78:30.24) = 353268 sectors
Lout start:      792 MB (78:32/18) = 353268 sectors
Current Secsize: 2048
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
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 6578
Speed set to 706 KB/s
Starting to write CD/DVD at speed   4.0 in real TAO mode for single session.
[B]Last chance to quit, starting real write in    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:    1 of  689 MB written (fifo 100%) [buf  96%]   0.9x.Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 02 0F 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 2A 30 02 80 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0 [/B]<----- what is this?
[B]Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 40s

write track data: error after 1079296 bytes
wodim: The current problem looks like a buffer underrun.
wodim: It looks like 'driveropts=burnfree' does not work for this drive.
wodim: Please report.
wodim: Make sure that you are root, enable DMA and check your HW/OS set up.[/B]
Writing  time:   15.304s
Average write speed 308.7x.
Min drive buffer fill was 96%
Fixating...
Fixating time:   63.216s
wodim: fifo had 209 puts and 18 gets.
wodim: fifo was 0 times empty and 7 times full, min fill was 97%.
helamsirrine@helam:~$

---

### Post by helamsirrine on 2009-11-06
I just burned the iso in windows 7 succesfully, which is really just sad. At least I can be sure that this is a software problem. I think the problem is with wodim, can someone Please give me some clue as to what my problem is. I am typing in the dark here, and I am afraid I might F*ck something up.:mad:

---

### Post by sh4d0w808 on 2009-11-09
> **helamsirrine said:**
> I just burned the iso in windows 7 succesfully, which is really just sad. At least I can be sure that this is a software problem. I think the problem is with wodim, can someone Please give me some clue as to what my problem is. I am typing in the dark here, and I am afraid I might F*ck something up.:mad:

Just one page back...

---

### Post by userFrodo on 2009-11-19
Hello helamsirrine,

I think we might be experiencing the same troubles on Ubuntu 9.1.

Same dvd-drive, (from your post):
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GH41N    '

Same computer too?
Mine is an Acer Aspire AX3300 AMD Athlon 2 X2 240 dual core

I had many problems using Brasero, tried all kinds of things from forums. Eventually something happened using Brasero, but speed was less than 1. More like 0.1.

Than used K3b, which seemed a little bit more friendly to my system. But alas, it also burnt at no higher speed than 0.2.

I've used +RW discs for this.

I've also tried regular DVD-r discs with no success. Brasero just ended the session after burning slowly about 25 Mb.

Because we seem to have the same problems I would very much appreciate some kind of exchange of experiences.

I'll keep in touch on this forum and post details from logs next time.

Best regards,

Frodo Dirks
Rotterdam | The Netherlands

---

### Post by kerneloftruth on 2010-03-14
I got that drive too with firmware MN01 on an Packard Bell (Acer Brand)

the manufacturer is Hitachi (!)

this drive is a pure nightmare !

I tried burning 2 different CD-Rs (4 CD-Rs in total: 2 in Windows 7 and 2 in Linux) and each of them showed that error

@Hitachi:

awaiting firmware-updates please :KS

---

### Post by bclarky12 on 2010-04-08
> **fancypiper said:**
> Open an x terminal and these commands should work for burning CDs.
# Using cdrecord
# As root, find the device
sudo cdrecord -scanbus
sudo cd /path/to/iso
sudo cdrecord -v dev=4,0,0 speed=0 ubuntu-9.10-desktop-i386.iso

I have the same drive as everybody else, I tried your command, thanks, but it didn't work, i got the following, any more advice would be greatly appreciated, thank you!

vik-desktop vik # cd /home/vik/Desktop
vik-desktop Desktop # cdrecord -scanbus
scsibus1:
    1,0,0    100) 'HL-DT-ST' 'DVDRAM GH41N    ' 'MN01' Removable CD-ROM
    1,1,0    101) *
    1,2,0    102) *
    1,3,0    103) *
    1,4,0    104) *
    1,5,0    105) *
    1,6,0    106) *
    1,7,0    107) *
scsibus11:
    11,0,0    1100) 'ASUS    ' 'SDRW-08D1S-U    ' 'A202' Removable CD-ROM
    11,1,0    1101) *
    11,2,0    1102) *
    11,3,0    1103) *
    11,4,0    1104) *
    11,5,0    1105) *
    11,6,0    1106) *
    11,7,0    1107) *
vik-desktop Desktop # cdrecord -v dev=1,0,0 speed=0 cdrom_image.iso
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
WARNING: the deprecated pseudo SCSI syntax found as device specification.
Support for that may cease in the future versions of wodim. For now,
the device will be mapped to a block device file where possible.
Run "wodim --devices" for details.
Linux sg driver version: 3.5.27
Wodim version: 1.1.9
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GH41N    '
Revision       : 'MN01'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x001A (DVD+RW) 
Profile: 0x001B (DVD+R) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
Drive buf size : 1053696 = 1029 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Drive DMA Speed: 16007 kB/s 90x CD 11x DVD
FIFO size      : 12582912 = 12288 KB
Track 01: data     0 MB        
Total size:        0 MB (00:04.02) = 302 sectors
Lout start:        1 MB (00:06/02) = 302 sectors
Current Secsize: 2048
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
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 359544
Speed set to 7057 KB/s
Starting to write CD/DVD at speed  40.0 in real TAO mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 MB written.
Track 01: writing 600 KB of pad data.
Track 01: Total bytes read/written: 0/614400 (300 sectors).
Writing  time:   12.603s
Average write speed   0.3x.
Fixating...
Fixating time:   19.806s
wodim: fifo had 1 puts and 1 gets.
wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
vik-desktop Desktop #

---

### Post by bclarky12 on 2010-04-08
i also don't think its just wodim, it doesn't work with nero linux or k3b either.

---

### Post by userFrodo on 2010-05-28
After upgrading to 10.04 (Lucid Lynx) DVD's are burning at normal speeds. 
 Problem solved. Same machine, only upgraded OS. 
Unfortunately I wasn't able to solve the problem running Karmic.ThanksFrodo Dirks> **kerneloftruth said:**
> I got that drive too with firmware MN01 on an Packard Bell (Acer Brand)
 
the manufacturer is Hitachi (!)
 
this drive is a pure nightmare !
 
I tried burning 2 different CD-Rs (4 CD-Rs in total: 2 in Windows 7 and 2 in Linux) and each of them showed that error
 
@Hitachi:
 
awaiting firmware-updates please :KS

---


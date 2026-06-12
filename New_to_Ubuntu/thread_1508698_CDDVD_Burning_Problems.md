---
title: "CD/DVD Burning Problems"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by Tumpster on 2010-06-13
So I'm trying to burn cd's and DVD's and I keep having them fail, both with K3B and Brasero, here is the error log I get with K3B:
Devices
-----------------------
HL-DT-ST DVDRAM GH24NS50 XP00 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

System
-----------------------
K3b Version: 1.68.0
KDE Version: 4.3.5 (KDE 4.3.5)
QT Version:  4.5.2
Kernel:      2.6.31-22-generic

Used versions
-----------------------
cdrecord: 1.1.9

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
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
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GH24NS50 '
Revision       : 'XP00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x001B (DVD+R)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x001A (DVD+RW) 
Profile: 0x001B (DVD+R) (current)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0009 (CD-R) 
Profile: 0x000A (CD-RW) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1048576 = 1024 KB
Drive DMA Speed: 15002 kB/s 85x CD 10x DVD
FIFO size      : 12582912 = 12288 KB
Speed set to 22160 KB/s
Track 01: data   622 MB        
Total size:      715 MB (70:50.45) = 318784 sectors
Lout start:      715 MB (70:52/34) = 318784 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 2295104 Blocks current: 2295104 Blocks remaining: 1976320
Starting to write CD/DVD at speed  17.0 in real SAO mode for single session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... Errno: 5 (Input/output error), reserve track scsi sendcmd: no error
CDB:  53 00 00 00 00 00 04 DD 40 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 35 2D 03 0E 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.606s timeout 200s
/usr/bin/wodim: Cannot open new session.
input buffer ready.
Writing  time:    0.660s
/usr/bin/wodim: fifo had 191 puts and 0 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=16 -sao driveropts=burnfree -data -tsize=318784s -

Here's the error message I get from Xfburn: "SCSI error on write(0,16): [3 0C 00]  Write error"

Any help to get this working again?

---

### Post by quixote on 2010-06-15
First: I have no real idea what all the messages are trying to say.  But I did have a situation once where writing to CD failed because of some permission problem and one of the messages was a very similar "operation not permitted."  So, just for grins, try "sudo k3b" (or whatever the command is) and see if the problem goes away.  If yes, it's a permission problem and at least we know which direction to start looking in.

---

### Post by gbear14275 on 2010-11-13
Tried sudo... no luck.  Here are my outputs from both brasero and from cdrecord:

cdrecord:

sudo cdrecord -v bootcd.iso
wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
Device was not specified. Trying to find an appropriate drive...
Looking for a CD-R drive to store 1.75 MiB...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
scsidev: '/dev/cdrom'
devname: '/dev/cdrom'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.10
Driveropts: 'burnfree'
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   :
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GSA-U10N '
Revision       : '1.05'
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
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Drive DMA Speed: 15582 kB/s 88x CD 11x DVD
FIFO size      : 12582912 = 12288 KB
Track 01: data     1 MB        
Total size:        2 MB (00:11.97) = 898 sectors
Lout start:        2 MB (00:13/73) = 898 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 4
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, low Beta category (A-) (2)
  ATIP start of lead in:  -12508 (97:15/17)
  ATIP start of lead out: 359845 (79:59/70)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 22
Manufacturer: Ritek Co.
Blocks total: 359845 Blocks current: 359845 Blocks remaining: 358947
Speed set to 4234 KB/s
Starting to write CD/DVD at speed  24.0 in real TAO mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:    1 of    1 MB written (fifo 100%) [buf  99%]   0.5x.
Track 01: Total bytes read/written: 1835008/1835008 (896 sectors).
Errno: 5 (Input/output error), flush cache scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 73 04 BB 80 A0 80 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0xA0 Qual 0x80 (vendor unique sense code 0xA0) [No matching qualifier] Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 26.236s timeout 120s
Trouble flushing the cache
wodim: Cannot close track.
Writing  time:   40.710s
Average write speed   0.3x.
Min drive buffer fill was 99%
Fixating...
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 71 00 03 00 00 00 00 0A 34 2C 03 80 73 04 00 00
Sense Key: 0x3 Medium Error, deferred error, Segment 0
Sense Code: 0x73 Qual 0x04 (program memory area update failure) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 0.001s timeout 480s
cmd finished after 0.001s timeout 480s
wodim: Cannot fixate disk.
Fixating time:    0.004s
wodim: fifo had 29 puts and 29 gets.
wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

Brasero log: 

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1744)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_RILYLV.bin toc = none
BraseroBurnURI called brasero_job_get_session_output_size
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_3WLYLV.bin toc = none
BraseroLocalTrack called brasero_job_get_session_output_size
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
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_DGEYLV.bin toc = none
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /home/gbear14275/Desktop/bootcd (copy).iso (size = 1835008)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 3284bdcf36f28c0d38465362090c3e82 ((null) before)
BraseroChecksumImage Finished track successfully
BraseroChecksumImage stopping
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_action
BraseroLibburn unsupported operation
BraseroLibburn deactivating
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_device
BraseroLibburn Drive (/dev/sr0) init result = 1
BraseroLibburn called brasero_job_get_flags
BraseroLibburn called brasero_job_get_media
BraseroLibburn called brasero_job_get_fd_in
BraseroLibburn called brasero_job_get_tracks
BraseroLibburn Setting multi 0
BraseroLibburn Setting burnproof 1
BraseroLibburn Setting dummy 0
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_convert_fs_adr( /dev/sr0 )
BraseroLibburn Writing
BraseroLibburn called brasero_job_set_dangerous
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_is_enumerable_adr( /dev/sr0 ) is true
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Async START UNIT succeeded after 0.1 seconds
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Allocating buffer via mmap()
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn cd Profile= 09h , obs= 32768 , obs_pad= 0
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn TAO pre-track 01 : get_nwa(0)=1, d=0 , demand=1835008 , cap=736958464
 
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI error condition on command 2Ah WRITE(10): [3 0C 00] Write error
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Libburn reported an error SCSI error on write(0,16): [3 0C 00] Write error
BraseroLibburn called brasero_job_error
BraseroLibburn finished with an error
BraseroLibburn asked to stop because of an error
        error           = 1
        message = "SCSI error on write(0,16): [3 0C 00] Write error"
BraseroLibburn stopping
Session error : SCSI error on write(0,16): [3 0C 00] Write error (brasero_burn_record brasero-burn.c:2862)

Any help would be appreciated.

---

### Post by jrev on 2010-11-13
the fault comes on a new CD to burn ?

---

### Post by I'mGeorge on 2010-11-13
when you insert a disc into your CD/DVD unit can you at least read it, I mean are there any problems in mounting the device and read a CD either or you're having problems only when you're trying to write a CD ?

---

### Post by gbear14275 on 2010-11-13
I'mGeorge,

I can normally read them as blank disks until I try and burn them.  Then I get the error "SCSI error on write(0,16): [3 0C 00] Write error" or the errors out of cdrecord and the discs can no longer even be seen when re-inserted...

---

### Post by I'mGeorge on 2010-11-13
you could try using cdrskin instead of wodim for k3b. 

```

sudo apt-get install cdrskin

```

cache this tutorial to see how to configure k3b to use cdrskin instead of wodim [http://scdbackup.sourceforge.net/k3b_on_cdrskin.html](http://scdbackup.sourceforge.net/k3b_on_cdrskin.html)

---


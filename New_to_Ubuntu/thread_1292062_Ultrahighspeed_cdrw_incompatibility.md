---
title: "Ultrahighspeed cdrw incompatibility?"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by biomanolo on 2009-10-15
Hi to all! 

Does anyone know why I can not burn ultrahighspeed cd-rw's anymore after update although my drive does mention unltrahighspeed compatibility...

I have tried lowering the burn speed and multiple programs (brasero, K3d and gnomebaker) but have failed nonetheless...

here is the log from brasero:

Checking session consistency (brasero_burn_check_session_consistency burn.c:1714)
Inconsistent flag: you can't use flag on_the_fly (brasero_burn_check_session_consistency burn.c:1810)
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum deactivating
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum output set (IMAGE) image = /media/disk/brasero_tmp_RGY21U toc = (null)
BraseroMd5sum called brasero_job_get_session_output_size
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_input_type
BraseroMd5sum called brasero_job_get_fd_in
BraseroMd5sum called brasero_job_get_current_track
BraseroMd5sum called brasero_job_set_current_action
BraseroMd5sum called brasero_job_start_progress
[B]BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress

50 times or so....

BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
[/B]BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_input_type
BraseroMd5sum called brasero_job_get_current_track
BraseroMd5sum setting new checksum cace6ea9dde8dc158174e345aabe3fae ((null) before)
BraseroMd5sum finished track successfully
BraseroMd5sum stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack output set (IMAGE) image = /media/disk/brasero_tmp_L11P1U toc = (null)
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
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
    dev=/dev/scd0
    gracetime=0
    speed=10
    driveropts=burnfree
    -dao
    fs=16m
    -data
    -nopad
    /home/seta/Desktop/Sharing/ubuntu-9.04-desktop-amd64.iso
BraseroWodim launching command
BraseroWodim called brasero_job_get_fd_out
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/scd0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsibus: -2 target: -2 lun: -2
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Linux sg driver version: 3.5.27
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Wodim version: 1.1.6
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
BraseroWodim stdout: Identification : 'DVDRAM GMA-4080N'
BraseroWodim stdout: Revision       : '0V35'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x000A (CD-RW)
BraseroWodim stdout: Profile: 0x0012 (DVD-RAM) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) (current)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Profile: 0x0002 (Removable disk) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
BraseroWodim stdout: Drive buf size : 1053696 = 1029 KB
BraseroWodim stdout: Drive DMA Speed: 12502 kB/s 71x CD 9x DVD
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 1764 KB/s
BraseroWodim called brasero_job_get_flags
**BraseroWodim stderr: wodim: Probably trying to use ultra high speed medium on improper writer.**
*##this is where I dont get it...*

BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   696 MB        
BraseroWodim stdout: Total size:      800 MB (79:16.21) = 356716 sectors
BraseroWodim stdout: Lout start:      800 MB (79:18/16) = 356716 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 1
BraseroWodim stdout:   Reference speed: 0
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is erasable
BraseroWodim stdout:   Disk sub type: Ultra High speed Rewritable media (2)
BraseroWodim stdout:   ATIP start of lead in:  -11076 (97:34/24)
BraseroWodim stdout:   ATIP start of lead out: 359849 (79:59/74)
BraseroWodim stdout:   1T speed low: 16 1T speed high: 16
BraseroWodim stdout:   2T speed low:  8 2T speed high: 24
BraseroWodim stdout:   power mult factor: 4 5
BraseroWodim stdout:   recommended erase/write power: 1
BraseroWodim stdout:   A1 values: 66 4A 99
BraseroWodim stdout:   A2 values: 38 80 00
BraseroWodim stdout:   A3 values: 04 C4 A0
BraseroWodim stdout: Disk type:    Phase change
BraseroWodim stdout: Manuf. index: 11
BraseroWodim stdout: Manufacturer: Mitsubishi Chemical Corporation
BraseroWodim stdout: Blocks total: 359849 Blocks current: 359849 Blocks remaining: 3133
BraseroWodim stdout: Writing  time:    0.670s
BraseroWodim stderr: wodim: fifo had 8 puts and 0 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo was 0 times empty and 0 times full, min fill was 0%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: HUP
BraseroWodim stdout: HUP
BraseroWodim process finished with status 255
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroWodim stopping
BraseroWodim got killed
Session error : unknown (brasero_burn_record burn.c:2273)

---

### Post by biomanolo on 2009-10-15
Please help me out...
Need to get a Live Cd on the go for a friend's brand new "vista" laptop!

Cheers.
Manolo

---


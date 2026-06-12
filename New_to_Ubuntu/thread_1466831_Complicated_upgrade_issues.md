---
title: "Complicated upgrade issues"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by ben1986 on 2010-04-30
I've looked around, and no-one seems to be having this problem but me.  If I'm wrong, kindly berate me and post a link.

Anyway, trying to upgrade through update manager, I get an error because apparently I have broken packages.  Annoying.  Synaptic doesn't fix this packages, or rather, doesn't think any need fixing when I ask it to.  Whatever, fine, I had some kernel issues a while ago, updated the kernel to avoid the "freeze", but this ran me in low graphics mode, and when I updated the drivers to something that sort of worked, its not able to enable effects on my card, which I know works fine, and worked fine before.  Anyway, I figured I would just go for a clean install.  but now of course, having downloaded the iso, inserting a cd, and telling Brasero to write to disc I get this error:

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1848)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_BAUWBV.bin toc = none
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_NMUWBV.bin toc = none
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
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
    speed=48
    driveropts=burnfree
    fs=16m
    -data
    -nopad
    /media/Storage/Downloads/ubuntu-10.04-desktop-i386.iso
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
BraseroWodim stdout: Identification : 'DVDRAM GH22NS50 '
BraseroWodim stdout: Revision       : 'TN01'
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
BraseroWodim stdout: Drive DMA Speed: 16415 kB/s 93x CD 11x DVD
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 8468 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   699 MB        
BraseroWodim stdout: Total size:      803 MB (79:34.89) = 358117 sectors
BraseroWodim stdout: Lout start:      803 MB (79:36/67) = 358117 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 4
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is not erasable
BraseroWodim stdout:   Disk sub type: Medium Type A, low Beta category (A-) (2)
BraseroWodim stdout:   ATIP start of lead in:  -12508 (97:15/17)
BraseroWodim stdout:   ATIP start of lead out: 359845 (79:59/70)
BraseroWodim stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
BraseroWodim stdout: Manuf. index: 22
BraseroWodim stdout: Manufacturer: Ritek Co.
BraseroWodim stdout: Blocks total: 359845 Blocks current: 359845 Blocks remaining: 1728
BraseroWodim stdout: Starting to write CD/DVD at speed  48.0 in dummy TAO mode for single session.
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
BraseroWodim stdout: Track 01:    0 of  699 MB written.
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
BraseroWodim stderr: cmd finished after 0.002s timeout 40s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: The current problem looks like a buffer underrun.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: It looks like 'driveropts=burnfree' does not work for this drive.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Please report.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Make sure that you are root, enable DMA and check your HW/OS set up.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01:    1 of  699 MB written (fifo 100%) [buf  95%]   1.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: write track data: error after 1079296 bytes
BraseroWodim stdout: Writing  time:   10.063s
BraseroWodim stdout: Average write speed 476.4x.
BraseroWodim stdout: Min drive buffer fill was 95%
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: WARNING: Some drives don't like fixation in dummy mode.
BraseroWodim stderr: wodim: fifo had 272 puts and 18 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Fixating time:   20.844s
BraseroWodim stderr: wodim: fifo was 0 times empty and 4 times full, min fill was 97%.
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
Session error : unknown (brasero_burn_record brasero-burn.c:2811)


And I tried to use Unetbootin but my computer won't see a bootable image on the SDHC card I'm using.  And yes, the boot order in the BIOS is appropriate.

What I would like, is for someone to help me either fix my broken packages so I can upgrade normally, or to help me burn a Live CD so I can do a clean install.  Any ideas?

---

### Post by ben1986 on 2010-04-30
This is the error I get when I try to upgrade through update manager:

Could not determine the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Unable to correct problems, you have held broken packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.



I'm not running a pre-release, although my current kernel might be the release candidate from a couple of months ago.

---

### Post by ben1986 on 2010-04-30
Ok, I got fed-up and did a clean install, took the opportunity to mount /home on its own partition as well, so now my hard drive is chopped into about 7 pieces.  Never mind, 'mon the Lynx!

---


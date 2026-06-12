---
title: "Unknown error brasero"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by the_karmic_koala on 2010-03-23
I'm trying to burn audio cd's and bootable iso disks but evertime brasero starts burning i get the message "unknown error occured .i viewed the log and got this....HELP!!! please ^_^


Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1848)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI burn:// URI found burn:///Elfen%20Lied%20-%20Lilium%20(Full%20Version).mp3
BraseroBurnURI called brasero_job_set_current_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Information retrieval for burn:///Elfen%20Lied%20-%20Lilium%20(Full%20Version).mp3
BraseroBurnURI Added file /home/steven/LimeWire/Saved/Elfen Lied - Lilium (Full Version).mp3 at /Elfen Lied - Lilium (Full Version).mp3
BraseroBurnURI called brasero_job_add_track
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI Finished track successfully
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_set_output_size_for_current_track
BraseroChecksumFiles stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_session_output_size
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_set_current_action
BraseroChecksumFiles called brasero_job_get_flags
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_IA509U.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles Finished track successfully
BraseroChecksumFiles stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroWodim called brasero_job_get_action
BraseroWodim creating input
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim got varg:
BraseroWodim deactivating
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage creating input
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage deactivating
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_data_label
BraseroGenisoimage called brasero_job_get_flags
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_current_action
BraseroGenisoimage got varg:
    /usr/bin/genisoimage
    -input-charset
    utf8
    -r
    -J
    -graft-points
    -path-list
    /tmp/brasero_tmp_YN649U
    -exclude-list
    /tmp/brasero_tmp_CB749U
    -A
    Brasero-2.28.2
    -sysid
    LINUX
    -quiet
    -print-size
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stderr: HUP
BraseroGenisoimage stdout: 3739
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_output_size_for_current_track
BraseroGenisoimage stdout: HUP
BraseroGenisoimage process finished with status 0
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage Finished track successfully
BraseroGenisoimage got killed
BraseroGenisoimage stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroWodim called brasero_job_get_action
BraseroWodim creating input
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_get_device
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_speed
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_fd_in
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_session_output_size
BraseroWodim called brasero_job_set_current_action
BraseroWodim got varg:
    wodim
    -v
    dev=/dev/sr0
    speed=16
    driveropts=burnfree
    fs=4m
    tsize=3739s
    -data
    -nopad
    -
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage linked to BraseroWodim
BraseroChecksumImage creating input
BraseroChecksumImage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage linked to BraseroChecksumImage
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_data_label
BraseroGenisoimage called brasero_job_get_flags
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_set_current_action
BraseroGenisoimage got varg:
    /usr/bin/genisoimage
    -input-charset
    utf8
    -r
    -J
    -graft-points
    -path-list
    /tmp/brasero_tmp_70ER9U
    -exclude-list
    /tmp/brasero_tmp_BYER9U
    -A
    Brasero-2.28.2
    -sysid
    LINUX
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage Starting checksum generation live (size = 0)
BraseroChecksumImage called brasero_job_set_nonblocking
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
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
BraseroWodim stdout: Vendor_info    : '_NEC    '
BraseroWodim stdout: Identification : 'DVD+RW ND-1100A '
BraseroWodim stdout: Revision       : '2.15'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-ROM.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) (current)
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
BraseroWodim stdout: Drive buf size : 1345536 = 1314 KB
BraseroWodim stdout: FIFO size      : 4194304 = 4096 KB
BraseroWodim stderr: Speed set to 2822 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data     7 MB        
BraseroWodim stdout: Total size:        8 MB (00:49.88) = 3741 sectors
BraseroWodim stdout: Lout start:        8 MB (00:51/66) = 3741 sectors
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
BraseroWodim stdout: Blocks total: 359846 Blocks current: 359846 Blocks remaining: 356105
BraseroWodim stdout: Starting to write CD/DVD at speed  16.0 in real TAO mode for single session.
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
BraseroWodim stdout:    1 seconds.   0 seconds. Operation starts.
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Performing OPC...
BraseroWodim stderr: Errno: 5 (Input/output error), send opc scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  54 01 00 00 00 00 00 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing  time:   15.715s
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: BURN-Free was never needed.
BraseroWodim stderr: Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: Sense Key: 0x3 Medium Error, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 15.627s timeout 60s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: OPC failed.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo had 64 puts and 0 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: HUP
BraseroWodim process finished with status 255
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroGenisoimage stopping
BraseroGenisoimage got killed
BraseroGenisoimage disconnecting BraseroGenisoimage from BraseroChecksumImage
BraseroChecksumImage stopping
BraseroChecksumImage disconnecting BraseroChecksumImage from BraseroWodim
BraseroChecksumImage closing connection for BraseroChecksumImage
BraseroWodim stopping
BraseroWodim got killed
BraseroWodim closing connection for BraseroWodim
Session error : unknown (brasero_burn_record brasero-burn.c:2811)

---

### Post by Didius Falco on 2010-03-27
I always had problems with Brasero in Karmic. I eventually installed Gnomebaker (from the repos) and had no problems with it.

Regards,

Didius

---

### Post by stringtheorem on 2010-03-28
Try a complete removal and reinstall of Brasero in Synaptic Package Manager.

System => Administration => Synaptic Package Manager

---


---
title: "Burning ISO to CD-R"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by Ahunt on 2010-12-07
I am having an odd problem with just a desktop PC that I have. This is a Compaq Presario that was purchased new in May 2009. It is running Ubuntu 10.04. It came with an ATAPI A DH16A6L-C cd-r cd-rw dvd dvd-r dvd-ram reader/writer combination drive.

In trying it out with both Brasero and K3B I find that it can read CDs and DVDs, erase CD-RWs, write data to CDs (only with K3B and not with Brasero) and DVDs and burn ISO images to CD-RWs, but not CD-Rs (with either K3B or Brasero).

In trying to burn ISO files to CD-Rs it just produces "unknown error" and the disk is unbootable. Oddly in writing the same ISO files to a CD-RW with either Brasero or K3B the disk tests fine. 

I am using good quality Phillips CD-Rs and these have been used with no problems to burn ISO images on other Ubuntu PCs.

This same problem seems to have been [discussed on the forums before]("http://ubuntuforums.org/showthread.php?t=1627890"), but without any resolution. In that case it was suggested to make a bootable USB, but I need to be able to make ISO CDs to give away. (Spreading Ubuntu!)

Any help would be greatly appreciated!

Here is the error report from trying to burn a CD-R with Brassero:

```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1741)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_VVSWMV.bin toc = none
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_F9UWMV.bin toc = none
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
	speed=40
	driveropts=burnfree
	fs=16m
	-data
	-nopad
	/home/ruth/ISOs/lubuntu-10.10.iso
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
BraseroWodim called brasero_job_get_fd_in
BraseroWodim called brasero_job_get_fd_out
BraseroWodim stderr: wodim: No write mode specified.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Assuming -tao mode.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Future versions of wodim may have different drive dependent defaults.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsidev: '/dev/sr0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/sr0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsibus: -2 target: -2 lun: -2
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Linux sg driver version: 3.5.27
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Wodim version: 1.1.10
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
BraseroWodim stdout: Vendor_info    : 'ATAPI   '
BraseroWodim stdout: Identification : 'DVD A  DH16A6L-C'
BraseroWodim stdout: Revision       : 'ZHCG'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0016 (DVD-R/DL layer jump recording) 
BraseroWodim stdout: Profile: 0x0015 (DVD-R/DL sequential recording) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0012 (DVD-RAM) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Profile: 0x0002 (Removable disk) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
BraseroWodim stdout: Drive buf size : 1867008 = 1823 KB
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 7057 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   545 MB        
BraseroWodim stdout: Total size:      626 MB (62:04.06) = 279305 sectors
BraseroWodim stdout: Lout start:      626 MB (62:06/05) = 279305 sectors
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
BraseroWodim stdout: Blocks total: 359846 Blocks current: 359846 Blocks remaining: 80541
BraseroWodim stdout: Forcespeed is OFF.
BraseroWodim stdout: Starting to write CD/DVD at speed  40.0 in real TAO mode for single session.
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
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stdout: 
BraseroWodim stdout: Track 01:    0 of  545 MB written.
BraseroWodim stdout: Track 01:    1 of  545 MB written (fifo  97%) [buf  79%]   4.5x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    2 of  545 MB written (fifo 100%) [buf 100%]  19.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    3 of  545 MB written (fifo 100%) [buf 100%]  19.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    4 of  545 MB written (fifo 100%) [buf 100%]  18.4x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    5 of  545 MB written (fifo 100%) [buf 100%]  19.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    6 of  545 MB written (fifo 100%) [buf 100%]  18.4x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    7 of  545 MB written (fifo 100%) [buf 100%]  19.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    8 of  545 MB written (fifo 100%) [buf 100%]  18.5x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    9 of  545 MB written (fifo 100%) [buf 100%]  19.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   10 of  545 MB written (fifo 100%) [buf 100%]  18.6x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   11 of  545 MB written (fifo 100%) [buf 100%]  19.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   12 of  545 MB written (fifo 100%) [buf 100%]  18.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   13 of  545 MB written (fifo 100%) [buf 100%]  19.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   14 of  545 MB written (fifo 100%) [buf 100%]  18.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   15 of  545 MB written (fifo 100%) [buf 100%]  19.4x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   16 of  545 MB written (fifo 100%) [buf 100%]  18.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   17 of  545 MB written (fifo 100%) [buf 100%]  19.5x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   18 of  545 MB written (fifo 100%) [buf 100%]  18.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   19 of  545 MB written (fifo 100%) [buf 100%]  19.5x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   20 of  545 MB written (fifo 100%) [buf 100%]  19.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   21 of  545 MB written (fifo 100%) [buf 100%]  19.6x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   22 of  545 MB written (fifo 100%) [buf 100%]  19.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   23 of  545 MB written (fifo 100%) [buf 100%]  19.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   24 of  545 MB written (fifo 100%) [buf 100%]  19.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   25 of  545 MB written (fifo 100%) [buf 100%]  19.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   26 of  545 MB written (fifo 100%) [buf 100%]  19.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   27 of  545 MB written (fifo 100%) [buf  99%]  19.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   28 of  545 MB written (fifo 100%) [buf 100%]  19.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   29 of  545 MB written (fifo 100%) [buf 100%]  19.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   30 of  545 MB written (fifo 100%) [buf 100%]  19.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   31 of  545 MB written (fifo 100%) [buf 100%]  19.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   32 of  545 MB written (fifo 100%) [buf 100%]  19.4x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   33 of  545 MB written (fifo 100%) [buf 100%]  20.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   34 of  545 MB written (fifo 100%) [buf 100%]  20.6x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   35 of  545 MB written (fifo 100%) [buf 100%]  20.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   36 of  545 MB written (fifo 100%) [buf 100%]  20.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   37 of  545 MB written (fifo 100%) [buf 100%]  20.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   38 of  545 MB written (fifo 100%) [buf 100%]  20.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   39 of  545 MB written (fifo 100%) [buf 100%]  20.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   40 of  545 MB written (fifo 100%) [buf 100%]  20.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   41 of  545 MB written (fifo 100%) [buf 100%]  20.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   42 of  545 MB written (fifo 100%) [buf 100%]  20.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   43 of  545 MB written (fifo 100%) [buf 100%]  20.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   44 of  545 MB written (fifo 100%) [buf 100%]  21.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   45 of  545 MB written (fifo 100%) [buf 100%]  20.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   46 of  545 MB written (fifo 100%) [buf  99%]  21.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   47 of  545 MB written (fifo 100%) [buf 100%]  20.4x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   48 of  545 MB written (fifo 100%) [buf 100%]  21.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   49 of  545 MB written (fifo 100%) [buf 100%]  20.5x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   50 of  545 MB written (fifo 100%) [buf 100%]  21.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   51 of  545 MB written (fifo 100%) [buf 100%]  20.5x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   52 of  545 MB written (fifo 100%) [buf  99%]  21.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   53 of  545 MB written (fifo 100%) [buf 100%]  20.6x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   54 of  545 MB written (fifo 100%) [buf 100%]  21.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   55 of  545 MB written (fifo 100%) [buf  97%]  20.6x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   56 of  545 MB written (fifo 100%) [buf 100%]  21.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   57 of  545 MB written (fifo 100%) [buf 100%]  20.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   58 of  545 MB written (fifo 100%) [buf  99%]  21.4x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   59 of  545 MB written (fifo 100%) [buf 100%]  20.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   60 of  545 MB written (fifo 100%) [buf 100%]  21.4x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   61 of  545 MB written (fifo 100%) [buf 100%]  20.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   62 of  545 MB written (fifo 100%) [buf 100%]  21.5x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   63 of  545 MB written (fifo 100%) [buf 100%]  20.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   64 of  545 MB written (fifo 100%) [buf  99%]  21.5x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   65 of  545 MB written (fifo 100%) [buf 100%]  22.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   66 of  545 MB written (fifo 100%) [buf 100%]  21.6x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   67 of  545 MB written (fifo 100%) [buf 100%]  22.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   68 of  545 MB written (fifo 100%) [buf 100%]  21.6x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   69 of  545 MB written (fifo 100%) [buf 100%]  22.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   70 of  545 MB written (fifo 100%) [buf 100%]  21.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   71 of  545 MB written (fifo 100%) [buf 100%]  22.4x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   72 of  545 MB written (fifo 100%) [buf 100%]  21.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   73 of  545 MB written (fifo 100%) [buf 100%]  22.4x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   74 of  545 MB written (fifo 100%) [buf 100%]  21.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   75 of  545 MB written (fifo 100%) [buf 100%]  22.5x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   76 of  545 MB written (fifo 100%) [buf 100%]  21.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   77 of  545 MB written (fifo 100%) [buf 100%]  22.5x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   78 of  545 MB written (fifo 100%) [buf 100%]  21.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   79 of  545 MB written (fifo 100%) [buf 100%]  22.6x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   80 of  545 MB written (fifo 100%) [buf 100%]  21.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   81 of  545 MB written (fifo 100%) [buf 100%]  22.6x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   82 of  545 MB written (fifo 100%) [buf 100%]  22.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   83 of  545 MB written (fifo 100%) [buf 100%]  22.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   84 of  545 MB written (fifo 100%) [buf 100%]  22.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   85 of  545 MB written (fifo 100%) [buf 100%]  22.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   86 of  545 MB written (fifo 100%) [buf 100%]  22.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   87 of  545 MB written (fifo 100%) [buf  96%]  22.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   88 of  545 MB written (fifo 100%) [buf 100%]  22.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   89 of  545 MB written (fifo 100%) [buf 100%]  22.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   90 of  545 MB written (fifo 100%) [buf 100%]  22.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   91 of  545 MB written (fifo  99%) [buf 100%]  22.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   92 of  545 MB written (fifo 100%) [buf 100%]  22.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   93 of  545 MB written (fifo 100%) [buf 100%]  22.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   94 of  545 MB written (fifo 100%) [buf 100%]  22.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   95 of  545 MB written (fifo 100%) [buf 100%]  22.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   96 of  545 MB written (fifo 100%) [buf 100%]  23.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   97 of  545 MB written (fifo 100%) [buf 100%]  23.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   98 of  545 MB written (fifo 100%) [buf 100%]  23.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   99 of  545 MB written (fifo 100%) [buf 100%]  23.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  100 of  545 MB written (fifo  99%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  101 of  545 MB written (fifo 100%) [buf 100%]  23.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  102 of  545 MB written (fifo  99%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  103 of  545 MB written (fifo 100%) [buf 100%]  23.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  104 of  545 MB written (fifo 100%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  105 of  545 MB written (fifo 100%) [buf 100%]  23.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  106 of  545 MB written (fifo 100%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  107 of  545 MB written (fifo  99%) [buf 100%]  23.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  108 of  545 MB written (fifo 100%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  109 of  545 MB written (fifo 100%) [buf  99%]  23.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  110 of  545 MB written (fifo  99%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  111 of  545 MB written (fifo 100%) [buf 100%]  23.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  112 of  545 MB written (fifo 100%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  113 of  545 MB written (fifo 100%) [buf 100%]  23.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  114 of  545 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  115 of  545 MB written (fifo 100%) [buf 100%]  23.4x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  116 of  545 MB written (fifo  99%) [buf  99%]  24.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  117 of  545 MB written (fifo  99%) [buf 100%]  23.5x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  118 of  545 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  119 of  545 MB written (fifo 100%) [buf 100%]  23.5x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  120 of  545 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  121 of  545 MB written (fifo  99%) [buf 100%]  23.5x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  122 of  545 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  123 of  545 MB written (fifo 100%) [buf 100%]  23.5x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  124 of  545 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  125 of  545 MB written (fifo 100%) [buf  97%]  23.6x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  126 of  545 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  127 of  545 MB written (fifo 100%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  128 of  545 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  129 of  545 MB written (fifo  99%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  130 of  545 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  131 of  545 MB written (fifo 100%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  132 of  545 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  133 of  545 MB written (fifo 100%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  134 of  545 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  135 of  545 MB written (fifo 100%) [buf  99%]  25.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  136 of  545 MB written (fifo 100%) [buf  99%]  24.5x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  137 of  545 MB written (fifo 100%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  138 of  545 MB written (fifo 100%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  139 of  545 MB written (fifo 100%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  140 of  545 MB written (fifo 100%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  141 of  545 MB written (fifo 100%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  142 of  545 MB written (fifo 100%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  143 of  545 MB written (fifo 100%) [buf  99%]  25.4x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  144 of  545 MB written (fifo 100%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  145 of  545 MB written (fifo 100%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  146 of  545 MB written (fifo 100%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  147 of  545 MB written (fifo 100%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  148 of  545 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  149 of  545 MB written (fifo 100%) [buf 100%]  25.5x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  150 of  545 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  151 of  545 MB written (fifo  99%) [buf  99%]  25.5x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  152 of  545 MB written (fifo 100%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  153 of  545 MB written (fifo 100%) [buf 100%]  25.5x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  154 of  545 MB written (fifo 100%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  155 of  545 MB written (fifo 100%) [buf 100%]  25.6x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  156 of  545 MB written (fifo 100%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  157 of  545 MB written (fifo 100%) [buf 100%]  25.6x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  158 of  545 MB written (fifo  99%) [buf 100%]  26.4x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  159 of  545 MB written (fifo  99%) [buf 100%]  25.6x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  160 of  545 MB written (fifo 100%) [buf 100%]  26.4x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  161 of  545 MB written (fifo 100%) [buf 100%]  25.6x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  162 of  545 MB written (fifo 100%) [buf 100%]  26.5x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  163 of  545 MB written (fifo 100%) [buf 100%]  25.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  164 of  545 MB written (fifo 100%) [buf 100%]  26.5x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  165 of  545 MB written (fifo  99%) [buf 100%]  25.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  166 of  545 MB written (fifo 100%) [buf  99%]  26.5x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  167 of  545 MB written (fifo  99%) [buf 100%]  25.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  168 of  545 MB written (fifo  99%) [buf 100%]  26.6x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  169 of  545 MB written (fifo 100%) [buf 100%]  25.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  170 of  545 MB written (fifo 100%) [buf 100%]  26.6x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  171 of  545 MB written (fifo 100%) [buf 100%]  25.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  172 of  545 MB written (fifo 100%) [buf 100%]  26.6x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  173 of  545 MB written (fifo  99%) [buf 100%]  25.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  174 of  545 MB written (fifo  99%) [buf 100%]  26.6x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  175 of  545 MB written (fifo 100%) [buf 100%]  25.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  176 of  545 MB written (fifo 100%) [buf 100%]  26.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  177 of  545 MB written (fifo  99%) [buf 100%]  25.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  178 of  545 MB written (fifo 100%) [buf 100%]  26.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  179 of  545 MB written (fifo 100%) [buf 100%]  25.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  180 of  545 MB written (fifo 100%) [buf 100%]  26.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  181 of  545 MB written (fifo 100%) [buf 100%]  25.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  182 of  545 MB written (fifo 100%) [buf 100%]  26.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  183 of  545 MB written (fifo  99%) [buf 100%]  25.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  184 of  545 MB written (fifo 100%) [buf 100%]  26.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  185 of  545 MB written (fifo 100%) [buf 100%]  26.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  186 of  545 MB written (fifo 100%) [buf 100%]  26.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  187 of  545 MB written (fifo 100%) [buf 100%]  26.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  188 of  545 MB written (fifo 100%) [buf 100%]  26.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  189 of  545 MB written (fifo 100%) [buf 100%]  27.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  190 of  545 MB written (fifo 100%) [buf 100%]  26.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  191 of  545 MB written (fifo  99%) [buf 100%]  27.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  192 of  545 MB written (fifo 100%) [buf 100%]  26.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  193 of  545 MB written (fifo  99%) [buf  96%]  27.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  194 of  545 MB written (fifo 100%) [buf  99%]  26.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  195 of  545 MB written (fifo 100%) [buf  99%]  27.7x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  196 of  545 MB written (fifo  99%) [buf  96%]  26.6x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  197 of  545 MB written (fifo 100%) [buf  99%]  28.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  198 of  545 MB written (fifo 100%) [buf 100%]  26.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  199 of  545 MB written (fifo  99%) [buf 100%]  27.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  200 of  545 MB written (fifo 100%) [buf 100%]  26.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  201 of  545 MB written (fifo 100%) [buf 100%]  27.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  202 of  545 MB written (fifo 100%) [buf 100%]  27.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  203 of  545 MB written (fifo  99%) [buf 100%]  27.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  204 of  545 MB written (fifo 100%) [buf 100%]  27.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  205 of  545 MB written (fifo 100%) [buf 100%]  27.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  206 of  545 MB written (fifo 100%) [buf 100%]  27.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  207 of  545 MB written (fifo 100%) [buf 100%]  27.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  208 of  545 MB written (fifo 100%) [buf 100%]  27.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  209 of  545 MB written (fifo  99%) [buf 100%]  27.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  210 of  545 MB written (fifo  99%) [buf 100%]  27.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  211 of  545 MB written (fifo 100%) [buf 100%]  27.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  212 of  545 MB written (fifo 100%) [buf 100%]  27.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  213 of  545 MB written (fifo 100%) [buf 100%]  27.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  214 of  545 MB written (fifo 100%) [buf 100%]  27.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  215 of  545 MB written (fifo 100%) [buf 100%]  28.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  216 of  545 MB written (fifo 100%) [buf 100%]  27.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  217 of  545 MB written (fifo 100%) [buf 100%]  28.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  218 of  545 MB written (fifo 100%) [buf 100%]  27.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  219 of  545 MB written (fifo 100%) [buf 100%]  27.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  220 of  545 MB written (fifo 100%) [buf 100%]  28.8x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  221 of  545 MB written (fifo  99%) [buf 100%]  28.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  222 of  545 MB written (fifo  99%) [buf 100%]  28.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  223 of  545 MB written (fifo 100%) [buf 100%]  28.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  224 of  545 MB written (fifo  99%) [buf 100%]  28.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  225 of  545 MB written (fifo 100%) [buf 100%]  28.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  226 of  545 MB written (fifo 100%) [buf 100%]  28.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  227 of  545 MB written (fifo 100%) [buf 100%]  28.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  228 of  545 MB written (fifo 100%) [buf 100%]  28.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  229 of  545 MB written (fifo  99%) [buf 100%]  28.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  230 of  545 MB written (fifo 100%) [buf 100%]  28.9x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  231 of  545 MB written (fifo 100%) [buf 100%]  28.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  232 of  545 MB written (fifo 100%) [buf 100%]  29.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  233 of  545 MB written (fifo  99%) [buf 100%]  28.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  234 of  545 MB written (fifo 100%) [buf 100%]  29.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  235 of  545 MB written (fifo 100%) [buf 100%]  28.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  236 of  545 MB written (fifo 100%) [buf 100%]  29.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  237 of  545 MB written (fifo 100%) [buf 100%]  28.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  238 of  545 MB written (fifo 100%) [buf 100%]  29.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  239 of  545 MB written (fifo  99%) [buf 100%]  28.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  240 of  545 MB written (fifo 100%) [buf 100%]  29.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  241 of  545 MB written (fifo 100%) [buf 100%]  28.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  242 of  545 MB written (fifo  99%) [buf 100%]  29.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  243 of  545 MB written (fifo 100%) [buf 100%]  28.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  244 of  545 MB written (fifo 100%) [buf 100%]  29.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  245 of  545 MB written (fifo 100%) [buf 100%]  28.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  246 of  545 MB written (fifo 100%) [buf 100%]  29.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  247 of  545 MB written (fifo 100%) [buf 100%]  28.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  248 of  545 MB written (fifo 100%) [buf 100%]  29.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  249 of  545 MB written (fifo 100%) [buf 100%]  28.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  250 of  545 MB written (fifo  99%) [buf 100%]  29.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  251 of  545 MB written (fifo 100%) [buf 100%]  30.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  252 of  545 MB written (fifo  99%) [buf  99%]  29.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  253 of  545 MB written (fifo 100%) [buf  99%]  30.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  254 of  545 MB written (fifo 100%) [buf  99%]  29.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  255 of  545 MB written (fifo 100%) [buf 100%]  30.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  256 of  545 MB written (fifo 100%) [buf 100%]  29.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  257 of  545 MB written (fifo 100%) [buf  99%]  30.0x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  258 of  545 MB written (fifo 100%) [buf 100%]  29.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  259 of  545 MB written (fifo  99%) [buf 100%]  30.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  260 of  545 MB written (fifo  99%) [buf  99%]  29.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  261 of  545 MB written (fifo 100%) [buf 100%]  30.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  262 of  545 MB written (fifo 100%) [buf 100%]  29.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  263 of  545 MB written (fifo 100%) [buf 100%]  30.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  264 of  545 MB written (fifo 100%) [buf 100%]  29.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  265 of  545 MB written (fifo 100%) [buf 100%]  30.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  266 of  545 MB written (fifo 100%) [buf 100%]  29.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  267 of  545 MB written (fifo 100%) [buf  99%]  30.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  268 of  545 MB written (fifo 100%) [buf 100%]  29.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  269 of  545 MB written (fifo 100%) [buf 100%]  30.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  270 of  545 MB written (fifo 100%) [buf  99%]  29.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  271 of  545 MB written (fifo  99%) [buf 100%]  30.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  272 of  545 MB written (fifo  99%) [buf 100%]  29.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  273 of  545 MB written (fifo 100%) [buf 100%]  30.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  274 of  545 MB written (fifo 100%) [buf  99%]  29.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  275 of  545 MB written (fifo 100%) [buf 100%]  30.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  276 of  545 MB written (fifo 100%) [buf  99%]  29.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  277 of  545 MB written (fifo  99%) [buf  99%]  30.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  278 of  545 MB written (fifo 100%) [buf 100%]  29.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  279 of  545 MB written (fifo  99%) [buf  99%]  30.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  280 of  545 MB written (fifo  99%) [buf 100%]  29.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  281 of  545 MB written (fifo  99%) [buf  99%]  30.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  282 of  545 MB written (fifo  99%) [buf 100%]  31.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  283 of  545 MB written (fifo  99%) [buf 100%]  30.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  284 of  545 MB written (fifo  99%) [buf  99%]  31.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  285 of  545 MB written (fifo  99%) [buf 100%]  30.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  286 of  545 MB written (fifo  99%) [buf  99%]  31.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  287 of  545 MB written (fifo 100%) [buf  99%]  30.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  288 of  545 MB written (fifo  99%) [buf  99%]  31.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  289 of  545 MB written (fifo 100%) [buf  99%]  30.1x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  290 of  545 MB written (fifo  99%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  291 of  545 MB written (fifo 100%) [buf  99%]  30.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  292 of  545 MB written (fifo 100%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  293 of  545 MB written (fifo 100%) [buf  99%]  30.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  294 of  545 MB written (fifo 100%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  295 of  545 MB written (fifo 100%) [buf  99%]  30.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  296 of  545 MB written (fifo 100%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  297 of  545 MB written (fifo  99%) [buf  99%]  30.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  298 of  545 MB written (fifo  99%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  299 of  545 MB written (fifo 100%) [buf  99%]  30.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  300 of  545 MB written (fifo 100%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  301 of  545 MB written (fifo 100%) [buf  99%]  30.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  302 of  545 MB written (fifo  99%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  303 of  545 MB written (fifo 100%) [buf  99%]  30.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  304 of  545 MB written (fifo 100%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  305 of  545 MB written (fifo 100%) [buf  99%]  30.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  306 of  545 MB written (fifo  99%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  307 of  545 MB written (fifo 100%) [buf  99%]  30.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  308 of  545 MB written (fifo 100%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  309 of  545 MB written (fifo  99%) [buf  99%]  30.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  310 of  545 MB written (fifo  99%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  311 of  545 MB written (fifo 100%) [buf  99%]  30.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  312 of  545 MB written (fifo  99%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  313 of  545 MB written (fifo  99%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  314 of  545 MB written (fifo 100%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  315 of  545 MB written (fifo  99%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  316 of  545 MB written (fifo 100%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  317 of  545 MB written (fifo 100%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  318 of  545 MB written (fifo 100%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  319 of  545 MB written (fifo 100%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  320 of  545 MB written (fifo  99%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  321 of  545 MB written (fifo 100%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  322 of  545 MB written (fifo  99%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  323 of  545 MB written (fifo 100%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  324 of  545 MB written (fifo  99%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  325 of  545 MB written (fifo 100%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  326 of  545 MB written (fifo  99%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  327 of  545 MB written (fifo 100%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  328 of  545 MB written (fifo  99%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  329 of  545 MB written (fifo 100%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  330 of  545 MB written (fifo  99%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  331 of  545 MB written (fifo 100%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  332 of  545 MB written (fifo  99%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  333 of  545 MB written (fifo 100%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  334 of  545 MB written (fifo 100%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  335 of  545 MB written (fifo 100%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  336 of  545 MB written (fifo 100%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  337 of  545 MB written (fifo  99%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  338 of  545 MB written (fifo 100%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  339 of  545 MB written (fifo 100%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  340 of  545 MB written (fifo  99%) [buf  99%]  31.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  341 of  545 MB written (fifo 100%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  342 of  545 MB written (fifo 100%) [buf  99%]  31.3x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  343 of  545 MB written (fifo 100%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  344 of  545 MB written (fifo 100%) [buf  99%]  33.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  345 of  545 MB written (fifo 100%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  346 of  545 MB written (fifo 100%) [buf  99%]  33.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  347 of  545 MB written (fifo  99%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  348 of  545 MB written (fifo 100%) [buf  99%]  33.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  349 of  545 MB written (fifo 100%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  350 of  545 MB written (fifo 100%) [buf  99%]  33.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  351 of  545 MB written (fifo  99%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  352 of  545 MB written (fifo 100%) [buf  99%]  33.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  353 of  545 MB written (fifo 100%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  354 of  545 MB written (fifo 100%) [buf  99%]  33.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  355 of  545 MB written (fifo 100%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  356 of  545 MB written (fifo  99%) [buf  99%]  33.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  357 of  545 MB written (fifo  99%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  358 of  545 MB written (fifo 100%) [buf  99%]  33.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  359 of  545 MB written (fifo 100%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 00 02 D0 FE 00 00 1F 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 71 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x3 Medium Error, deferred error, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 23.156s timeout 40s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: A write error occured.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Please properly read the error message above.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01:  360 of  545 MB written (fifo 100%) [buf  99%]  33.2x.
BraseroWodim called brasero_job_get_media
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: write track data: error after 378007552 bytes
BraseroWodim stdout: Writing  time:  135.472s
BraseroWodim stdout: Average write speed  28.9x.
BraseroWodim stdout: Min drive buffer fill was 96%
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Fixating time:   20.887s
BraseroWodim stderr: wodim: fifo had 6209 puts and 5955 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo was 0 times empty and 4845 times full, min fill was 96%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: BURN-Free was 1 times used.
BraseroWodim stderr: HUP
BraseroWodim stdout: HUP
BraseroWodim process finished with status 254
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroWodim stopping
Session error : unknown (brasero_burn_record brasero-burn.c:2842)
```

---

### Post by oldfred on 2010-12-07
I have preferred K3b, but are you writing at the slowest speed that it will let you. That almost always is a problem if you do not write at slow speeds.

---

### Post by Ahunt on 2010-12-07
> **oldfred said:**
> I have preferred K3b, but are you writing at the slowest speed that it will let you. That almost always is a problem if you do not write at slow speeds.

That is a good point, I have always let both K3B and Brasero choose their own speeds to write the ISOs for both CD-RWs and CD-Rs, but naturally CD-RWs run more slowly. Let me try that and see if I wreck another CD-R or not.

---

### Post by amjjawad on 2010-12-07
> **oldfred said:**
> I have preferred K3b, but are you writing at the slowest speed that it will let you. That almost always is a problem if you do not write at slow speeds.

I agree with my friend oldfred :)
I always use 32x and it's usually work.

P.S.
I love K3b.

---

### Post by Ahunt on 2010-12-07
> **amjjawad said:**
> I agree with my friend oldfred :)
I always use 32x and it's usually work.

P.S.
I love K3b.

We have had good experiences with K3B in the past, but it has outstanding [bug 581926]("https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/581926") about not blanking CD-RWs right now that reduces its usefulness.

While you are talking CD-writing any thoughts on [this other thread I started yesterday about XFburn on Lubuntu 10.10]("http://ubuntuforums.org/showthread.php?p=10209045")? No answers yet over there, I think it ended up off the front page too fast.

---

### Post by anewguy on 2010-12-07
Do you dual-boot on this PC?  If so, copy the ISO image to a place in your NTSF file system, then boot Windows and try to burn it there.  If it doesn't burn correctly there I would suspect either an image problem or a device (DVD/RW) problem.  The log does show some error on the medium, but whether or not that is a "legit" error I don't know.

I also would recommend the slowest speed possible.  Why?  The heads on different drives react differently to the heat generated by both the spin of the disk and by the burning process.  Slower burn time seems to work better in those cases.  This also helps on media that may be borderline.

Dave ;)

---

### Post by Ahunt on 2010-12-07
No it is an Ubuntu 10.04 box only!

I tried burning an ISO CD-R using K3B at the slowest selectable speed (8X) and it completed the burn without any errors. I tested the CD in the same drive and it wouldn't boot although it booted fine on another PC and the built in test showed that the CD has no errors!

I then tried booting another identical ISO on a CD-RW on the first PC and it booted fine and tested fine as well.

I would think this drive is worn out except that it is nearly new and has been rarely used. I am starting to wonder if it is just unservicable?

I am going to try writing an ISO CD-R on it using Brasero set as slowly as possible and see how that goes.

---

### Post by Ahunt on 2010-12-07
Okay I burned an ISO to a CD-R with Brasero this time set to run at the lowest selectable speed (again 8X) and the result was the same: the burn went fine with no errors but the PC would not boot from the CD when it was done. Putting the CD into another PC it booted fine and tested fine as well, no errors.

I am going to try one more experiment - try burning the same ISO image with another PC and then see if it boots on the first PC or not.

---

### Post by Ahunt on 2010-12-07
This time I burned an ISO CD-R on another PC and then booted to it and checked it on that PC. It indicated no errors, just like the other two. Then I booted to it on the Compaq and it booted fine and tested as no errors.

I have to admit that I don't really get it. Is this virtually new drive failing or not or is this some other problem?

---

### Post by ezsit on 2010-12-07
> I tested the CD in the same drive and it wouldn't boot although it booted fine on another PC and the built in test showed that the CD has no errors!

Then this appears to be a hardware problem. Your drive isn't working correctly if your disc checks out and works in another computer. Get a new drive or update the firmware in your current drive.

---

### Post by amjjawad on 2010-12-08
> > **ezsit said:**
> Then this appears to be a hardware problem. Your drive isn't working correctly if your disc checks out and works in another computer. Get a new drive or update the firmware in your current drive.


I would do two more things before anything else:
1- Burn at a bit faster speed like: 24x
2- Install the driver on another PC and try it from there. Different PC, different OS. If the same issue will happen again, then guess you have no other choices except what ezsit suggested :)

---

### Post by anewguy on 2010-12-08
> **amjjawad said:**
> I would do two more things before anything else:
1- Burn at a bit faster speed like: 24x
2- Install the driver on another PC and try it from there. Different PC, different OS. If the same issue will happen again, then guess you have no other choices except what ezsit suggested :)

Just for your information - burning at a FASTER rate won't solve a problem like this - when the device and/or media are questionable, burning at the SLOWEST speed is recommended.

---

### Post by gerowen on 2010-12-08
Brasero is broken, and I haven't seen an update pushed so I'm assuming it's still broken.  I use Gnomebaker instead; works like a charm whereas the latest version of Brasero falls on its face.

---

### Post by anewguy on 2010-12-08
I wonder if it's actually Brasero, or if it's in the underlying wodim (sp??) that it actually uses.  I think wodim can be used from the command line, so I'd be curious as to what happens if someone having trouble with Brasero just tries the same function with command line wodim.  That would be a way to isolate the problem.  I'm probably wrong here, but I *thought* Brasero was more or less a Gui's front end using other tools (like cdrkit, genisoimage, wodim, etc.) to actually do the work - sort of like what ndisgtk is to ndiswrapper -> a saver of time, typing and frustration.

I'd do some of these tests myself, but I am not having any of these problems.

Dave ;)

---

### Post by Ahunt on 2010-12-08
I am using Brasero on another PC with Ubuntu 10.04 and it works fine there. I agree with some of the other posters here that prior to Ubuntu 10.04 was terrible, but it has improved.

K3B also works fine on that PC, except that it has outstanding [Bug 581926]("https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/581926") and won't currently blank CD-RWs.

Does anyone know if there is a command line tool to write CDs? That would bypass the problems of the various GUI frontends.

---

### Post by anewguy on 2010-12-08
There are a couple in Synaptic Package Manager, one of which is wodim.  I *think* cdrecord or a variant is there as well.

Let us know how things go.  

Dave ;)

---

### Post by anewguy on 2010-12-09
Okay, going from your other post (for anyone who might be concerned, it's not a duplicate post), we can see that wodim on its own can burn the ISO.  Makes me think the problem must indeed then lie with Brasero.

I would suggest opening a bug report on launchpad about this, including the stuff from the other post where stand-alone wodim did create the ISO disk.

Dave ;)

---

### Post by billnyeizzle on 2010-12-09
here is your problem right here...
wherever you downloaded that .iso you need to match the checksums from the downloaded file and the .iso on the CD/DVD. Sometimes what happens is the .iso doesn't burn correctly and can have an offset checksum. :P

BraseroChecksumImage There is a checksum already 0[FONT=Verdana]

[/FONT]

---

### Post by anewguy on 2010-12-10
> **billnyeizzle said:**
> here is your problem right here...
wherever you downloaded that .iso you need to match the checksums from the downloaded file and the .iso on the CD/DVD. Sometimes what happens is the .iso doesn't burn correctly and can have an offset checksum. :P

BraseroChecksumImage There is a checksum already 0[FONT=Verdana]

[/FONT]

Re-read this thread carefully, then you may want to modify your post.

---

### Post by billnyeizzle on 2010-12-10
> **anewguy said:**
> Re-read this thread carefully, then you may want to modify your post.

thanks for the insight.. I thought he was actually trying to burn .iso's of Ubuntu. yeahh.. sorry I'm just tired.. It's almost 2AM here in the states. I'll admit, it was a "noob" error.

---

### Post by MrWES on 2010-12-10
FYI, cdrdao is command line from the terminal, but it always does the trick for me.

[http://ubuntuforums.org/showthread.php?t=795181]("http://ubuntuforums.org/showthread.php?t=795181")

Bill

---

### Post by Ahunt on 2010-12-10
For billnyeizzle - thanks for the thought on MD5 sum checking, all the ISOs I am using have been MD5 sum checked!

Okay we are making some progress on this issue. Today I had a chance to access the PC in question and try burning CDs from the command line using Wodim. I should note that both K3B and Brasero use wodim to burn, whereas Xfburn uses the libburnia libraries.

As when using K3B and Brasero, burning an ISO from the command line to a CD-RW worked fine, producing a disk that passed the "Check this disc for defects" built in test.

Burning a CD-R using wodim from the command line using:

```
wodim dev=/dev/cdrom ~/image.iso
```

resulted in a wrecked disk and this error:

```
ruth@b:~$ wodim dev=/dev/cdrom ~/ISOs/ubuntu-10.10-desktop-i386.iso
wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'ATAPI   '
Identification : 'DVD A  DH16A6L-C'
Revision       : 'ZHCG'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Speed set to 7057 KB/s
Starting to write CD/DVD at speed  40.0 in real TAO mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 05 52 CA 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 71 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, deferred error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 3.865s timeout 40s
write track data: error after 714493952 bytes
wodim: A write error occured.
wodim: Please properly read the error message above.
ruth@b:~$ 
```

The problem may have well been the burning speed it chose there, but I would need to know the syntax to designate a slower speed for burning. The same problem happened when using Brasero and K3B as described above.

So next I tried installing Xfburn. Using this application is covered in [another thread]("http://ubuntuforums.org/showthread.php?p=10209045"). I successfully wrote an ISO to a CD-RW with it and it tested serviceable using the built-in "Test this disc for defects" feature. Next I tried writing an ISO to a CD-R with it at the slowest possible speed (8X) and it wrote for a short while and then ejected the CD-R reporting "burn run failed". The CD-R was of course wrecked.

So it seems this drive will read CD-Rs, CD-RWs and DVDs and will write CD-RWs, but not consistently write CD-Rs, using any of Brasero, K3B, wodim from the command line and Xfburn.

My conclusion from all of this is that the CD writing function of this almost new CD/DVD reader writer drive is unservicable or at least intermittently failing. Does anyone else see any other conclusions, perhaps something I have missed?

---

### Post by anewguy on 2010-12-10
I'm going to suggest something that is going to seem a little strange, but bear with me:

- what ever brand of CD you are using, get a small pack of a different brand.  Also make this small pack the opposite of what you are using - if you are using CD-R, try CD+R or vice versa.

I can't imagine why it would make any difference, but it might be worth a shot as I know some drives (though I thought it was just older drives) don't like CD-R or CD+R, depending on the drive.

For changing the burn speed for wodim, try either man wodim or wodim --help in the command line.  I don't remember off the top of my head right now but I do recall seeing the speed option.

BTW - the disk you created from an ISO - is that the same one as you mentioned in the other thread?  I thought that one completed ok and we were just waiting to see if it would boot.

Dave ;)

---

### Post by Ahunt on 2010-12-10
Thanks for your reply!

I am convinced that the CD-Rs themselves are not the problem. The ones I have now are good quality Phillips ones and I haven't had any bad ones from them. The drive in question here has had problems with several other brands (Maxell, Verbatim) while my other PC has had none with any of those brands. In the past I have had problems with some unbranded generic CD-Rs which can be awful. I don't buy them anymore.

Sorry, the other thread is about a different PC running Lubuntu, I will update that thread now that I have the answers, thanks for reminding me!

---

### Post by anewguy on 2010-12-10
Ah......

In that case, I would really lean towards a drive problem.  A friend of mine in Illinois had a similar problem with a drive no more than 3 months old - I don't remember the brand.  He ended up having to get a new drive after everything else failed.  It's quite possible the write heads just aren't any good or are misaligned, either way would mean getting a new drive.  Is your current drive still under warranty?

Dave ;)

---

### Post by Ahunt on 2010-12-10
I really think you are right, it is a hardware problem. I just found the paperwork and the PC was purchased new, along with its CD/DVD writer in May 2009. It has a standard HP warranty of 1 years so I am SOL! 

On the bright side I just bought a new CD reader/writer for another PC recently for Cdn$36, so they aren't too expensive.

I did want to take this opportunity to thank everyone who answered this thread. The Ubuntu Forums are part of what makes Ubuntu so great - helpful and polite people helping each other. Thank you all.

---


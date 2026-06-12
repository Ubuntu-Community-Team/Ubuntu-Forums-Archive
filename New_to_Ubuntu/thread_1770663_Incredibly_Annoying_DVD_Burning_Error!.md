---
title: "Incredibly Annoying DVD Burning Error!"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by Andavane on 2011-05-29
Hi 
Last year I purchased a HP ultra mobile laptop which came bundled with a DVD burner. Now I also have a thinkpad to which I downloaded an *.iso and I right clicked to burn the image to a DVD using the DVD burner from the HP.
I got this message. (attached)

I guess that this piece of hardware is locked so it can only be burned on the HP? !

The logfile btw:

> Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1744)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_ORGJWV.bin toc = none
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_VZFJWV.bin toc = none
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
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_8CDJWV.bin toc = none
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /home/wubithink/Desktop/openSUSE-11.4-DVD-i586.iso/openSUSE-11.4-DVD-i586.iso (size = 4541382656)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 5f6d6d67c3e256b2513311f4ed650515 ((null) before)
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
BraseroLibburn Setting burnproof 0
BraseroLibburn Setting dummy 0
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_convert_fs_adr( /dev/sr0 )
BraseroLibburn Writing
BraseroLibburn called brasero_job_set_dangerous
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_is_enumerable_adr( /dev/sr0 ) is true
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Async START UNIT succeeded after 0.1 seconds
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn mmc_set_streaming: end_lba=2295103 ,  r=4584 ,  w=11080
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Allocating buffer via mmap()
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn dvd/bd Profile= 1Bh , obs= 32768 , obs_pad= 1
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn DVD+R pre-track 01 : get_nwa(0), ret= 1 , d->nwa= 0
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn DVD pre-track 01 : demand=4541382656, cap=4700372992

BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 7h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 7h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 7h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 7h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 7h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 5Ch indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 5Ch indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI command 2Ah indicates host or driver error: host_status= 1h , driver_status= 0h
BraseroLibburn called brasero_job_set_dangerous
BraseroLibburn Finished successfully session
BraseroLibburn stopping
Preparing to checksum (type 2 5f6d6d67c3e256b2513311f4ed650515) (brasero_burn_record_session brasero-burn.c:2487)
Unsupported type of task operation
Session successfully finished (brasero_burn_record brasero-burn.c:2868) 

---

### Post by wolfen69 on 2011-05-29
At the end of that mess it says: "Session successfully finished". Did you try and use the disk?

---

### Post by wildmanne39 on 2011-05-29
> **Andavane said:**
> Hi 
Last year I purchased a HP ultra mobile laptop which came bundled with a DVD burner. Now I also have a thinkpad to which I downloaded an *.iso and I right clicked to burn the image to a DVD using the DVD burner from the HP.
I got this message. (attached)

I guess that this piece of hardware is locked so it can only be burned on the HP? !

The logfile btw:HI, make sure you have the restricted packages for dvd burning installed.

---

### Post by wolfen69 on 2011-05-29
> **wildmanne39 said:**
> HI, make sure you have the restricted packages for dvd burning installed.

Restricted packages aren't needed for burning iso's to DVD. Those are only for viewing DVD movies.

---

### Post by wildmanne39 on 2011-05-29
> **wolfen69 said:**
> Restricted packages aren't needed for burning iso's to DVD. Those are only for viewing DVD movies.
Hi, I didnt click on the fact that it was an iso, thanks.

---


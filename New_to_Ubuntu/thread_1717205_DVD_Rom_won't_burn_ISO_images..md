---
title: "DVD Rom won't burn ISO images."
date: 2011-03-29
forum: New to Ubuntu
---

### Post by roy.champion on 2011-03-29
Here is the save log after I attempted to burn the disc. I have tried multiple discs and haven't ever had a problem with them before I switched to Ubuntu. I tried 2 different types of Memorex DVD+R discs and the burner is compatible with +-R and +R DL.

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1741)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /media/Downloads/brasero_tmp_627LTV.bin toc = none
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
BraseroLocalTrack output set (IMAGE) image = /media/Downloads/brasero_tmp_KQ2LTV.bin toc = none
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
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs got varg:
BraseroGrowisofs deactivating
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
    growisofs
    -use-the-force-luke=notray
    -use-the-force-luke=4gms
    -dvd-compat
    -speed=6
    -use-the-force-luke=tracksize:1823885
    -use-the-force-luke=tty
    -Z
    /dev/sr0=/media/Downloads/Programs/Ultimate.iso
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/media/Downloads/Programs/Ultimate.iso of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 6.1x1352KBps.
BraseroGrowisofs stdout:           0/3735316480 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/3735316480 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/3735316480 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/3735316480 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroGrowisofs stopping
Session error : unknown (brasero_burn_record brasero-burn.c:2842)

---

### Post by TeoBigusGeekus on 2011-03-29
Try to use growisofs straight from command line
```
growisofs -dvd-compat -Z /dev/sr0=/path/name.iso
```
If /dev/sr0 doesn't work, try /dev/cd or /dev/dvd.

---


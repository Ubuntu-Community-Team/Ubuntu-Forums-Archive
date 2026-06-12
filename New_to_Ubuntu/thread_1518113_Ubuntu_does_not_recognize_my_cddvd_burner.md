---
title: "Ubuntu does not recognize my cd/dvd burner"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by trooperchix on 2010-06-26
It's causing issues with burning anything.  

[[IMG]http://i46.photobucket.com/albums/f115/Trooperchix/th_Screenshot-1.png[/IMG]](http://s46.photobucket.com/albums/f115/Trooperchix/?action=view&current=Screenshot-1.png)

When I do burn, this is the error I get from Brasero:

```

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1741)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_87BSEV.bin toc = none
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_4YBSEV.bin toc = none
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
	-speed=8
	-use-the-force-luke=tracksize:1498045
	-use-the-force-luke=tty
	-Z
	/dev/sr0=/home/eddie/Desktop/Home Movies/folsomprisontitan/folsomprisontitan.iso
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/eddie/Desktop/Home Movies/folsomprisontitan/folsomprisontitan.iso of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 8.2x1352KBps.
BraseroGrowisofs stdout:           0/3067996160 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/3067996160 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/3067996160 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/3067996160 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/3067996160 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/3067996160 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/3067996160 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/3067996160 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/3067996160 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGrowisofs stopping
Session error : unknown (brasero_burn_record brasero-burn.c:2842)

```

Thanks ahead of time for the help.

---

### Post by mk1w86 on 2010-06-26
Quite a lot of people seem to be having problems similar to yours.

The CD/DVD drive showing up as unrecognised is normal because there is no disk inserted, when you insert a disk its properties get displayed (see screenshot).  My DVD burner shows up as unrecognised with no disk inserted (see screenshot) yet it still works. ;)

The first thing you could try to resolve your problem is another burning application such as GnomeBaker or K3B.

Also, what are you trying to burn e.g. iso, data, audio CD?

---


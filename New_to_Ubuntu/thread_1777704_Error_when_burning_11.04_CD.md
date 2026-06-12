---
title: "Error when burning 11.04 CD"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by Andavane on 2011-06-08
I'm trying to burn a CD for Ubuntu 11.04 using my Thinkpad X201i.
It's a new burner called "Storage Options" it's "Powered by Panasonic" and I bought it from Maplin.

On my first attempt I got the message listed below (and it wouldn't recognise the CD when I reinserted it).

On a new CD I'm getting to select "Burn As File" or "Burn Contents".

In the past I just right-clicked and used "Write to disc" not understanding fully the process. I could do it by booting into Windows and using the software disc that came with it, but I really want to use Ubuntu (currently 10.10) and to understand the process deeper.

Attached is the text of the logfile for the error I'm getting on the first CD as well as a screenshot of the message I'm getting with the new CD.

```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1744)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_9N17VV.bin toc = none
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_GS07VV.bin toc = none
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
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_0OZ7VV.bin toc = none
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /home/wubithink/Desktop/ubuntu-11.04-desktop-amd64.iso (size = 732112896)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 7de611b50c283c1755b4007a4feb0379 ((null) before)
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
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_is_enumerable_adr( /dev/sr0 ) is true
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Async START UNIT succeeded after 0.1 seconds
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Allocating buffer via mmap()
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn cd Profile= 09h , obs= 32768 , obs_pad= 0
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn TAO pre-track 01 : get_nwa(0)=1, d=0 , demand=732112896 , cap=736960512

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
BraseroLibburn SCSI error condition on command 2Ah WRITE(10): See MMC specs: Sense Key 3 "Medium error", ASC 10 ASCQ 00
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Libburn reported an error SCSI error on write(208,16): See MMC specs: Sense Key 3 "Medium error", ASC 10 ASCQ 00
BraseroLibburn called brasero_job_error
BraseroLibburn finished with an error
BraseroLibburn asked to stop because of an error
	error		= 1
	message	= "SCSI error on write(208,16): See MMC specs: Sense Key 3 "Medium error", ASC 10 ASCQ 00"
BraseroLibburn stopping
Session error : SCSI error on write(208,16): See MMC specs: Sense Key 3 "Medium error", ASC 10 ASCQ 00 (brasero_burn_record brasero-burn.c:2862)
```

---

### Post by jtarin on 2011-06-08
[Maybe this will help.]("http://www.downloadatoz.com/file-extensions/tutorial,12140,burn-contents-to-burn-iso-file-to-cd-on-ubuntu-11-04-with-simple-steps.html")......in otherwords....."contents".

---

### Post by Andavane on 2011-06-08
mmm thanks.
However when I tried that, nothing happened, so I went burn and got these:
attached shots listed below:


Off to the link u gave to try a 3rd CD. Funny, I never had problems with burning an *.iso for years.

Thanks for bearing with me - it;s time I started to learn what all this is about.

```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1744)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI burn:// URI found burn:///ubuntu-11.04-desktop-amd64.iso
BraseroBurnURI called brasero_job_set_current_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Information retrieval for burn:///ubuntu-11.04-desktop-amd64.iso
BraseroBurnURI Added file /home/wubithink/Desktop/ubuntu-11.04-desktop-amd64.iso at /ubuntu-11.04-desktop-amd64.iso
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
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_E9YDWV.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles Finished track successfully
BraseroChecksumFiles stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroLibburn called brasero_job_get_action
BraseroLibburn creating input
BraseroLibburn called brasero_job_get_action
BraseroLibburn unsupported operation
BraseroLibburn deactivating
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage creating input
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage deactivating
BraseroLibisofs called brasero_job_get_action
BraseroLibisofs called brasero_job_get_action
BraseroLibisofs called brasero_job_set_current_action
BraseroLibisofs creating volume
BraseroLibisofs called brasero_job_get_data_label
BraseroLibisofs called brasero_job_get_flags
BraseroLibisofs called brasero_job_get_current_track
BraseroLibisofs Adding graft disc path = /.checksum.md5, URI = file:///tmp/brasero_tmp_E9YDWV.md5
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /ubuntu-11.04-desktop-amd64.iso, URI = /home/wubithink/Desktop/ubuntu-11.04-desktop-amd64.iso
BraseroLibisofs Found parent
BraseroLibisofs called brasero_job_set_output_size_for_current_track
BraseroLibisofs called brasero_job_get_action
BraseroLibisofs Finished track successfully
BraseroLibisofs stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroLibburn called brasero_job_get_action
BraseroLibburn creating input
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_device
BraseroLibburn Drive (/dev/sr0) init result = 1
BraseroLibburn called brasero_job_get_flags
BraseroLibburn called brasero_job_get_media
BraseroLibburn called brasero_job_get_fd_in
BraseroLibburn called brasero_job_get_fd_in
BraseroLibburn called brasero_job_get_input_type
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn Setting multi 0
BraseroLibburn Setting burnproof 1
BraseroLibburn Setting dummy 0
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage linked to BraseroLibburn
BraseroChecksumImage creating input
BraseroChecksumImage called brasero_job_get_action
BraseroLibisofs called brasero_job_get_action
BraseroLibisofs linked to BraseroChecksumImage
BraseroLibisofs called brasero_job_get_action
BraseroLibisofs Entering thread
BraseroLibisofs called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroLibisofs called brasero_job_set_nonblocking
BraseroChecksumImage called brasero_job_get_
nput_type
BraseroLibisofs called brasero_job_get_fd_out
BraseroLibisofs called brasero_job_set_current_action
BraseroLibisofs called brasero_job_get_fd_out
BraseroLibisofs Writing to pipe
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage Starting checksum generation live (size = 0)
BraseroChecksumImage called brasero_job_set_nonblocking
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
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
BraseroLibburn Allocating buffer via mmap()
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn cd Profile= 09h , obs= 32768 , obs_pad= 0
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn TAO pre-track 01 : get_nwa(0)=1, d=0 , demand=732180480 , cap=736960512

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
BraseroLibburn SCSI error condition on command 5Ch READ BUFFER CAPACITY: See MMC specs: Sense Key 3 "Medium error", ASC 10 ASCQ 00
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI error condition on command 2Ah WRITE(10): [5 64 00] Illegal mode for this track
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Libburn reported an error SCSI error on write(176,16): [5 64 00] Illegal mode for this track
BraseroLibburn called brasero_job_error
BraseroLibburn finished with an error
BraseroLibburn asked to stop because of an error
	error		= 1
	message	= "SCSI error on write(176,16): [5 64 00] Illegal mode for this track"
BraseroLibisofs stopping
BraseroLibisofs Getting out thread
BraseroLibisofs disconnecting BraseroLibisofs from BraseroChecksumImage
BraseroChecksumImage stopping
BraseroChecksumImage disconnecting BraseroChecksumImage from BraseroLibburn
BraseroChecksumImage closing connection for BraseroChecksumImage
BraseroLibburn stopping
BraseroLibburn closing connection for BraseroLibburn
Session error : SCSI error on write(176,16): [5 64 00] Illegal mode for this track (brasero_burn_record brasero-burn.c:2862)
```

---

### Post by Andavane on 2011-06-08
Re the message in that link:

> This will open a dialog box letting you verify the disk type, size and burn speed. If all is correct you can click burn.

I don't get that, I get:
[IMG][[img]http://farm3.static.flickr.com/2260/5811380448_b35aed3f78.jpg[/img]](http://www.flickr.com/photos/andavane/5811380448/) [select image to write](http://www.flickr.com/photos/andavane/5811380448/) by [vasudevaram](http://www.flickr.com/people/andavane/), on Flickr[/IMG]

and I know that if I select Burn (again) it will take me back to square one (again).

If I put the *.iso on my old Sony VGN-S3HP I know it will "just do it"
but I want to find out why I apparently can't do this on my Thinkpad.

Getting confused now.

---


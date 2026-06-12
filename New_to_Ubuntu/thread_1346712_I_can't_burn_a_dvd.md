---
title: "I can't burn a dvd"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by Joentokyo on 2009-12-05
I am new to ubuntu, but I have been reading the forums, including the posted manual on using audio and video.  I have installed devede and Brasero. Devede creates an iso file with no problems, but when I try to burn the iso to a disk I get an unknown error message.](*,) Here is the log:
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1848)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_U87K4U.bin toc = none
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI burn:// URI found burn:///duplicity.iso
BraseroBurnURI called brasero_job_set_current_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI called brasero_job_add_track
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI Finished track successfully
BraseroBurnURI stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage Dummy operation, skipping
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
    -use-the-force-luke=dummy
    -use-the-force-luke=4gms
    -speed=6
    -use-the-force-luke=tracksize:924993
    -use-the-force-luke=tty
    -Z
    /dev/sr0=/home/joe/Desktop/Duplicity/duplicity.iso
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/joe/Desktop/Duplicity/duplicity.iso of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: :-( more than 50% of space will be *wasted*!
BraseroGrowisofs stderr:     use single layer media for this recording
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: HUP
BraseroGrowisofs process finished with status 252
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record brasero-burn.c:2811)

Does this indicate the problem? Why is the error unknown? Any help would be appreciated.

---

### Post by Muskegman on 2009-12-05
Install K3b from the repositories , it will work much better than brasero.


;)

---

### Post by Joentokyo on 2009-12-05
> **Muskegman said:**
> Install K3b from the repositories , it will work much better than brasero.


;)

I will try that, but some other postings indicate problems with K3b

---

### Post by 73ckn797 on 2009-12-05
I was having problems with Brasero not burning and telling me there were missing plugins. I installed "dvdauthor" from Synaptic which seems to have fixed the problem.

---

### Post by Joentokyo on 2009-12-05
> **Muskegman said:**
> Install K3b from the repositories , it will work much better than brasero.


;)
Thank you Muskegman, K3b burned the iso onto the disk, and it plays both on my computer and in my standalone dvd player!

The disk has no subtitles, but that may be due to a mistake I made when I created the iso with devede.

---

### Post by Joentokyo on 2009-12-05
> **73ckn797 said:**
> I was having problems with Brasero not burning and telling me there were missing plugins. I installed "dvdauthor" from Synaptic which seems to have fixed the problem.
Thank you; I will try that. I have already suceeded with K3b, but it never hurts to have more than one way to skin a cat.

---

### Post by 73ckn797 on 2009-12-05
> **Joentokyo said:**
> Thank you; I will try that. I have already suceeded with K3b, but it never hurts to have more than one way to skin a cat.

There have been multiple threads on this issue with Brasero. Some cannot get it working by installing dvdauthor. I never had a problem until 9.10 but others have had it even in 8.04, as you have said.

Off Topic:
Skinning cats has many variations. It all depends upon whether you are wanting to save the skin or make guitar strings or other needs/uses! I saw a book years ago titled "100 Uses For a Dead Cat". It was funny.

---


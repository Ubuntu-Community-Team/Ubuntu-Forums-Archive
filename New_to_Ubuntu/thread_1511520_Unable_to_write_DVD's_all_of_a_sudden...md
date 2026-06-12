---
title: "Unable to write DVD's all of a sudden.."
date: 2010-06-16
forum: New to Ubuntu
---

### Post by trooperchix on 2010-06-16
I've been writing DVD's for the past few days with no problem.  I ran the update manager last night, and since then have not been able to write any.  From what I can tell, it looks like something went on with the last update.  That is my guess anyway.  Any ideas?  Below is the error log contents.

```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1737)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_NYWMEV.bin toc = none
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_9ZVMEV.bin toc = none
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
	/dev/sr0=/home/eddie/Desktop/Home Movies/folsom.iso
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/eddie/Desktop/Home Movies/folsom.iso of=/dev/sr0 obs=32k seek=0'
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
BraseroGrowisofs stdout:           0/3067996160 ( 0.0%) @0x, remaining ??:?? RBU 100.0

```

---

### Post by trooperchix on 2010-06-16
K3b isn't working either.  Below is the debugging output.  I have no clue what any of it means.  Just trying to get as much information as possible in one place.  

```
Devices
-----------------------
PBDS DVD+-RW DS-8W1P BD1B (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite] [%7]

System
-----------------------
K3b Version: 1.91.0
KDE Version: 4.4.2 (KDE 4.4.2)
QT Version:  4.6.2
Kernel:      2.6.32-22-generic

Used versions
-----------------------
cdrecord: 1.1.10

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.10
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PBDS    '
Identification : 'DVD+-RW DS-8W1P '
Revision       : 'BD1B'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x001B (DVD+R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) (current)
Profile: 0x001A (DVD+RW) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1029888 = 1005 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 11080 KB/s
Track 01: data  2925 MB        
Total size:     3360 MB (332:53.93) = 1498045 sectors
Lout start:     3360 MB (332:55/70) = 1498045 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 2295104 Blocks current: 2295104 Blocks remaining: 797059
Starting to write CD/DVD at speed   8.0 in real SAO mode for single session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... Errno: 5 (Input/output error), reserve track scsi sendcmd: no error
CDB:  53 00 00 00 00 00 16 DB BD 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 55.232s timeout 200s
/usr/bin/wodim: Cannot open new session.
input buffer ready.
Writing  time:   55.287s
/usr/bin/wodim: fifo had 192 puts and 0 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=8 -sao driveropts=burnfree -data -tsize=1498045s -
```



Also, upon viewing the properties of my cd/dvd drive, this is what i get:

[IMG]http://i46.photobucket.com/albums/f115/Trooperchix/Screenshot.jpg[/IMG]

Something went terribly wrong with this last update...

---

### Post by trooperchix on 2010-06-17
bump

---

### Post by trooperchix on 2010-06-17
It doesn't matter what version of DVD burner software I use (K3b or Brasero), I am still unable to burn.  I can play DVD's just fine.  I have been doing research all over the place, and as far as I can tell, folks are thinking there is a wodim issue?  Ok, I have no clue what that is, but something is going on.  I went from burning, to doing a software update, and then not being able to burn.  Can someone walk me through troubleshooting please?  My other post regarding this is:

[http://ubuntuforums.org/showthread.php?t=1511520](http://ubuntuforums.org/showthread.php?t=1511520) 

I'm terribly frustrated.  Any help would be appreciated.

---

### Post by cariboo on 2010-06-17
Please don't create multiple threads on the same subject. I have merged your two threads.

---

### Post by trooperchix on 2010-06-21
> **cariboo907 said:**
> Please don't create multiple threads on the same subject. I have merged your two threads.

I made multiple after reading the post on how to get responses.  I see that updated post is now gone.  That didn't help.  I apologize.  I will say though that evidently there is a major wodim issue, if you peruse the posts for wodim.

Anyway, I was reading around, and here is more information.. which seemed to help other posters.  Please, someone help!!  I truly am now thinking about returning to Windows, if only to maintain full functionality of my hardware.  It's unfortunate, I have been a die hard Ubuntu convert.

```

eddie@kilimanjaro:~$ wodim -scanbus
scsibus0:
	0,0,0	  0) 'PBDS    ' 'DVD+-RW DS-8W1P ' 'BD1B' Removable CD-ROM
	0,1,0	  1) *
	0,2,0	  2) *
	0,3,0	  3) *
	0,4,0	  4) *
	0,5,0	  5) *
	0,6,0	  6) *
	0,7,0	  7) *
eddie@kilimanjaro:~$ 


```

Not sure what it means, but it looks odd to me.  Shouldn't I have just one entry if I have only just one cd/dvd burner drive?

---

### Post by lisati on 2010-07-22
> **trooperchix said:**
> I made multiple after reading the post on how to get responses.  I see that updated post is now gone.  That didn't help.  I apologize.  

From the forum [Code of Conduct]("http://ubuntuforums.org/index.php?page=policy"): > Please do not cross post, or post the same thing in multiple locations.

---

### Post by lidex on 2010-07-22
Have you tried downgrading those relevant packages? Does one of these sound familiar: [https://bugzilla.gnome.org/buglist.cgi?quicksearch=brasero](https://bugzilla.gnome.org/buglist.cgi?quicksearch=brasero)
Have you tried xfburn?

---

### Post by Zeike on 2010-07-22
Have a look at /var/log/apt/history.log and see what packages were updated & post them here.

---

### Post by trooperchix on 2010-09-12
I did a complete clean install, and am burning a DVD right now.  What I have noticed is that Brasero is not allowing me to write on DVD R+ media, even though my burner has that capability.  I'm currently burning on a DVD R-, and it hasn't completed yet.  The last time I tried to it went all the way to the end and crashed last time.  I'll give you an update to let you know if it actually completed.  Thanks for the help so far guys...

---

### Post by trooperchix on 2010-09-12
Alright.  So Brasero is having issues with media types.  I just burned an R- but it won't burn on an R+.  I've burned R+ in the past, in fact out of the same spindle, until that last update.  Again, I did a complete reinstall of Lucid, and finally I got at least a partial burn process back.  Funny thing? Never lost ability to burn CD-R's...

---

### Post by bazillion on 2010-09-12
I'm having a similar issue: since the last update my system has no sound, but more importantly, the system cannot see external media (flash drive or camera card).

I followed the advice in #9 above and got:

Start-Date: 2010-09-09  18:45:39
Upgrade: firefox-3.5-branding (3.6.8+build1+nobinonly-0ubuntu0.10.04.1, 3.6.9+build1+nobinonly-0ubuntu0.10.04.1), 
xulrunner-1.9.2 (1.9.2.8+build1+nobinonly-0ubuntu0.10.04.1, 1.9.2.9+build1+nobinonly-0ubuntu0.10.04.1), 
thunderbird (3.0.6+build2+nobinonly-0ubuntu0.10.04.1, 3.0.7+build1+nobinonly-0ubuntu0.10.04.1), 
firefox (3.6.8+build1+nobinonly-0ubuntu0.10.04.1, 3.6.9+build1+nobinonly-0ubuntu0.10.04.1), 
firefox-gnome-support (3.6.8+build1+nobinonly-0ubuntu0.10.04.1, 3.6.9+build1+nobinonly-0ubuntu0.10.04.1), 
firefox-3.0 (3.6.8+build1+nobinonly-0ubuntu0.10.04.1, 3.6.9+build1+nobinonly-0ubuntu0.10.04.1), 
firefox-3.5 (3.6.8+build1+nobinonly-0ubuntu0.10.04.1, 3.6.9+build1+nobinonly-0ubuntu0.10.04.1), 
firefox-3.0-gnome-support (3.6.8+build1+nobinonly-0ubuntu0.10.04.1, 3.6.9+build1+nobinonly-0ubuntu0.10.04.1), 
firefox-branding (3.6.8+build1+nobinonly-0ubuntu0.10.04.1, 3.6.9+build1+nobinonly-0ubuntu0.10.04.1), 
mountall (2.15.1, 2.15.2)
End-Date: 2010-09-09  18:46:51

Everything else seems to be working OK although I haven't tried to burn a CD - I've just noticed that those two functionalities are now apparently dead.

I haven't downloaded any update- or program-type stuff other than what's been listed in the Program Manager.  Any suggestions?

---

### Post by trooperchix on 2010-09-15
I also had pre-release updates enabled.  I have since done a clean install.  I'm still having the same issues.  This time I have the default update selections, no pre-release or unsupported options picked.  Just trying to give as much info as possible.

---

### Post by trooperchix on 2012-07-25
Just as a final update...  the dvd burner was good, it was a bad mother board.  Swapped it and we are all good.  :)

---


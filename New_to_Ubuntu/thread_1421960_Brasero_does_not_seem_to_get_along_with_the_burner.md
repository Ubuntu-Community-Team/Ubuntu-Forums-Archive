---
title: "Brasero does not seem to get along with the burner"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by rawdul on 2010-03-04
I just installed Ubuntu 9.10 64 bit and so far everything went well EXCEPT.... I can't get Brasero to burn a CD or DVD. An unspecified error occurs right after it begins to burn. The drive is a Plextor PX-806SA. The "Session Log" is rather long, but maybe someone can look over it and give me a hint what's going wrong? I tried to delete the package (purge) and reinstall it without effect. Many thanks!!!



> Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1848)
BraseroReadom called brasero_job_get_action
BraseroReadom getting varg
BraseroReadom called brasero_job_get_action
BraseroReadom called brasero_job_get_output_type
BraseroReadom called brasero_job_get_current_track
BraseroReadom called brasero_job_set_output_size_for_current_track
BraseroReadom got varg:
BraseroReadom stopping
BraseroReadom called brasero_job_get_action
BraseroReadom called brasero_job_get_session_output_size
BraseroReadom output set (IMAGE) image = /tmp/brasero_tmp_GF278U toc = /tmp/brasero_tmp_GF278U.toc
BraseroReadom getting varg
BraseroReadom called brasero_job_get_action
BraseroReadom called brasero_job_get_current_track
BraseroReadom called brasero_job_get_output_type
BraseroReadom called brasero_job_get_fd_out
BraseroReadom called brasero_job_get_image_output
BraseroReadom called brasero_job_set_use_average_rate
BraseroReadom got varg:
    readom
    dev=/dev/sr0
    -nocorr
    -clone
    -f=/tmp/brasero_tmp_GF278U
BraseroReadom Launching command
BraseroReadom stderr: Read  speed:  8468 kB/s (CD  48x, DVD  6x).
BraseroReadom stderr: Write speed:  8468 kB/s (CD  48x, DVD  6x).
BraseroReadom stderr: TOC len: 70. First Session: 1 Last Session: 1.
BraseroReadom stderr: 01 14 00 A0 00 00 00 00 01 00 00 
BraseroReadom stderr: 01 14 00 A1 00 00 00 00 01 00 00 
BraseroReadom stderr: 01 14 00 A2 00 00 00 00 0E 37 2F 
BraseroReadom stderr: 01 14 00 01 00 00 00 00 00 02 00 
BraseroReadom stderr: 01 54 00 B0 11 19 2F 02 4F 3B 4A 
BraseroReadom stderr: 01 54 00 C0 A0 00 40 00 61 11 06 
BraseroReadom stderr: Lead out 1: 67022
BraseroReadom stderr: Capacity: 67020 Blocks = 134040 kBytes = 130 MBytes = 137 prMB
BraseroReadom called brasero_job_set_current_action
BraseroReadom stderr: Sectorsize: 2048 Bytes
BraseroReadom stderr: Errno: 5 (Input/output error), mode select g1 scsi sendcmd: no error
BraseroReadom stderr: CDB:  55 10 00 00 00 00 00 00 14 00
BraseroReadom stderr: status: 0x2 (CHECK CONDITION)
BraseroReadom stderr: Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 26 00 00 00
BraseroReadom stderr: Sense Key: 0x5 Illegal Request, Segment 0
BraseroReadom stderr: Sense Code: 0x26 Qual 0x00 (invalid field in parameter list) Fru 0x0
BraseroReadom stderr: Sense flags: Blk 0 (not valid) 
BraseroReadom stderr: cmd finished after 0.001s timeout 40s
BraseroReadom stderr: Copy from SCSI (2,0,0) disk to file '/tmp/brasero_tmp_GF278U'
BraseroReadom stderr: end:     67020
BraseroReadom stderr: addr:        0 cnt: 53 
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:       53 cnt: 53 
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6837 cnt: 53 
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    67020

... this goes on for many, many more different addrs ....

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: Time total: 37.386sec
BraseroReadom stderr: Read 160219.69 kB at 4285.6 kB/sec.
BraseroReadom stderr: HUP
BraseroReadom process finished with status 0
BraseroReadom called brasero_job_get_fd_out
BraseroReadom called brasero_job_get_action
BraseroReadom called brasero_job_get_output_type
BraseroReadom called brasero_job_get_image_output
BraseroReadom called brasero_job_get_session_output_size
BraseroReadom called brasero_job_add_track
BraseroReadom called brasero_job_get_action
BraseroReadom Finished track successfully
BraseroReadom got killed
BraseroReadom stopping
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1848)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_ORKB9U toc = /tmp/brasero_tmp_ORKB9U.toc
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
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
    speed=32
    driveropts=burnfree
    -raw96r
    fs=16m
    -clone
    /tmp/brasero_tmp_GF278U
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
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
BraseroWodim stderr: wodim: Clone writing TOC length 67022 does not match track length 67020
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Device type    : Removable CD-ROM
BraseroWodim stdout: Version        : 5
BraseroWodim stdout: Response Format: 2
BraseroWodim stdout: Capabilities   : 
BraseroWodim stdout: Vendor_info    : 'PLEXTOR '
BraseroWodim stdout: Identification : 'DVDR   PX-806SA '
BraseroWodim stdout: Revision       : '1.06'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0018 (Reserved/Unknown) 
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
BraseroWodim stderr: HUP
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stdout: Encoding speed : 1000x (75000 sectors/s) for libedc from Heiko Ei
BraseroWodim stdout: HUP
BraseroWodim process finished with status 255
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroWodim stopping
BraseroWodim got killed
Session error : unknown (brasero_burn_record brasero-burn.c:2811)

---

### Post by Jazzy_Jeff on 2010-03-04
You might want to try another cd/dvd burning software and see if that works. I use k3b and it works great all the time.

---

### Post by 73ckn797 on 2010-03-04
Look in Synaptic Package Manager and install "dvdauthor". That may solve your problem.

---

### Post by ndefontenay on 2010-03-04
Hi.

I had the same problem and someone mentioned reducing the speed from max speed to the next available. It worked for me.

Nico

---

### Post by rawdul on 2010-03-05
First, thank you for the quick and friendly (this isn't Windows any more... !!!) advise. I first lowered the write speed in brasero to 16x - still the same error. I then installed K3b. The process went along further, but an error occurred in the final stage (when Nero would say it's writing the lead-out), resulting in an unusable CD. I then lowered the write speed to 16x and .... although it takes about 2 minutes just to finalize the CD (after writing the content) it produces a working CD! Thank you very much for your help :p.

---

### Post by PPPilot on 2010-03-05
Go to the Applications Menu, Select Ubuntu Software Center, Once it opens, Select Sound & Video. Scroll down to K3b and install it. That burner will work for you.... Just un-install Brasero...

---

### Post by Leslea_kate on 2010-03-07
Tried Brassero, tried K3b, tried slow speeds, nothing's working.  Not even going back to trying 19 instead of 20...

I even put a different DVD burner in the machine & NO difference.  HELP!

---

### Post by madmax75 on 2010-03-07
I've also had numerous troubles with Brasero.

Nowadays I use **Xfburn**. Small, fast, uncomplicated, does the job. I recommend it heartily! It is in the repositories.

---

### Post by 73ckn797 on 2010-03-07
> **73ckn797 said:**
> Look in Synaptic Package Manager and install "dvdauthor". That may solve your problem.
Has anyone tried my recommendation? My Brasero problems were solved via this.

---

### Post by Leslea_kate on 2010-04-10
Tried DVD author.  Couldn't even get the damn thing to do anything.

---

### Post by Leslea_kate on 2010-04-10
Tried XFburn & didn't work either.

---

### Post by lidex on 2010-04-10
> **Leslea_kate said:**
> Tried DVD author.  Couldn't even get the damn thing to do anything.
I believe what he's saying is the dvd author installation process may fix brasero, not to use it to burn with.

---

### Post by lidex on 2010-04-10
> **Leslea_kate said:**
> Tried DVD author.  Couldn't even get the damn thing to do anything.
I believe what 73ckn797 is saying is the dvd author installation process may fix brasero, not to use it to burn with.

---

### Post by Leslea_kate on 2010-04-11
Tried both options folks.  No joy.

So I said screw it.  Backed up the essential bits, took some notes on the programs I've installed to tiddly my OS just the way I like it & then wiped it.  Reloaded with 9.04 Jackalope.

NO more burning problems.  Burners work fine now (both of em).  There's something whacked with 9.10 to make the burners not cooperate.  It also conflicted a bit with my video card (it's an older 128 Mb ATI card).  Something that's a non-issue with 9.04.

I spent less time reloading 9.04, than I did trying to make 9.10 cooperate.  What a pain that was.

Leslea

---

### Post by lidex on 2010-04-11
> **Leslea_kate said:**
> Tried both options folks.  No joy.

So I said screw it.  Backed up the essential bits, took some notes on the programs I've installed to tiddly my OS just the way I like it & then wiped it.  Reloaded with 9.04 Jackalope.

NO more burning problems.  Burners work fine now (both of em).  There's something whacked with 9.10 to make the burners not cooperate.  It also conflicted a bit with my video card (it's an older 128 Mb ATI card).  Something that's a non-issue with 9.04.

I spent less time reloading 9.04, than I did trying to make 9.10 cooperate.  What a pain that was.

Leslea

Yeah, I just skipped karmic altogether. Pretty happy with jaunty. Been testing lucid - it looks like a keeper.

---

### Post by Leslea_kate on 2010-12-20
The good news is this is so far, not an issue with 10.10.  :)

---

### Post by amjjawad on 2010-12-20
It could be a hardware issue not a software issue.

---


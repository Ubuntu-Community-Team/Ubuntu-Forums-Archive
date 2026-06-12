---
title: "Can't burn DVD"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-07-28
When I try and use brasero I get a message saying that I need to replace the disk with a supported CD or DVD. It also tells me that I need "it is not possible to write with the current set of plugins."

I already have all the medibuntu stuff. I am able to burn cds, and play dvds. I can also burn isos onto dvds but I can't burn a video onto a dvd. The video is an mpeg4. There are also .avi and .wmv files. 

What do I need to do?

---

### Post by HotShotDJ on 2009-07-28
I suspect that you are trying to burn the video files using the "Video Project" button.  If you are trying to create a Video DVD, you'll need to convert the video files to the proper DVD format (VOB) first -- I use Q DVD Author for that (see: [https://help.ubuntu.com/community/DVDAuthoring](https://help.ubuntu.com/community/DVDAuthoring) for a comprehensive list of software for authoring video DVD's).  However, if you are just trying to create a DVD with the various video files on it for use on your computer(s), you'll want to create a Data Project and just burn the mp4, wmv, avi, etc. files just as you would any other set of data files.

---

### Post by Sup3r3g0 on 2009-07-28
thanks I'll try Q DVD author

---

### Post by halitech on 2009-07-28
you can also use Devede to create an iso of the video files with a menu

---

### Post by Sup3r3g0 on 2009-07-30
I'm still having trouble burning a dvd. Even if I try and use Brasero to burn a data disk, it continues to give an error. Should I post the log file it gives after the error?

---

### Post by nhasian on 2009-07-30
you can run the program from a terminal with the command:

```
brasero
```

then you can copy/paste any errors the terminal shows when you try to burn a disc.

---

### Post by Sup3r3g0 on 2009-07-30
Error Log
```

Checking session consistency (brasero_burn_check_session_consistency burn.c:1956)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI called brasero_job_get_input_type
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs Using genisoimage
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-dvd-compat
	-speed=7
	-use-the-force-luke=tty
	-Z
	/dev/scd0
	-dry-run
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-path-list
	/tmp/brasero_tmp_8QEYXU
	-exclude-list
	/tmp/brasero_tmp_G4UXXU
	-print-size
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_8QEYXU -exclude-list /tmp/brasero_tmp_G4UXXU -print-size | builtin_dd of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Total extents scheduled to be written = 2126895
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_output_size_for_current_track
BraseroGrowisofs finished successfully session
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs Using genisoimage
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_data_label
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-dvd-compat
	-speed=7
	-use-the-force-luke=tracksize:2126895
	-use-the-force-luke=tty
	-Z
	/dev/scd0
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-path-list
	/tmp/brasero_tmp_JJ4UXU
	-exclude-list
	/tmp/brasero_tmp_6DBVXU
	-V
	Data disc (30 Jul 09)
	-A
	Brasero-0.9.1
	-sysid
	LINUX
	-v
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stderr: genisoimage 1.1.8 (Linux)
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_JJ4UXU -exclude-list /tmp/brasero_tmp_6DBVXU -V Data disc (30 Jul 09) -A Brasero-0.9.1 -sysid LINUX -v | builtin_dd of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Writing:   Initial Padblock                        Start Block 0
BraseroGrowisofs stderr: Done with: Initial Padblock                        Block(s)    16
BraseroGrowisofs stderr: Writing:   Primary Volume Descriptor               Start Block 16
BraseroGrowisofs stderr: Done with: Primary Volume Descriptor               Block(s)    1
BraseroGrowisofs stderr: Writing:   Joliet Volume Descriptor                Start Block 17
BraseroGrowisofs stderr: Done with: Joliet Volume Descriptor                Block(s)    1
BraseroGrowisofs stderr: Writing:   End Volume Descriptor                   Start Block 18
BraseroGrowisofs stderr: Done with: End Volume Descriptor                   Block(s)    1
BraseroGrowisofs stderr: Writing:   Version block                           Start Block 19
BraseroGrowisofs stderr: Done with: Version block                           Block(s)    1
BraseroGrowisofs stderr: Writing:   Path table                              Start Block 20
BraseroGrowisofs stderr: Done with: Path table                              Block(s)    4
BraseroGrowisofs stderr: Writing:   Joliet path table                       Start Block 24
BraseroGrowisofs stderr: Done with: Joliet path table                       Block(s)    4
BraseroGrowisofs stderr: Writing:   Directory tree                          Start Block 28
BraseroGrowisofs stderr: Done with: Directory tree                          Block(s)    1
BraseroGrowisofs stderr: Writing:   Joliet directory tree                   Start Block 29
BraseroGrowisofs stderr: Done with: Joliet directory tree                   Block(s)    1
BraseroGrowisofs stderr: Writing:   Directory tree cleanup                  Start Block 30
BraseroGrowisofs stderr: Done with: Directory tree cleanup                  Block(s)    0
BraseroGrowisofs stderr: Writing:   Extension record                        Start Block 30
BraseroGrowisofs stderr: Done with: Extension record                        Block(s)    1
BraseroGrowisofs stderr: Writing:   The File(s)                             Start Block 31
BraseroGrowisofs stderr:   0.24% done, estimate finish Thu Jul 30 17:57:59 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   0.47% done, estimate finish Thu Jul 30 18:01:31 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   0.71% done, estimate finish Thu Jul 30 18:00:20 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/scd0: engaging DVD-R DAO upon user request...
BraseroGrowisofs stderr: :-[ PERFORM OPC failed with SK=5h/COMMAND SEQUENCE ERROR]: Input/output error
BraseroGrowisofs stderr: /dev/scd0: reserving 2126895 blocks
BraseroGrowisofs stderr: /dev/scd0: "Current Write Speed" is 8.2x1352KBps.
BraseroGrowisofs stderr: :-[ WRITE@LBA=10h failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs stderr: /dev/scd0: flushing cache
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record burn.c:2653)

```

---

### Post by claypole on 2009-11-22
Try upgrading the DVDRW firmware [http://ubuntuforums.org/showthread.php?t=915674](http://ubuntuforums.org/showthread.php?t=915674)

---

### Post by kennedyjch on 2009-11-25
I've had similar problems. I'm trying to make data CDs/DVDs. Burning DVDs was impossible and CD was problematic. First, I cleaned the DVD writer with a cleaning disk and I was able to successfully burn CDs; DVDs still get HUP error. I burn and it still says disk is blank. I tried K3B and this seemed to give a better success with CDs but DVDs still got errors. 

I was using DVD-R discs; now I purchased DVD-RW and surprisingly I can now burn data DVDs without errors and load the DVD in and actually read it.

There is a firmware update for my DVD but I cannot apply it as the "burner" software is only available for window$...

---

### Post by topcause on 2009-11-25
I have the same problem. I can read DVDs with no problem but can not burn using Linux. I have no problem in windows.  I have tried different media and same results. I have also tired different applications and no luck yet.
# hdparm -i /dev/dvd
/dev/dvd:
Model=HL-DT-ST DVDRAM GH40L , FwRev=LM02 , SerialNo=684BEE7A70DA 
Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
BuffType=unknown, BuffSize=0kB, MaxMultSect=0
(maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
PIO modes: pio0 pio3 pio4 
DMA modes: mdma0 mdma1 mdma2 
UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
AdvancedPM=no
Drive conforms to: unknown: ATA/ATAPI-3,4,5,6,7

---

### Post by Tholley on 2009-11-25
There have been a MULTITUDE of problems with Brasero. It's really sucks and is silly Ubuntu puts it as default.
 
With that said...
 
I use DeVeDe to burn as ISO image and then K3B to rip the ISO to DVD.
 
It works the best for me. 
 
Unfortunetly, Ubuntu doesn't seem to have a good all in one app.
 
Hope this helps...

---

### Post by claypole on 2009-11-26
Install the latest version of WINE from [www.winehq.org](www.winehq.org) and run the Windows version of the firmware updater. This worked great for me.

---

### Post by rogerp1 on 2009-11-26
Forget Brasero....install k3b

---

### Post by sadinsudin on 2009-12-23
hi there..here I just want to share my experience when facing the same problems...last time I don't care to look what type of dvd that i wanted to burn either data or iso. Actually there are many types of dvd out there for instance DVD+R, DVD-R, DVD-RW and many more (read wiki..)..To cut it short I think you should  identify what type of dvd that you use now and if it still can not be burnt why not you try another type of dvd...for my case my machine can't burn the DVD-R but I have no problem to burn any kind of data on the DVD+R..hope this help

---

### Post by extremepoors on 2009-12-23
Try to install ubuntu with Memory Stick.


I can't boot from my dvd reader/burner, i have installed it with Memory Stick.


First, buy an 1GB Memory Stick (Kingston).

Then download Ubuntu 9.10 (Karmic Koala) .ISO.

Then download Unetbootin.

Then open unetbootin and click on diskimage, then search for the ubuntu's iso and open it on unetbootin.

Then select your memory stick from the drive list, then click ok.


Wait for it be completed and then restart your computer.

It says all time: "Click delete to go on bios" or something like this, press the key what it wants to press.

Then go to boot and find kingstondatatraveler2.0, get it to the first place.

Then save anything and restart your computer.


Then you can install ubuntu!:)

---

### Post by extremepoors on 2009-12-23
> **extremepoors said:**
> Try to install ubuntu with Memory Stick.


I can't boot from my dvd reader/burner, i have installed it with Memory Stick.


First, buy an 1GB Memory Stick (Kingston).

Then download Ubuntu 9.10 (Karmic Koala) .ISO.

Then download Unetbootin.

Then open unetbootin and click on diskimage, then search for the ubuntu's iso and open it on unetbootin.

Then select your memory stick from the drive list, then click ok.


Wait for it be completed and then restart your computer.

It says all time: "Click delete to go on bios" or something like this, press the key what it wants to press.

Then go to boot and find kingstondatatraveler2.0, get it to the first place.

Then save anything and restart your computer.


Then you can install ubuntu!:)Whoops, sorry i do not looked what you posted and sended this guide :( i thinked you was trying to boot from dvd :(

---


---
title: "CD/DVD Creator - &quot;unknown error&quot;"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by solarpenguin on 2010-11-13
Whenever I try to write a data DVD I always get an error, usually "an unknown error".  Does anyone, uh, know what this unknown error is?  If so, how do I fix it?

If it helps, I can post the session log from the last time it happened.

One thing that might complicate things is that this is a second hand computer that came with Ubuntu already installed (and I stuck with it since I'm not geeky enough to know how to remove it and replace it with proper Windows.)  So, because I've never been able to test burning with this DVD drive under a different system, I've no idea whether the fault is with Ubuntu or a genuine hardware error in the drive itself.

Any suggestions?

---

### Post by taseedorf on 2010-11-13
/var/log/apport.log

there may be an explanation in there, or check the other logs...
[http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/)

---

### Post by solarpenguin on 2010-11-13
> **taseedorf said:**
> /var/log/apport.log

there may be an explanation in there, or check the other logs...
[http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/)

Thanks for the quick reply.  I'm afraid I didn't quite understand it.

Is that "var and/or apport.log" stuff at the beginning supposed to mean anything?  If so, what?

"An explanation in there"?  In where?

I did check the webpage you recommended, but I didn't understand that either.  Can you recommend one in plain English instead?

Sorry, like I said, I really don't understand all the geeky stuff.  The one thing I did understand from your post is that the logs can be useful.  At least I think that's what you were trying to say.  Sorry if I've got that wrong.

Anyway, just in case you do want logs, here's the most recent session log:

[I]Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1737)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI burn:// URI found burn:///Kiss%20Me%20and%20Die.tar.gz
BraseroBurnURI called brasero_job_set_current_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Information retrieval for burn:///Kiss%20Me%20and%20Die.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/Kiss Me and Die.tar.gz at /Kiss Me and Die.tar.gz
BraseroBurnURI Information retrieval for burn:///An%20Echo%20of%20Theresa.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/An Echo of Theresa.tar.gz at /An Echo of Theresa.tar.gz
BraseroBurnURI Information retrieval for burn:///K%20is%20for%20Killing.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/K is for Killing.tar.gz at /K is for Killing.tar.gz
BraseroBurnURI Information retrieval for burn:///Come%20Out%20Come%20Out%20Wherever%20You%20Are.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/Come Out Come Out Wherever You Are.tar.gz at /Come Out Come Out Wherever You Are.tar.gz
BraseroBurnURI Information retrieval for burn:///I'm%20the%20Girl%20He%20Wants%20to%20Kill.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/I'm the Girl He Wants to Kill.tar.gz at /I'm the Girl He Wants to Kill.tar.gz
BraseroBurnURI Information retrieval for burn:///If%20It's%20a%20Man%20-%20Hang%20Up.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/If It's a Man - Hang Up.tar.gz at /If It's a Man - Hang Up.tar.gz
BraseroBurnURI Information retrieval for burn:///Lady%20Killer.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/Lady Killer.tar.gz at /Lady Killer.tar.gz
BraseroBurnURI Information retrieval for burn:///In%20the%20Steps%20of%20a%20Dead%20Man.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/In the Steps of a Dead Man.tar.gz at /In the Steps of a Dead Man.tar.gz
BraseroBurnURI Information retrieval for burn:///Death%20to%20Sister%20Mary.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/Death to Sister Mary.tar.gz at /Death to Sister Mary.tar.gz
BraseroBurnURI Information retrieval for burn:///Death%20in%20Deep%20Water.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/Death in Deep Water.tar.gz at /Death in Deep Water.tar.gz
BraseroBurnURI Information retrieval for burn:///Double%20Kill.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/Double Kill.tar.gz at /Double Kill.tar.gz
BraseroBurnURI Information retrieval for burn:///Death%20Day.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/Death Day.tar.gz at /Death Day.tar.gz
BraseroBurnURI Information retrieval for burn:///Level%20Seven.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/Level Seven.tar.gz at /Level Seven.tar.gz
BraseroBurnURI Information retrieval for burn:///File%20it%20Under%20Fear.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/File it Under Fear.tar.gz at /File it Under Fear.tar.gz
BraseroBurnURI Information retrieval for burn:///A%20Killer%20in%20Every%20Corner.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/A Killer in Every Corner.tar.gz at /A Killer in Every Corner.tar.gz
BraseroBurnURI Information retrieval for burn:///Dead%20Past.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/Dead Past.tar.gz at /Dead Past.tar.gz
BraseroBurnURI Information retrieval for burn:///A%20Place%20to%20Die.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/A Place to Die.tar.gz at /A Place to Die.tar.gz
BraseroBurnURI Information retrieval for burn:///A%20Midsummer%20Nightmare.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/A Midsummer Nightmare.tar.gz at /A Midsummer Nightmare.tar.gz
BraseroBurnURI Information retrieval for burn:///Killer%20with%20Two%20Faces.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/Killer with Two Faces.tar.gz at /Killer with Two Faces.tar.gz
BraseroBurnURI Information retrieval for burn:///Good%20Salary%20-%20Prospects%20-%20Free%20Coffin.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/Good Salary - Prospects - Free Coffin.tar.gz at /Good Salary - Prospects - Free Coffin.tar.gz
BraseroBurnURI Information retrieval for burn:///Crazy%20Kill.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/Crazy Kill.tar.gz at /Crazy Kill.tar.gz
BraseroBurnURI Information retrieval for burn:///Kill%20Two%20Birds.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/Kill Two Birds.tar.gz at /Kill Two Birds.tar.gz
BraseroBurnURI Information retrieval for burn:///Dial%20a%20Deadly%20Number.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/Dial a Deadly Number.tar.gz at /Dial a Deadly Number.tar.gz
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
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_NG9VLV.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles Finished track successfully
BraseroChecksumFiles stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs Using genisoimage
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
    growisofs
    -use-the-force-luke=notray
    -use-the-force-luke=4gms
    -dvd-compat
    -speed=8
    -use-the-force-luke=tty
    -Z
    /dev/sr0
    -dry-run
    -r
    -J
    -input-charset
    utf8
    -graft-points
    -path-list
    /tmp/brasero_tmp_MJMKLV
    -exclude-list
    /tmp/brasero_tmp_S9LKLV
    -print-size
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs called brasero_job_get_fd_iummer Nightmare.tar.gz
BraseroBurnURI Information retrieval for burn:///Killer%20with%20Two%20Faces.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/Killer with Two Faces.tar.gz at /Killer with Two Faces.tar.gz
BraseroBurnURI Information retrieval for burn:///Good%20Salary%20-%20Prospects%20-%20Free%20Coffin.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/Good Salary - Prospects - Free Coffin.tar.gz at /Good Salary - Prospects - Free Coffin.tar.gz
BraseroBurnURI Information retrieval for burn:///Crazy%20Kill.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/Crazy Kill.tar.gz at /Crazy Kill.tar.gz
BraseroBurnURI Information retrieval for burn:///Kill%20Two%20Birds.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/Kill Two Birds.tar.gz at /Kill Two Birds.tar.gz
BraseroBurnURI Information retrieval for burn:///Dial%20a%20Deadly%20Number.tar.gz
BraseroBurnURI Added file /home/paul/Videos/Downloaded/Dial a Deadly Number.tar.gz at /Dial a Deadly Number.tar.gz
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
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_NG9VLV.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles Finished track successfully
BraseroChecksumFiles stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs Using genisoimage
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
    growisofs
    -use-the-force-luke=notray
    -use-the-force-luke=4gms
    -dvd-compat
    -speed=8
    -use-the-force-luke=tty
    -Z
    /dev/sr0
    -dry-run
    -r
    -J
    -input-charset
    utf8
    -graft-points
    -path-list
    /tmp/brasero_tmp_MJMKLV
    -exclude-list
    /tmp/brasero_tmp_S9LKLV
    -print-size
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_MJMKLV -exclude-list /tmp/brasero_tmp_S9LKLV -print-size | builtin_dd of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Total extents scheduled to be written = 2153444
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_output_size_for_current_track
BraseroGrowisofs Finished successfully session
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
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs Using genisoimage
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_data_label
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
    growisofs
    -use-the-force-luke=notray
    -use-the-force-luke=4gms
    -dvd-compat
    -speed=8
    -use-the-force-luke=tracksize:2153444
    -use-the-force-luke=tty
    -Z
    /dev/sr0
    -r
    -J
    -input-charset
    utf8
    -graft-points
    -path-list
    /tmp/brasero_tmp_6ATTLV
    -exclude-list
    /tmp/brasero_tmp_HFTTLV
    -A
    Brasero-2.30.0
    -sysid
    LINUX
    -v
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_6ATTLV -exclude-list /tmp/brasero_tmp_HFTTLV -A Brasero-2.30.0 -sysid LINUX -v | builtin_dd of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: genisoimage 1.1.10 (Linux)
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
BraseroGrowisofs stderr: Done with: Directory tree                          Block(s)    2
BraseroGrowisofs stderr: Writing:   Joliet directory tree                   Start Block 30
BraseroGrowisofs stderr: Done with: Joliet directory tree                   Block(s)    2
BraseroGrowisofs stderr: Writing:   Directory tree cleanup                  Start Block 32
BraseroGrowisofs stderr: Done with: Directory tree cleanup                  Block(s)    0
BraseroGrowisofs stderr: Writing:   Extension record                        Start Block 32
BraseroGrowisofs stderr: Done with: Extension record                        Block(s)    1
BraseroGrowisofs stderr: Writing:   The File(s)             
[/I]

I've no idea what any of that's supposed to mean.  But hopefully someone can translate it for me.

---

### Post by solarpenguin on 2010-11-19
Bumping this thread in case someone else can help.

---

### Post by solarpenguin on 2010-11-23
Bump again.

---

### Post by col48 on 2010-11-23
I can't help substantially but I think taseedorf meant look in the log found at

/var/log/apport.log

My system is Ubuntu 8.04.
This log file does not exist on my system - at least, not in the /var/log directory.

---

### Post by solarpenguin on 2010-12-06
> **col48 said:**
> I can't help substantially but I think taseedorf meant look in the log found at

/var/log/apport.log

My system is Ubuntu 8.04.
This log file does not exist on my system - at least, not in the /var/log directory.

Thanks.  I don't seem to have one on my system either.

BTW I'm assuming that by "/var/log/apport.log" you mean *"Click on Places menu, then click on Computer option, then on File System, then var, then log, and then finally on apport.log if it exists."  *(It's taken a lot of trial and error, but think I've ***finally** *worked out that this seems to be what you people mean when you say "/this/that/whatever".)

Anyway assuming that's what you mean, then like I said, it doesn't look like I have an apport.log there.  Is that what's causing the problem?  Does my computer need to get one from somewhere before I can write DVDs?  If so, where can I download one?  (There doesn't seem to be one listed in the Synaptic repositories.)

---

### Post by mikechant on 2010-12-06
I've sometimes received odd errors at the end of the burn process but still got a working DVD. Does this error seem to happen at the end of the process, and if so have you tried the DVD to see if it works regardless of the error?

Also, I seem to remember there are some problems with CD/DVD burning in Ubuntu 10.10 - is that the version you are running?

As for the log file, it's not something you need to obtain, it's something that would be written by the 'apport' program which is a crash reporting program if it was activated. As the application seems to be issueing an error message rather than crashing I'm not sure that it's relevant.

---


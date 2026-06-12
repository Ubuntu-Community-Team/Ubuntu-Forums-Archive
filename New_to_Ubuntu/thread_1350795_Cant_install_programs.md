---
title: "Cant install programs"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by Zundap on 2009-12-09
Hi, could anyone please help? 

I have been trying to install frostwire, but i get the error message. **"   	** 	 	 	 	 	  **Only one software management tool is allowed to run at the same time**
 [B]please close the other application eg: update manager aptitude or synaptic first" 
[/B]


I have had the same trouble trying to install other software also**, **i am running ubuntu 9.04


Thanks

---

### Post by candtalan on 2009-12-09
You can only run one of these at a time - 
1) applications>add/remove[....]

or 

2) System>Admnistration>synaptic package manager

(not both at once)

running something in a terminal such as apt-get will probably also count as one item, too, or a package installer such as gdebi (?)

---

### Post by audiomick on 2009-12-09
you seem to have  two instances of aptitude running.
What are you doing, exactly, when you try and install something?

---

### Post by Zundap on 2009-12-09
Thanks for the replies.

I have downloaded frostwire and i am trying to install it, i get this problem everytime i try to install a program. I have shut down and rebooted, but i still get that message.

---

### Post by wojox on 2009-12-09
Copy and paste this in your terminal:

```
top -b -n 1 > top.txt
```

It will create a top.txt file in your home directory and load it up here.

---

### Post by Zundap on 2009-12-09
i Dont understand what you mean by "load it up here? Could you explain how i do that, Thanks

---

### Post by audiomick on 2009-12-09
open the text file, copy the text, and past it with "code" tags in a post  here.

---

### Post by Zundap on 2009-12-09
I have copied pasted the code in to the terminal, but nothing happens, it just brings up another prompt.

---

### Post by vanhelsing2009 on 2009-12-10
[SIZE="5"]well he did not mean to paste code in ur terminal
but paste it here to figure out what is going on ur pc
[/SIZE]

---

### Post by cholericfun on 2009-12-10
> **vanhelsing2009 said:**
> [SIZE="5"]well he did not mean to paste code in ur terminal
but paste it here to figure out what is going on ur pc
[/SIZE]

this thread is 22h old - no need to shout...
prob update manager running?

---

### Post by beetleman64 on 2009-12-10
It probably means that you have update manager running in the background. Go to System>Administration>Update manager and then click the close button. If that doesn't work then try restarting the computer. If that doesn't work then you'll have to ask someone else.

---

### Post by cholericfun on 2009-12-11
> I have copied pasted the code in to the terminal, but nothing happens, it just brings up another prompt.

by the way this "top" command just lists the active applications ">" means tunnel the output somewhere and "top.txt" is the text file where they'll go. you just see another prompt because the output has been written to a txt file.
you just open the textfile and paste the content here...
the idea is to see if some other packet manager is working.
alternativly you just wait a bit... i guess the "problem" fixed itself by now.

---

### Post by Zundap on 2009-12-12
Is this the relevant file?                           > Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_1GNI3U.bin toc = none
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI called brasero_job_get_input_type
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_K50I3U.bin toc = none
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
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
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_O2ZK3U.bin toc = none
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /home/allen/Desktop/ubuntu-9.10-desktop-i386.iso (size = 723488768)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 8790491bfa9d00f283ed9dd2d77b3906 ( before)
BraseroChecksumImage Finished track successfully
BraseroChecksumImage stopping
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
    -dao
    fs=16m
    -data
    -nopad
    /home/allen/Desktop/ubuntu-9.10-desktop-i386.iso
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
BraseroWodim stdout: Device type    : Removable CD-ROM
BraseroWodim stdout: Version        : 5
BraseroWodim stdout: Response Format: 2
BraseroWodim stdout: Capabilities   : 
BraseroWodim stdout: Vendor_info    : 'PIONEER '
BraseroWodim stdout: Identification : 'DVD-RW  DVR-112D'
BraseroWodim stdout: Revision       : '1.21'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0016 (DVD-R/DL layer jump recording) 
BraseroWodim stdout: Profile: 0x0015 (DVD-R/DL sequential recording) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
BraseroWodim stdout: Drive buf size : 1267712 = 1238 KB
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 7056 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   689 MB        
BraseroWodim stdout: Total size:      792 MB (78:30.21) = 353266 sectors
BraseroWodim stdout: Lout start:      792 MB (78:32/16) = 353266 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 5
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is not erasable
BraseroWodim stdout:   Disk sub type: Medium Type B, low Beta category (B-) (4)
BraseroWodim stdout:   ATIP start of lead in:  -11607 (97:27/18)
BraseroWodim stdout:   ATIP start of lead out: 359849 (79:59/74)
BraseroWodim stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
BraseroWodim stdout: Manuf. index: 18
BraseroWodim stdout: Manufacturer: Plasmon Data systems Ltd.
BraseroWodim stdout: Blocks total: 359849 Blocks current: 359849 Blocks remaining: 6583
BraseroWodim stdout: Starting to write CD/DVD at speed  40.0 in real SAO mode for single session.
BraseroWodim stdout: Last chance to quit, starting real write in    4 seconds.#
BraseroWodim called brasero_job_set_dangerous
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout:    3 seconds.#
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout:    2 seconds.#
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout: #
BraseroWodim stdout:    1 seconds.#############   0 seconds. Operation starts.
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Performing OPC...
BraseroWodim stdout: Sending CUE sheet...
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Writing pregap for track 1 at -150
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stdout: 
BraseroWodim stdout: Track 01:    0 of  689 MB written.
BraseroWodim stdout: Track 01:    1 of  689 MB written (fifo  99%) [buf  94%]   0.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    2 of  689 MB written (fifo  99%) [buf  92%]  17.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    3 of  689 MB written (fifo  99%) [buf  92%]  18.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    4 of  689 MB written (fifo 100%) [buf  85%]  16.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    5 of  689 MB written (fifo  99%) [buf  93%]  20.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    6 of  689 MB written (fifo 100%) [buf  86%]  16.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    7 of  689 MB written (fifo 100%) [buf  89%]  19.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    8 of  689 MB written (fifo 100%) [buf  87%]  17.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    9 of  689 MB written (fifo 100%) [buf  94%]  20.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   10 of  689 MB written (fifo  99%) [buf  91%]  17.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   11 of  689 MB written (fifo  99%) [buf  95%]  19.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   12 of  689 MB written (fifo 100%) [buf  86%]  16.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   13 of  689 MB written (fifo 100%) [buf  87%]  19.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   14 of  689 MB written (fifo  99%) [buf  98%]  20.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   15 of  689 MB written (fifo  99%) [buf  98%]  19.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   16 of  689 MB written (fifo 100%) [buf  89%]  16.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   17 of  689 MB written (fifo  99%) [buf  89%]  19.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   18 of  689 MB written (fifo  99%) [buf  99%]  20.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   19 of  689 MB written (fifo  99%) [buf  98%]  19.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   20 of  689 MB written (fifo 100%) [buf  88%]  16.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   21 of  689 MB written (fifo  99%) [buf  87%]  18.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   22 of  689 MB written (fifo 100%) [buf  96%]  20.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 00 00 2E 42 00 00 1F 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 05 04 93 00 00 0E 26 08 10 FE A8 03 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x5 Illegal Request, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0xA8 Qual 0x03 (vendor unique sense code 0xA8) [No matching qualifier] Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 76742656 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.007s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: A write error occured.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Please properly read the error message above.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01:   23 of  689 MB written (fifo  99%) [buf  97%]  16.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: write track data: error after 24252416 bytes
BraseroWodim stdout: Writing  time:   44.230s
BraseroWodim stdout: Average write speed 163.7x.
BraseroWodim stdout: Min drive buffer fill was 85%
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Fixating time:    2.260s
BraseroWodim stderr: wodim: fifo had 637 puts and 383 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: wodim: fifo was 0 times empty and 161 times full, min fill was 96%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: HUP
BraseroWodim process finished with status 254
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroWodim stopping
BraseroWodim got killed
Session error : unknown (brasero_burn_record burn.c:2602)

---

### Post by running_rabbit07 on 2009-12-12
That is a log file for a CD you burnt.

---

### Post by Zundap on 2009-12-13
Can anyone please tell me where i would find the output document?  i have checked all (my documents) and there is only the three outputs for  the disc burning.

Thanks

---

### Post by Troll_the_Great on 2009-12-13
> **Zundap said:**
> Can anyone please tell me where i would find the output document?  i have checked all (my documents) and there is only the three outputs for  the disc burning.

Thanks

Just open a terminal (Applications-Accessories-Terminal), write "top" (without the quotes), hit ENTER and then copy and paste here everything you see there.
Cheers!

PS: that document should be in /home/username

---

### Post by Zundap on 2009-12-13
Thanks troll. :D



I  have done that, but I have just noticed that the writing in the shell keeps chainging, some times the ending lines show up to line 16, then it changes to just 8 lines, then ten, then 12, then 14 and then back to 16, is this normal?

ie: 12 root, 14 root, 16 root etc 

> top - 17:01:10 up  1:31,  2 users,  load average: 0.14, 0.18, 0.24
top - 17:01:17 up  1:31,  2 users,  load average: 0.12, 0.18, 0.24
Tasks: 111 total,   3 running, 108 sleeping,   0 stopped,   0 zombie
Cpu(s): 13.6%us,  2.7%sy,  0.0%ni, 83.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2028556k total,   503404k used,  1525152k free,    19840k buffers
Swap:  3229024k total,        0k used,  3229024k free,   228840k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5591 allen     20   0 32872  13m 9320 R 10.3  0.7   0:01.52 gnome-terminal     
 2469 root      20   0 84052  39m 7644 R  4.0  2.0   6:56.07 Xorg               
 3129 allen     20   0  286m 128m  29m S  2.0  6.5  19:59.37 firefox            
 5610 allen     20   0  2448 1172  912 R  0.3  0.1   0:00.08 top                
    1 root      20   0  3084 1888  564 S  0.0  0.1   0:01.29 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0            
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0          
   11 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   12 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify  


---

### Post by Zundap on 2009-12-19
Could anyone please advise me on this problem? 

Thanks in advance for any replies.

---

### Post by joes7 on 2009-12-19
Applications->Add/Remove..

---

### Post by 3rdalbum on 2009-12-19
Can you please stop messing around telling the poster to give us the output of "top"? This isn't helping.

To the question asker: You can only run one package management system at a time; it's a technical limitation. Each package manager will create a "lock file", so if another package manager starts it will see the lock file and know not to run. Sometimes, very rarely, the lock file will not be removed when your package manager closes. The following command fixes this:

```
sudo rm /var/lib/dpkg/lock
```

This command will not put any messages into the terminal.

Reboot before running any more package managers.

You should be fine now.

---

### Post by Extract_Here on 2009-12-19
> **Zundap said:**
> Hi, could anyone please help? 

I have been trying to install frostwire, but i get the error message. **"       **                           **Only one software management tool is allowed to run at the same time**
 [B]please close the other application eg: update manager aptitude or synaptic first" 
[/B]


I have had the same trouble trying to install other software also**, **i am running ubuntu 9.04


Thanks

well first off you shouldnt use frostwire I would suggest a torrent like deluge and a torrent site like [www.thepiratebay.org](www.thepiratebay.org)  to get deluge follow these steps.

system>admin>synapticpackagemanager>search:deluge and install.

---

### Post by 3rdalbum on 2009-12-19
> **Extract_Here said:**
> well first off you shouldnt use frostwire I would suggest a torrent like deluge and a torrent site like [www.thepiratebay.org](www.thepiratebay.org)  to get deluge follow these steps.

system>admin>synapticpackagemanager>search:deluge and install.

*sigh* I don't think downloading Deluge with Synaptic will help the OP fix his inability to install software from Synaptic...

...and Ubuntu ships with a Bittorrent client already (Transmission).

---

### Post by Zundap on 2009-12-20
Sorry to  be a pest, but it still will  not not install the program, and i am getting the same error message, anymore advise would be greatly appreciated.

3rdalbum is correct by the way, Transmission is shipped with Ubuntu.

I decided to go for Frostwire, because someone recommended it here on the forum and they had no trouble installing it at all.

Thanks to everyone for their efforts to help, its greatly appreciated.

---

### Post by 3rdalbum on 2009-12-20
> **Zundap said:**
> Sorry to  be a pest, but it still will  not not install the program, and i am getting the same error message, anymore advise would be greatly appreciated.

To clarify: You've run the following command in the terminal:

```
sudo rm /var/lib/dpkg/lock
```

and your package manager is still reporting that there's already a PM in use?

Try:

```
killall update-notifier
```

---

### Post by UnknownFear on 2009-12-20
> **Extract_Here said:**
> well first off you shouldnt use frostwire I would suggest a torrent like deluge

Thanks, looks just like BitTorrent and runs perfectly :)

---

### Post by Zundap on 2009-12-21
> **3rdalbum said:**
> To clarify: You've run the following command in the terminal:

```
sudo rm /var/lib/dpkg/lock
```and your package manager is still reporting that there's already a PM in use?

Try:

```
killall update-notifier
```

Thats correct, i copied and pasted    the text below in to terminal first of all, then rebooted, and it is still the same, i still get the same error message
sudo rm /var/lib/dpkg/lock

Then i copied and pasted the text below, entered it in to terminal and re booted and i am still getting the same error message.

killall update-notifier

Thanks for your patience 3rdalbum.

Any more advise will be gratefully received.

---

### Post by master620 on 2010-01-16
i am having a very similar problem, although the "kill now" thing fixed it somewhat.. what's happening with mine is that i try to install virtualbox, but when i download it and tell it to install, it pops up and says everything is ok, then i click "install" and a password prompt comes up for sudo privaliges, after that its like the installer thing just reloads, and then it tells me that i can only have one installer running at a time... very annoying

although i am using karmic so it may be different.. right now i'm trying to just redownload and this time save it instead of just running.. maybe that'll fix it

---


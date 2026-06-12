---
title: "have i got the right o/s"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by rgbargee on 2009-12-01
Im really beginning to doubt whether karmic or even 64 bit o/s was a good decision for me and i need some help and hand holding to decide , my justiication for choosing 64 bit (originally had jaunty) was  because my pc was 64bit amd so i figured 64 bit was the way to go. My journey through windows was ok then xp and finally the vista monster put paid to my trust of the microsoft o/s so i needed an alternative . I formatted my hard drive and applied a full install of jaunty and recently karmic. My first installation failed because i had downloaded 32 bit and i coudnt figure how to install, then the 64 bit installed ok. I live on the internet facebook, you tube and browsing forums ive even got a rubbish website up that i find difficult to maintain or improve but i stammer on. The first problem i had was flash player i still havent got it fixed properly but 64 and flash dont seem to mix, the second problem is firefox crashes all the time not just daily but several times a day, i have seen several reports of this instability, my best success has been from installing/running firefox with wine and using that for flash intensive sites. Now i have bought a gamepad to enjoy the large number of games with my kidz but it wont work (its usb see my other thread in absolute beginners). I cant burn dvds even though my pc is only a year or so old  i just cant get a disc to burn ( ive tried three different drives but no joy). Three or four very basic i would think processes that i would need my o/s to do but im unable to do them .So the question is although i was a reasonably good windows user have i made the right decision to keep the most up to date o/s given my very limited linux experience and what are the alternatives.:-k

---

### Post by marco123 on 2009-12-01
As for alternatives, Windows 7 is a fairly good OS.

I've personally never had any problems with Firefox on 64bit Ubuntu.  I usually install Flash/Java/Codecs using the;

> sudo apt-get install ubuntu-restricted-extras

command, and haven't had any problems.  Maybe a clean install to reset everything, then running that command and see how you go?

What are your system specs?

---

### Post by QIII on 2009-12-01
It might be easier to post one issue at a time.  Often people will look at a "laundry list" post and move on because it is difficult to know where to begin answering several questions at once.

But, with regard to Flash/FF:  Both work fine for me on a 64 bit install of both Karmic and Lucid.

I recommend lovinglinux' troubleshooting guide here:

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by Zoot7 on 2009-12-01
Flash under 64bit has been quite flakey for some time now (in fact flash under Linux in general has been less than optimal). It's still in Alpha and has been for a while now.
Here's a link that might be of use to you:
[http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/](http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/)

Have you got the right OS? Well.. Linux isn't for everybody, and has a bit of a learning curve, but if you persevere, the advantages are tenfold IMO.
Ubuntu is a good distro to start off with, but if you wanted an alternative you could look at something like Fedora or openSUSE, or if you wanted something similar to Ubuntu, you could try Linux Mint or Mepis.

Hang in there! ;)

---

### Post by ed-koala on 2009-12-01
I'd be very interested in knowing what type of equipment you have in your PC.  64 bit flash has come a long way and I no longer have any problem, but you must install it properly for it to work well.

List your components.
What burning software are you trying to use?

I'm thinking perhaps something isn't set up properly, as far as flash goes. As for the disk burning, might be a hardware issue but won't know till we see what type of burner you have.

---

### Post by rgbargee on 2009-12-01
sorry everyone i guess it is a 'laundry list', i have no doubts about ubuntu being the right tools for me  the real question is im gonna reinstall ubuntu so which one , ive written down the flash links for when im done installing thanks for that

---

### Post by rgbargee on 2009-12-01
@ ed is there a system page in ubuntu so i can copy and paste my pcs specs

---

### Post by Zoot7 on 2009-12-01
If you do Edit -> Preferences in the Terminal you can set the shorcuts for Copying and Pasting.
The command **lspci** pretty much tells us most of what we'd want to know about your machine.

---

### Post by Paqman on 2009-12-01
> **rgbargee said:**
> im gonna reinstall ubuntu

That's probably not going to fix the issues you've got. Why not give us a bit more detail about the problems you're having with Firefox and DVDs, and we'll see if we can sort those out for you as well.

---

### Post by rgbargee on 2009-12-01
@Ed
 00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
release 9.10 (karmic)
kernal Linux 2.6.31-15 generic
memory 744.8 mb (1gb but some shared by on board graphics)
processor 0 AMD athlon 64 x 2 dual core processor 4000+
processor 1 amd athlon 64 x 2 dual core processor 4000+
available disc space 118 gb

hope this is enough , its not a power gaming pc or anything but should suffice for web browsing and occasional gaming i think :)

---

### Post by marco123 on 2009-12-01
That's not far off my old PCs specs. (I had the 3800 X2 AMD processor and the 6100 onboard GPU.) I ran that setup without any problems for nearly 2 years until I upgraded last December.

How did you try to install Flash and did you modify Firefox in any way?

My setup routine was:

1. Install Ubuntu.
2. Install any updates through Update Manager.
3. Install the Restricted Drivers through Administration>Hardware Drivers.
4. Install all the Codecs/Browser Plugins/Flash and Java with the "sudo apt-get install ubuntu-restricted-extras" command. (I used to add "dvdrip devede audacious vlc" to that command though.)

And that was pretty much it, I had a stable functional system.  You can then go through Add/Remove, Software Centre or the Synaptic Package Manager and see if there's any other programs you would like to install.

---

### Post by rgbargee on 2009-12-01
@ paqman ,  
dvds and cds read no problems video and data i just cant burn ive tried brasero, deveedee , avidemux they load up i add the files but they dont burn id have to try one again to remember the error message

firefox as shipped with ubuntu works but the little flash games and videos dont, under wine the latest version of firefox works but is sporadic and glitchy slow pageloads and corrupted formatting on the pages descriptions not on the buttons etc, both crash a lot!

---

### Post by marco123 on 2009-12-01
> **rgbargee said:**
> @ paqman ,  
dvds and cds read no problems video and data i just cant burn ive tried brasero, deveedee , avidemux they load up i add the files but they dont burn id have to try one again to remember the error message

firefox as shipped with ubuntu works but the little flash games and videos dont, under wine the latest version of firefox works but is sporadic and glitchy slow pageloads and corrupted formatting on the pages descriptions not on the buttons etc, both crash a lot!

Try my old setup routine.  There's no reason that I can think of that you should have any problems with Firefox, or flash when setup properly.

Edit: I usually use Serpentine Audio CD Creator as a simple burning app.

---

### Post by rgbargee on 2009-12-01
@ marco
i tried a few methods of installing flash so ive probably got old versions lurking, my terminal knowledge is nil so i blindly followed whatever was in front of me at the time , think i tried four or five different 'fixes' some two liners and others with multiple commands even including trying to get air working (i still dont know what air is lol) it started working so i i left it as was, the recent adobe update applied by facebook and you tube meant i lost useability and i havent been able to get it going again, as above i got it working through wine but it is glitchy

---

### Post by marco123 on 2009-12-01
> **rgbargee said:**
> @ marco
i tried a few methods of installing flash so ive probably got old versions lurking, my terminal knowledge is nil so i blindly followed whatever was in front of me at the time , think i tried four or five different 'fixes' some two liners and others with multiple commands even including trying to get air working (i still dont know what air is lol) it started working so i i left it as was, the recent adobe update applied by facebook and you tube meant i lost useability and i havent been able to get it going again, as above i got it working through wine but it is glitchy

Sounds like there could be conflicts.  I'd count it as a learning experience and re-install and try it my way, in post No.11  (I'm not being egotistical, it's just that I know from experience because I went through about 3 installs until I found what works best with regard to setup etc...  and on very similar hardware.)

---

### Post by rgbargee on 2009-12-01
think i will try that marco thanks, got a stable torrent i can download? or should i overload the mirror :D

---

### Post by marco123 on 2009-12-01
> **rgbargee said:**
> think i will try that marco thanks, got a stable torrent i can download? or should i overload the mirror :D

The torrent is usually really fast and well seeded.:)

---

### Post by rgbargee on 2009-12-01
ok vuze is running im downloading the latest 910 desktop version torrent from the ubuntu site , ill have to burn it with my daughters vista laptop #-ogonna take a while, i do wish the uk would do something about rural internet being so slow i need t1 or optical now :)

---

### Post by oldos2er on 2009-12-01
Are you using 32- or 64-bit Flash? There is a script here to install 64-bit Flash: [http://ubuntuforums.org/attachment.php?attachmentid=128822&d=1253131938](http://ubuntuforums.org/attachment.php?attachmentid=128822&d=1253131938)

 If you install ubuntu-restricted-extras, it installs 32-bit Flash with nspluginwrapper, which in my opinion is less reliable that the 64-bit version.

---

### Post by mvelte54 on 2009-12-01
I am by no means an Ubuntu Linux wizard but I to ran winddoze for many years and just got fed up with it. My solution was to wipe both my machines C-3PO my workhorse and R2D2 with 'Kill disk' It's out there and free. I suspect you are having conflicts with two completely different operating systems. That is why I wiped mine clean as if starting with brand new disks. I installed Jaunty and used it for 6 months then Karmic came out and I felt I had learned enough to venture out and I haven't looked back.
Long live Ubuntu!

---

### Post by rgbargee on 2009-12-01
ah nspluginwrapper sounds familiar that was definately one of the options i tried, but failed ill come back for the 64 bit link when i reboot ubuntu still an hour left on the download :(

---

### Post by Paqman on 2009-12-01
> **rgbargee said:**
> @ paqman ,  
dvds and cds read no problems video and data i just cant burn ive tried brasero, deveedee , avidemux they load up i add the files but they dont burn id have to try one again to remember the error message


Ok, if you're still having the problem once you reinstall then it'd be helpful if you could post the error message.

---

### Post by rgbargee on 2009-12-01
thx paqman will do, ive got an image almost ready , ill give it a go and report the error before i reinstall it might be helpfull to someone else to resolve this too :)

---

### Post by rgbargee on 2009-12-01
while im waiting for my download, what does everyone recommend regarding partitions and stuff when im installing , its the only operating system so do i just go with the defaults or is there a better way

---

### Post by Paqman on 2009-12-01
The defaults are fine, but one popular option is to use "manual partitioning" to create an extra partition, then mount your /home on it. This means you can reinstall the system without affecting any of the data in your /home.

---

### Post by QIII on 2009-12-01
Many are the views on this subject...

At the very least, create a separate /home partition.

It makes fresh installations of new versions much easier.

---

### Post by rgbargee on 2009-12-01
mmm mount  that sounds complicated and size ill need to know optimum size for my /home feel free to follow up :)

---

### Post by halitech on 2009-12-01
sizing depends on how big your drive is. Typically you shouldn't need much more then 6-8gig for / , whatever you are alotting for swap and then give the rest to /home.

---

### Post by Paqman on 2009-12-01
> **rgbargee said:**
> mmm mount  that sounds complicated and size ill need to know optimum size for my /home feel free to follow up :)

It's actually pretty easy. After telling it to create a new partition, you just pick the filesystem you want (normally ext4) then pick the mount point from a drop-down box.

So create one partition for /, one for /home and one for swap. 10GB is plenty for /, swap should be the same as your RAM if you want to hibernate otherwise 1GB is fine, and /home can be as big as you want.

---

### Post by rgbargee on 2009-12-02
ok i tried to burn the o/s image to cd heres the brasero log , sorry to flood but i cant remember the name of that site where you can drop your error reports for remote viewing

note to self - keep better notes

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1848)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_4RPE4U.bin toc = none
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_DSOE4U.bin toc = none
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
    speed=48
    driveropts=burnfree
    fs=16m
    -data
    -nopad
    /home/dad/Desktop/ubuntu-9.10-desktop-amd64.iso
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
BraseroWodim stderr: wodim: No write mode specified.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Asuming -tao mode.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Future versions of wodim may have different drive dependent defaults.
BraseroWodim called brasero_job_get_flags
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
BraseroWodim stdout: Vendor_info    : '_NEC    '
BraseroWodim stdout: Identification : 'DVD_RW ND-3520A '
BraseroWodim stderr: Speed set to 8467 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Revision       : '1.04'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) (current)
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
BraseroWodim stdout: Drive buf size : 1343488 = 1312 KB
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stdout: Track 01: data   690 MB        
BraseroWodim stdout: Total size:      793 MB (78:35.86) = 353690 sectors
BraseroWodim stdout: Lout start:      793 MB (78:37/65) = 353690 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 5
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is not erasable
BraseroWodim stdout:   Disk sub type: Medium Type A, high Beta category (A+) (3)
BraseroWodim stdout:   ATIP start of lead in:  -11634 (97:26/66)
BraseroWodim stdout:   ATIP start of lead out: 359846 (79:59/71)
BraseroWodim stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
BraseroWodim stdout: Manuf. index: 3
BraseroWodim stdout: Manufacturer: CMC Magnetics Corporation
BraseroWodim stdout: Blocks total: 359846 Blocks current: 359846 Blocks remaining: 6156
BraseroWodim stdout: Starting to write CD/DVD at speed  48.0 in real TAO mode for single session.
BraseroWodim stdout: Last chance to quit, starting real write in    4 seconds.
BraseroWodim called brasero_job_set_dangerous
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    3 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    2 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    1 seconds.   0 seconds. Operation starts.
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Performing OPC...
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stdout: 
BraseroWodim stdout: Track 01:    0 of  690 MB written.
BraseroWodim stdout: Track 01:    1 of  690 MB written (fifo  96%) [buf  80%]  61.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    2 of  690 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    3 of  690 MB written (fifo 100%) [buf 100%]  22.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    4 of  690 MB written (fifo  99%) [buf 100%]  21.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    5 of  690 MB written (fifo 100%) [buf 100%]  22.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    6 of  690 MB written (fifo 100%) [buf 100%]  22.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    7 of  690 MB written (fifo 100%) [buf 100%]  22.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    8 of  690 MB written (fifo 100%) [buf 100%]  22.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    9 of  690 MB written (fifo 100%) [buf 100%]  22.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   10 of  690 MB written (fifo 100%) [buf 100%]  22.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   11 of  690 MB written (fifo  99%) [buf 100%]  22.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   12 of  690 MB written (fifo 100%) [buf 100%]  22.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   13 of  690 MB written (fifo 100%) [buf 100%]  22.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   14 of  690 MB written (fifo 100%) [buf 100%]  22.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   15 of  690 MB written (fifo 100%) [buf 100%]  23.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   16 of  690 MB written (fifo 100%) [buf 100%]  22.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   17 of  690 MB written (fifo 100%) [buf 100%]  23.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   18 of  690 MB written (fifo 100%) [buf 100%]  22.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   19 of  690 MB written (fifo 100%) [buf 100%]  23.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   20 of  690 MB written (fifo 100%) [buf 100%]  22.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   21 of  690 MB written (fifo 100%) [buf 100%]  23.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   22 of  690 MB written (fifo  99%) [buf 100%]  22.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   23 of  690 MB written (fifo 100%) [buf 100%]  23.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   24 of  690 MB written (fifo 100%) [buf 100%]  22.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   25 of  690 MB written (fifo 100%) [buf 100%]  23.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   26 of  690 MB written (fifo  99%) [buf 100%]  22.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   27 of  690 MB written (fifo 100%) [buf 100%]  23.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   28 of  690 MB written (fifo 100%) [buf 100%]  22.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   29 of  690 MB written (fifo 100%) [buf 100%]  23.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   30 of  690 MB written (fifo 100%) [buf 100%]  22.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   31 of  690 MB written (fifo 100%) [buf 100%]  23.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   32 of  690 MB written (fifo 100%) [buf 100%]  23.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   33 of  690 MB written (fifo 100%) [buf 100%]  23.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   34 of  690 MB written (fifo 100%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   35 of  690 MB written (fifo 100%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   36 of  690 MB written (fifo  99%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   37 of  690 MB written (fifo 100%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   38 of  690 MB written (fifo 100%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   39 of  690 MB written (fifo 100%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   40 of  690 MB written (fifo 100%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   41 of  690 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   42 of  690 MB written (fifo 100%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   43 of  690 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   44 of  690 MB written (fifo  99%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   45 of  690 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   46 of  690 MB written (fifo  99%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   47 of  690 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   48 of  690 MB written (fifo  99%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   49 of  690 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   50 of  690 MB written (fifo 100%) [buf 100%]   7.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   51 of  690 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   52 of  690 MB written (fifo 100%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   53 of  690 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   54 of  690 MB written (fifo 100%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   55 of  690 MB written (fifo 100%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   56 of  690 MB written (fifo 100%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   57 of  690 MB written (fifo  99%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   58 of  690 MB written (fifo 100%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   59 of  690 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   60 of  690 MB written (fifo 100%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   61 of  690 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   62 of  690 MB written (fifo 100%) [buf 100%]  25.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   63 of  690 MB written (fifo 100%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   64 of  690 MB written (fifo  99%) [buf 100%]  25.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   65 of  690 MB written (fifo 100%) [buf 100%]  26.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   66 of  690 MB written (fifo  99%) [buf 100%]  25.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   67 of  690 MB written (fifo 100%) [buf 100%]  26.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   68 of  690 MB written (fifo 100%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   69 of  690 MB written (fifo 100%) [buf 100%]  26.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   70 of  690 MB written (fifo 100%) [buf 100%]  25.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   71 of  690 MB written (fifo 100%) [buf 100%]  26.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   72 of  690 MB written (fifo  99%) [buf 100%]  25.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   73 of  690 MB written (fifo 100%) [buf 100%]  26.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   74 of  690 MB written (fifo 100%) [buf 100%]  25.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   75 of  690 MB written (fifo  99%) [buf 100%]  26.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   76 of  690 MB written (fifo 100%) [buf 100%]  25.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   77 of  690 MB written (fifo 100%) [buf 100%]  26.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   78 of  690 MB written (fifo  99%) [buf 100%]  25.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   79 of  690 MB written (fifo 100%) [buf 100%]  26.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   80 of  690 MB written (fifo  99%) [buf 100%]  26.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   81 of  690 MB written (fifo 100%) [buf 100%]  26.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   82 of  690 MB written (fifo  99%) [buf 100%]  26.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   83 of  690 MB written (fifo 100%) [buf 100%]  27.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   84 of  690 MB written (fifo 100%) [buf 100%]  26.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   85 of  690 MB written (fifo 100%) [buf 100%]  27.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   86 of  690 MB written (fifo  99%) [buf 100%]  26.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   87 of  690 MB written (fifo 100%) [buf 100%]  27.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   88 of  690 MB written (fifo 100%) [buf 100%]  26.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   89 of  690 MB written (fifo  99%) [buf 100%]  27.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   90 of  690 MB written (fifo  99%) [buf 100%]  26.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   91 of  690 MB written (fifo 100%) [buf 100%]  27.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   92 of  690 MB written (fifo 100%) [buf 100%]  26.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   93 of  690 MB written (fifo 100%) [buf 100%]  27.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   94 of  690 MB written (fifo 100%) [buf 100%]  26.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   95 of  690 MB written (fifo 100%) [buf 100%]  27.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   96 of  690 MB written (fifo  99%) [buf 100%]  28.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   97 of  690 MB written (fifo  99%) [buf 100%]  27.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   98 of  690 MB written (fifo 100%) [buf 100%]  28.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   99 of  690 MB written (fifo 100%) [buf 100%]  27.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  100 of  690 MB written (fifo 100%) [buf 100%]  28.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  101 of  690 MB written (fifo 100%) [buf 100%]  27.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  102 of  690 MB written (fifo 100%) [buf 100%]  28.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  103 of  690 MB written (fifo 100%) [buf 100%]  27.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  104 of  690 MB written (fifo 100%) [buf 100%]  28.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  105 of  690 MB written (fifo 100%) [buf 100%]  27.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  106 of  690 MB written (fifo 100%) [buf 100%]  28.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  107 of  690 MB written (fifo 100%) [buf 100%]  27.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  108 of  690 MB written (fifo 100%) [buf 100%]  28.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  109 of  690 MB written (fifo  99%) [buf 100%]  27.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  110 of  690 MB written (fifo  99%) [buf 100%]  28.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  111 of  690 MB written (fifo 100%) [buf 100%]  27.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  112 of  690 MB written (fifo 100%) [buf 100%]  28.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  113 of  690 MB written (fifo  99%) [buf 100%]  27.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  114 of  690 MB written (fifo  99%) [buf 100%]  28.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  115 of  690 MB written (fifo 100%) [buf 100%]  27.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  116 of  690 MB written (fifo 100%) [buf 100%]  28.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  117 of  690 MB written (fifo 100%) [buf 100%]  27.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  118 of  690 MB written (fifo 100%) [buf 100%]  28.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  119 of  690 MB written (fifo  99%) [buf 100%]  27.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  120 of  690 MB written (fifo 100%) [buf 100%]  28.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  121 of  690 MB written (fifo 100%) [buf 100%]  27.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  122 of  690 MB written (fifo  99%) [buf 100%]  28.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  123 of  690 MB written (fifo 100%) [buf 100%]  28.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  124 of  690 MB written (fifo  99%) [buf 100%]  28.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  125 of  690 MB written (fifo 100%) [buf 100%]  28.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  126 of  690 MB written (fifo 100%) [buf 100%]  28.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  127 of  690 MB written (fifo  99%) [buf 100%]  29.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  128 of  690 MB written (fifo 100%) [buf 100%]  28.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  129 of  690 MB written (fifo  99%) [buf 100%]  29.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  130 of  690 MB written (fifo 100%) [buf 100%]  28.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  131 of  690 MB written (fifo 100%) [buf 100%]  29.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  132 of  690 MB written (fifo 100%) [buf 100%]  29.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  133 of  690 MB written (fifo 100%) [buf 100%]  29.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  134 of  690 MB written (fifo  99%) [buf 100%]  29.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  135 of  690 MB written (fifo 100%) [buf 100%]  30.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  136 of  690 MB written (fifo 100%) [buf 100%]  29.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  137 of  690 MB written (fifo  99%) [buf 100%]  30.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  138 of  690 MB written (fifo  99%) [buf 100%]  29.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  139 of  690 MB written (fifo 100%) [buf 100%]  30.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  140 of  690 MB written (fifo  99%) [buf 100%]  29.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  141 of  690 MB written (fifo  99%) [buf 100%]  30.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  142 of  690 MB written (fifo 100%) [buf 100%]  28.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  143 of  690 MB written (fifo 100%) [buf 100%]  30.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  144 of  690 MB written (fifo 100%) [buf 100%]  29.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  145 of  690 MB written (fifo 100%) [buf 100%]  30.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  146 of  690 MB written (fifo 100%) [buf 100%]  29.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  147 of  690 MB written (fifo  99%) [buf 100%]  30.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  148 of  690 MB written (fifo 100%) [buf 100%]  29.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  149 of  690 MB written (fifo 100%) [buf 100%]  30.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  150 of  690 MB written (fifo 100%) [buf 100%]  29.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  151 of  690 MB written (fifo  99%) [buf 100%]  30.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  152 of  690 MB written (fifo 100%) [buf 100%]  29.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  153 of  690 MB written (fifo 100%) [buf 100%]  30.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  154 of  690 MB written (fifo  99%) [buf 100%]  29.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  155 of  690 MB written (fifo 100%) [buf 100%]  30.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  156 of  690 MB written (fifo 100%) [buf 100%]  29.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  157 of  690 MB written (fifo  99%) [buf 100%]  30.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  158 of  690 MB written (fifo 100%) [buf 100%]  31.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  159 of  690 MB written (fifo  99%) [buf 100%]  30.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  160 of  690 MB written (fifo 100%) [buf 100%]  31.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  161 of  690 MB written (fifo 100%) [buf 100%]  30.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  162 of  690 MB written (fifo 100%) [buf 100%]  31.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  163 of  690 MB written (fifo 100%) [buf 100%]  30.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  164 of  690 MB written (fifo 100%) [buf 100%]  31.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  165 of  690 MB written (fifo 100%) [buf 100%]  30.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  166 of  690 MB written (fifo 100%) [buf 100%]  31.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  167 of  690 MB written (fifo 100%) [buf 100%]  30.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  168 of  690 MB written (fifo 100%) [buf 100%]  31.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  169 of  690 MB written (fifo 100%) [buf 100%]  30.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  170 of  690 MB written (fifo  99%) [buf 100%]  31.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  171 of  690 MB written (fifo 100%) [buf 100%]  30.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  172 of  690 MB written (fifo  99%) [buf 100%]  31.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  173 of  690 MB written (fifo 100%) [buf 100%]  30.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  174 of  690 MB written (fifo  99%) [buf 100%]  31.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  175 of  690 MB written (fifo  99%) [buf 100%]  30.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  176 of  690 MB written (fifo 100%) [buf 100%]  31.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  177 of  690 MB written (fifo  98%) [buf 100%]  30.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  178 of  690 MB written (fifo 100%) [buf 100%]  31.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  179 of  690 MB written (fifo 100%) [buf 100%]  30.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  180 of  690 MB written (fifo 100%) [buf 100%]  31.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  181 of  690 MB written (fifo 100%) [buf 100%]  30.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  182 of  690 MB written (fifo 100%) [buf 100%]  31.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  183 of  690 MB written (fifo  99%) [buf 100%]  30.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  184 of  690 MB written (fifo 100%) [buf 100%]  31.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  185 of  690 MB written (fifo  99%) [buf 100%]  30.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  186 of  690 MB written (fifo 100%) [buf 100%]  31.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  187 of  690 MB written (fifo 100%) [buf 100%]  30.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  188 of  690 MB written (fifo 100%) [buf 100%]  32.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  189 of  690 MB written (fifo  99%) [buf 100%]  32.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  190 of  690 MB written (fifo  99%) [buf 100%]  31.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  191 of  690 MB written (fifo 100%) [buf 100%]  32.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  192 of  690 MB written (fifo  99%) [buf 100%]  32.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  193 of  690 MB written (fifo 100%) [buf 100%]  32.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  194 of  690 MB written (fifo  99%) [buf 100%]  31.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  195 of  690 MB written (fifo 100%) [buf 100%]  33.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  196 of  690 MB written (fifo 100%) [buf 100%]  32.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  197 of  690 MB written (fifo 100%) [buf 100%]  32.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  198 of  690 MB written (fifo  99%) [buf 100%]  32.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  199 of  690 MB written (fifo 100%) [buf 100%]  33.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  200 of  690 MB written (fifo 100%) [buf 100%]  32.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  201 of  690 MB written (fifo 100%) [buf 100%]  33.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  202 of  690 MB written (fifo 100%) [buf 100%]  32.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  203 of  690 MB written (fifo 100%) [buf 100%]  33.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  204 of  690 MB written (fifo  99%) [buf 100%]  32.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  205 of  690 MB written (fifo 100%) [buf 100%]  32.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  206 of  690 MB written (fifo  99%) [buf 100%]  32.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  207 of  690 MB written (fifo 100%) [buf 100%]  33.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  208 of  690 MB written (fifo  99%) [buf 100%]  32.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  209 of  690 MB written (fifo  99%) [buf 100%]  33.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  210 of  690 MB written (fifo 100%) [buf 100%]  32.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  211 of  690 MB written (fifo  99%) [buf 100%]  33.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  212 of  690 MB written (fifo 100%) [buf 100%]  32.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  213 of  690 MB written (fifo 100%) [buf 100%]  33.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  214 of  690 MB written (fifo 100%) [buf 100%]  32.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  215 of  690 MB written (fifo  99%) [buf 100%]  33.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  216 of  690 MB written (fifo 100%) [buf 100%]  32.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  217 of  690 MB written (fifo 100%) [buf 100%]  33.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  218 of  690 MB written (fifo  99%) [buf 100%]  32.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  219 of  690 MB written (fifo 100%) [buf 100%]  33.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  220 of  690 MB written (fifo  99%) [buf 100%]  34.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  221 of  690 MB written (fifo 100%) [buf 100%]  33.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  222 of  690 MB written (fifo 100%) [buf 100%]  34.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  223 of  690 MB written (fifo  99%) [buf 100%]  33.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  224 of  690 MB written (fifo  99%) [buf 100%]  34.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  225 of  690 MB written (fifo 100%) [buf 100%]  33.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  226 of  690 MB written (fifo  99%) [buf 100%]  34.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  227 of  690 MB written (fifo 100%) [buf 100%]  33.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  228 of  690 MB written (fifo 100%) [buf 100%]  34.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  229 of  690 MB written (fifo  98%) [buf 100%]  33.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  230 of  690 MB written (fifo 100%) [buf 100%]  34.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  231 of  690 MB written (fifo  99%) [buf 100%]  33.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  232 of  690 MB written (fifo  99%) [buf 100%]  34.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  233 of  690 MB written (fifo 100%) [buf 100%]  33.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  234 of  690 MB written (fifo  99%) [buf 100%]  34.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  235 of  690 MB written (fifo 100%) [buf 100%]  33.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  236 of  690 MB written (fifo 100%) [buf 100%]  34.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  237 of  690 MB written (fifo  99%) [buf 100%]  33.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  238 of  690 MB written (fifo  99%) [buf 100%]  34.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  239 of  690 MB written (fifo  99%) [buf 100%]  33.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  240 of  690 MB written (fifo 100%) [buf 100%]  34.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  241 of  690 MB written (fifo  99%) [buf 100%]  33.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  242 of  690 MB written (fifo 100%) [buf 100%]  34.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  243 of  690 MB written (fifo  99%) [buf 100%]  33.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  244 of  690 MB written (fifo 100%) [buf 100%]  34.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  245 of  690 MB written (fifo 100%) [buf 100%]  33.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  246 of  690 MB written (fifo 100%) [buf 100%]  34.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  247 of  690 MB written (fifo 100%) [buf 100%]  33.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  248 of  690 MB written (fifo 100%) [buf 100%]  34.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  249 of  690 MB written (fifo  99%) [buf 100%]  33.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  250 of  690 MB written (fifo 100%) [buf 100%]  34.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  251 of  690 MB written (fifo 100%) [buf 100%]  35.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  252 of  690 MB written (fifo 100%) [buf 100%]  34.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  253 of  690 MB written (fifo  99%) [buf 100%]  35.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  254 of  690 MB written (fifo 100%) [buf 100%]  34.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  255 of  690 MB written (fifo 100%) [buf 100%]  35.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  256 of  690 MB written (fifo 100%) [buf 100%]  34.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  257 of  690 MB written (fifo  99%) [buf 100%]  35.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  258 of  690 MB written (fifo  99%) [buf 100%]  34.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  259 of  690 MB written (fifo  99%) [buf 100%]  35.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  260 of  690 MB written (fifo  99%) [buf 100%]  34.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  261 of  690 MB written (fifo  99%) [buf 100%]  34.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  262 of  690 MB written (fifo 100%) [buf 100%]  35.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  263 of  690 MB written (fifo  99%) [buf 100%]  35.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  264 of  690 MB written (fifo  99%) [buf 100%]  34.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  265 of  690 MB written (fifo  99%) [buf 100%]  35.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  266 of  690 MB written (fifo 100%) [buf 100%]  34.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  267 of  690 MB written (fifo  99%) [buf 100%]  35.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  268 of  690 MB written (fifo 100%) [buf 100%]  34.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  269 of  690 MB written (fifo 100%) [buf 100%]  35.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  270 of  690 MB written (fifo 100%) [buf 100%]  34.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  271 of  690 MB written (fifo 100%) [buf 100%]  35.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  272 of  690 MB written (fifo  99%) [buf 100%]  34.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  273 of  690 MB written (fifo  99%) [buf 100%]  36.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  274 of  690 MB written (fifo  99%) [buf 100%]  34.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  275 of  690 MB written (fifo 100%) [buf 100%]  35.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  276 of  690 MB written (fifo 100%) [buf 100%]  34.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  277 of  690 MB written (fifo 100%) [buf 100%]  36.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  278 of  690 MB written (fifo  99%) [buf 100%]  34.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  279 of  690 MB written (fifo 100%) [buf 100%]  35.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  280 of  690 MB written (fifo 100%) [buf 100%]  34.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  281 of  690 MB written (fifo  99%) [buf 100%]  35.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  282 of  690 MB written (fifo  99%) [buf 100%]  37.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  283 of  690 MB written (fifo  99%) [buf 100%]  35.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  284 of  690 MB written (fifo  99%) [buf 100%]  37.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  285 of  690 MB written (fifo 100%) [buf 100%]  35.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  286 of  690 MB written (fifo  99%) [buf 100%]  37.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  287 of  690 MB written (fifo  99%) [buf 100%]  35.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  288 of  690 MB written (fifo  99%) [buf 100%]  36.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  289 of  690 MB written (fifo  99%) [buf 100%]  36.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  290 of  690 MB written (fifo 100%) [buf 100%]  37.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  291 of  690 MB written (fifo  99%) [buf 100%]  35.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  292 of  690 MB written (fifo 100%) [buf 100%]  37.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  293 of  690 MB written (fifo 100%) [buf 100%]  36.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  294 of  690 MB written (fifo  99%) [buf 100%]  37.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  295 of  690 MB written (fifo 100%) [buf 100%]  35.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  296 of  690 MB written (fifo 100%) [buf 100%]  36.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  297 of  690 MB written (fifo 100%) [buf 100%]  36.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  298 of  690 MB written (fifo  99%) [buf 100%]  37.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  299 of  690 MB written (fifo  99%) [buf 100%]  36.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  300 of  690 MB written (fifo  99%) [buf 100%]  37.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  301 of  690 MB written (fifo  99%) [buf 100%]  35.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  302 of  690 MB written (fifo  99%) [buf 100%]  37.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  303 of  690 MB written (fifo 100%) [buf 100%]  36.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  304 of  690 MB written (fifo 100%) [buf 100%]  37.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  305 of  690 MB written (fifo  99%) [buf 100%]  35.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  306 of  690 MB written (fifo 100%) [buf 100%]  37.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  307 of  690 MB written (fifo  99%) [buf 100%]  36.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  308 of  690 MB written (fifo  99%) [buf 100%]  37.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  309 of  690 MB written (fifo  99%) [buf 100%]  36.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  310 of  690 MB written (fifo  99%) [buf 100%]  37.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  311 of  690 MB written (fifo  99%) [buf 100%]  35.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  312 of  690 MB written (fifo 100%) [buf 100%]  37.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  313 of  690 MB written (fifo 100%) [buf 100%]  38.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  314 of  690 MB written (fifo  99%) [buf 100%]  37.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  315 of  690 MB written (fifo  99%) [buf 100%]  38.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  316 of  690 MB written (fifo 100%) [buf 100%]  37.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  317 of  690 MB written (fifo 100%) [buf 100%]  38.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  318 of  690 MB written (fifo  99%) [buf 100%]  37.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  319 of  690 MB written (fifo  99%) [buf 100%]  38.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  320 of  690 MB written (fifo 100%) [buf 100%]  37.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  321 of  690 MB written (fifo  99%) [buf 100%]  38.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  322 of  690 MB written (fifo 100%) [buf 100%]  37.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  323 of  690 MB written (fifo 100%) [buf 100%]  38.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  324 of  690 MB written (fifo 100%) [buf 100%]  36.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  325 of  690 MB written (fifo  99%) [buf 100%]  38.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  326 of  690 MB written (fifo 100%) [buf 100%]  37.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  327 of  690 MB written (fifo 100%) [buf 100%]  38.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  328 of  690 MB written (fifo 100%) [buf 100%]  37.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  329 of  690 MB written (fifo  99%) [buf 100%]  37.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  330 of  690 MB written (fifo  99%) [buf 100%]  37.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  331 of  690 MB written (fifo  99%) [buf 100%]  38.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  332 of  690 MB written (fifo  99%) [buf 100%]  37.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  333 of  690 MB written (fifo  99%) [buf 100%]  38.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  334 of  690 MB written (fifo  99%) [buf 100%]  37.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  335 of  690 MB written (fifo  99%) [buf 100%]  38.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  336 of  690 MB written (fifo  99%) [buf 100%]  37.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  337 of  690 MB written (fifo  99%) [buf 100%]  38.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  338 of  690 MB written (fifo 100%) [buf 100%]  37.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  339 of  690 MB written (fifo 100%) [buf 100%]  38.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  340 of  690 MB written (fifo  99%) [buf 100%]  37.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  341 of  690 MB written (fifo  99%) [buf 100%]  38.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  342 of  690 MB written (fifo 100%) [buf 100%]  37.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  343 of  690 MB written (fifo 100%) [buf 100%]  38.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  344 of  690 MB written (fifo 100%) [buf 100%]  39.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  345 of  690 MB written (fifo 100%) [buf 100%]  38.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  346 of  690 MB written (fifo 100%) [buf 100%]  39.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  347 of  690 MB written (fifo 100%) [buf 100%]  38.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  348 of  690 MB written (fifo  99%) [buf 100%]  39.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  349 of  690 MB written (fifo 100%) [buf 100%]  38.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  350 of  690 MB written (fifo 100%) [buf 100%]  39.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  351 of  690 MB written (fifo 100%) [buf 100%]  38.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  352 of  690 MB written (fifo 100%) [buf 100%]  39.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  353 of  690 MB written (fifo 100%) [buf 100%]  38.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  354 of  690 MB written (fifo  99%) [buf 100%]  39.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  355 of  690 MB written (fifo 100%) [buf 100%]  38.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  356 of  690 MB written (fifo  99%) [buf 100%]  39.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  357 of  690 MB written (fifo  99%) [buf 100%]  38.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  358 of  690 MB written (fifo 100%) [buf 100%]  39.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  359 of  690 MB written (fifo 100%) [buf 100%]  38.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  360 of  690 MB written (fifo  99%) [buf 100%]  39.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  361 of  690 MB written (fifo  99%) [buf 100%]  38.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  362 of  690 MB written (fifo  99%) [buf 100%]  39.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  363 of  690 MB written (fifo 100%) [buf 100%]  38.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  364 of  690 MB written (fifo  99%) [buf 100%]  39.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  365 of  690 MB written (fifo  99%) [buf 100%]  38.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  366 of  690 MB written (fifo 100%) [buf 100%]  39.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  367 of  690 MB written (fifo 100%) [buf 100%]  38.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  368 of  690 MB written (fifo  99%) [buf 100%]  39.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  369 of  690 MB written (fifo  99%) [buf 100%]  38.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  370 of  690 MB written (fifo 100%) [buf 100%]  39.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  371 of  690 MB written (fifo 100%) [buf 100%]  38.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  372 of  690 MB written (fifo 100%) [buf 100%]  39.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  373 of  690 MB written (fifo 100%) [buf 100%]  38.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  374 of  690 MB written (fifo 100%) [buf 100%]  39.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  375 of  690 MB written (fifo 100%) [buf 100%]  40.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  376 of  690 MB written (fifo  99%) [buf 100%]  39.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  377 of  690 MB written (fifo 100%) [buf 100%]  40.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  378 of  690 MB written (fifo 100%) [buf 100%]  39.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  379 of  690 MB written (fifo 100%) [buf 100%]  40.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  380 of  690 MB written (fifo 100%) [buf 100%]  39.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  381 of  690 MB written (fifo  99%) [buf 100%]  40.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  382 of  690 MB written (fifo 100%) [buf 100%]  39.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  383 of  690 MB written (fifo 100%) [buf 100%]  40.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  384 of  690 MB written (fifo  99%) [buf 100%]  39.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  385 of  690 MB written (fifo  99%) [buf 100%]  40.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  386 of  690 MB written (fifo 100%) [buf 100%]  39.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  387 of  690 MB written (fifo  99%) [buf 100%]  40.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  388 of  690 MB written (fifo 100%) [buf 100%]  39.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  389 of  690 MB written (fifo 100%) [buf 100%]  40.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  390 of  690 MB written (fifo 100%) [buf 100%]  39.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  391 of  690 MB written (fifo 100%) [buf 100%]  40.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  392 of  690 MB written (fifo 100%) [buf 100%]  39.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  393 of  690 MB written (fifo  99%) [buf 100%]  40.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  394 of  690 MB written (fifo  99%) [buf 100%]  39.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  395 of  690 MB written (fifo  99%) [buf 100%]  40.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  396 of  690 MB written (fifo 100%) [buf 100%]  39.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  397 of  690 MB written (fifo 100%) [buf 100%]  40.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  398 of  690 MB written (fifo 100%) [buf 100%]  38.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  399 of  690 MB written (fifo 100%) [buf 100%]  41.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  400 of  690 MB written (fifo  99%) [buf 100%]  39.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  401 of  690 MB written (fifo  98%) [buf 100%]  40.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  402 of  690 MB written (fifo 100%) [buf 100%]  11.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  403 of  690 MB written (fifo  99%) [buf 100%]  40.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  404 of  690 MB written (fifo 100%) [buf 100%]  39.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  405 of  690 MB written (fifo  99%) [buf 100%]  40.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  406 of  690 MB written (fifo  99%) [buf 100%]  42.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  407 of  690 MB written (fifo 100%) [buf 100%]  40.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  408 of  690 MB written (fifo 100%) [buf 100%]  41.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  409 of  690 MB written (fifo  99%) [buf 100%]  40.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  410 of  690 MB written (fifo  99%) [buf 100%]  40.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  411 of  690 MB written (fifo  99%) [buf 100%]  41.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  412 of  690 MB written (fifo 100%) [buf 100%]  41.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  413 of  690 MB written (fifo  99%) [buf 100%]  40.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  414 of  690 MB written (fifo  98%) [buf 100%]  41.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  415 of  690 MB written (fifo 100%) [buf 100%]  40.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  416 of  690 MB written (fifo  99%) [buf 100%]  41.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  417 of  690 MB written (fifo 100%) [buf 100%]  40.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  418 of  690 MB written (fifo 100%) [buf 100%]  42.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  419 of  690 MB written (fifo  99%) [buf 100%]  40.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  420 of  690 MB written (fifo 100%) [buf 100%]  41.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  421 of  690 MB written (fifo  99%) [buf 100%]  40.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  422 of  690 MB written (fifo  99%) [buf 100%]  42.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  423 of  690 MB written (fifo  99%) [buf 100%]  40.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  424 of  690 MB written (fifo  99%) [buf 100%]  41.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  425 of  690 MB written (fifo 100%) [buf 100%]  40.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  426 of  690 MB written (fifo 100%) [buf 100%]  41.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  427 of  690 MB written (fifo  99%) [buf 100%]  40.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  428 of  690 MB written (fifo  99%) [buf 100%]  41.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  429 of  690 MB written (fifo  99%) [buf 100%]  40.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  430 of  690 MB written (fifo  99%) [buf 100%]  41.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  431 of  690 MB written (fifo  99%) [buf 100%]  40.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  432 of  690 MB written (fifo  99%) [buf 100%]  41.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  433 of  690 MB written (fifo 100%) [buf 100%]  40.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  434 of  690 MB written (fifo 100%) [buf 100%]  42.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  435 of  690 MB written (fifo 100%) [buf 100%]  40.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  436 of  690 MB written (fifo 100%) [buf 100%]  41.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  437 of  690 MB written (fifo  99%) [buf 100%]  43.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  438 of  690 MB written (fifo 100%) [buf 100%]  41.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  439 of  690 MB written (fifo 100%) [buf 100%]  43.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  440 of  690 MB written (fifo 100%) [buf 100%]  41.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  441 of  690 MB written (fifo  99%) [buf 100%]  43.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  442 of  690 MB written (fifo 100%) [buf 100%]  42.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  443 of  690 MB written (fifo 100%) [buf 100%]  42.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  444 of  690 MB written (fifo 100%) [buf 100%]  42.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  445 of  690 MB written (fifo 100%) [buf 100%]  42.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  446 of  690 MB written (fifo  97%) [buf 100%]  41.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  447 of  690 MB written (fifo 100%) [buf 100%]  43.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  448 of  690 MB written (fifo 100%) [buf 100%]  41.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  449 of  690 MB written (fifo 100%) [buf 100%]  42.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  450 of  690 MB written (fifo 100%) [buf 100%]  41.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  451 of  690 MB written (fifo  99%) [buf 100%]  40.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  452 of  690 MB written (fifo 100%) [buf 100%]  41.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  453 of  690 MB written (fifo 100%) [buf 100%]  43.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  454 of  690 MB written (fifo  99%) [buf 100%]  42.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  455 of  690 MB written (fifo 100%) [buf 100%]  43.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  456 of  690 MB written (fifo  99%) [buf 100%]  41.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  457 of  690 MB written (fifo 100%) [buf 100%]  43.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  458 of  690 MB written (fifo  99%) [buf 100%]  41.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  459 of  690 MB written (fifo  99%) [buf 100%]  42.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  460 of  690 MB written (fifo  99%) [buf 100%]  42.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  461 of  690 MB written (fifo  99%) [buf 100%]  42.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  462 of  690 MB written (fifo  99%) [buf 100%]  41.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  463 of  690 MB written (fifo 100%) [buf 100%]  43.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  464 of  690 MB written (fifo  99%) [buf 100%]  42.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  465 of  690 MB written (fifo 100%) [buf 100%]  42.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  466 of  690 MB written (fifo  99%) [buf 100%]  41.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  467 of  690 MB written (fifo  99%) [buf 100%]  42.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  468 of  690 MB written (fifo  99%) [buf 100%]  43.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  469 of  690 MB written (fifo  99%) [buf 100%]  44.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  470 of  690 MB written (fifo 100%) [buf 100%]  43.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  471 of  690 MB written (fifo 100%) [buf 100%]  43.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  472 of  690 MB written (fifo 100%) [buf 100%]  44.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  473 of  690 MB written (fifo  99%) [buf 100%]  42.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  474 of  690 MB written (fifo 100%) [buf 100%]  44.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  475 of  690 MB written (fifo  98%) [buf 100%]  42.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  476 of  690 MB written (fifo 100%) [buf 100%]  44.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  477 of  690 MB written (fifo  99%) [buf 100%]  42.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  478 of  690 MB written (fifo 100%) [buf 100%]  44.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  479 of  690 MB written (fifo  98%) [buf 100%]  42.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  480 of  690 MB written (fifo 100%) [buf 100%]  44.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  481 of  690 MB written (fifo 100%) [buf 100%]  42.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  482 of  690 MB written (fifo  97%) [buf 100%]  44.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  483 of  690 MB written (fifo 100%) [buf 100%]  42.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  484 of  690 MB written (fifo  99%) [buf 100%]  44.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  485 of  690 MB written (fifo  99%) [buf 100%]  42.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  486 of  690 MB written (fifo  99%) [buf 100%]  43.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  487 of  690 MB written (fifo  99%) [buf 100%]  44.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  488 of  690 MB written (fifo 100%) [buf 100%]  41.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  489 of  690 MB written (fifo 100%) [buf 100%]  44.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  490 of  690 MB written (fifo  99%) [buf 100%]  44.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  491 of  690 MB written (fifo  99%) [buf 100%]  42.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  492 of  690 MB written (fifo  99%) [buf 100%]  44.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  493 of  690 MB written (fifo  98%) [buf 100%]  42.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  494 of  690 MB written (fifo 100%) [buf 100%]  43.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  495 of  690 MB written (fifo  99%) [buf 100%]  43.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  496 of  690 MB written (fifo  99%) [buf 100%]  43.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  497 of  690 MB written (fifo  99%) [buf 100%]  42.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  498 of  690 MB written (fifo 100%) [buf 100%]  44.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  499 of  690 MB written (fifo  99%) [buf 100%]  45.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  500 of  690 MB written (fifo  98%) [buf 100%]  44.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  501 of  690 MB written (fifo 100%) [buf 100%]  44.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  502 of  690 MB written (fifo 100%) [buf 100%]  44.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  503 of  690 MB written (fifo  99%) [buf 100%]  45.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  504 of  690 MB written (fifo  99%) [buf 100%]  43.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  505 of  690 MB written (fifo 100%) [buf 100%]  45.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  506 of  690 MB written (fifo 100%) [buf 100%]  43.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  507 of  690 MB written (fifo 100%) [buf 100%]  45.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  508 of  690 MB written (fifo  99%) [buf 100%]  44.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  509 of  690 MB written (fifo  99%) [buf 100%]  44.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  510 of  690 MB written (fifo  99%) [buf 100%]  44.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  511 of  690 MB written (fifo  99%) [buf 100%]  45.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  512 of  690 MB written (fifo  99%) [buf 100%]  43.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  513 of  690 MB written (fifo 100%) [buf 100%]  45.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  514 of  690 MB written (fifo 100%) [buf 100%]  43.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  515 of  690 MB written (fifo 100%) [buf 100%]  45.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  516 of  690 MB written (fifo  99%) [buf 100%]  43.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  517 of  690 MB written (fifo  99%) [buf 100%]  45.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  518 of  690 MB written (fifo 100%) [buf 100%]  42.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  519 of  690 MB written (fifo  99%) [buf 100%]  45.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  520 of  690 MB written (fifo  99%) [buf 100%]  43.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  521 of  690 MB written (fifo 100%) [buf 100%]  45.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  522 of  690 MB written (fifo 100%) [buf 100%]  43.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  523 of  690 MB written (fifo  99%) [buf 100%]  45.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  524 of  690 MB written (fifo  99%) [buf 100%]  43.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  525 of  690 MB written (fifo 100%) [buf 100%]  45.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  526 of  690 MB written (fifo  99%) [buf 100%]  44.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  527 of  690 MB written (fifo 100%) [buf 100%]  45.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  528 of  690 MB written (fifo 100%) [buf 100%]  43.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  529 of  690 MB written (fifo 100%) [buf 100%]  44.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  530 of  690 MB written (fifo  99%) [buf 100%]  47.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  531 of  690 MB written (fifo 100%) [buf 100%]  44.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  532 of  690 MB written (fifo 100%) [buf 100%]  46.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  533 of  690 MB written (fifo 100%) [buf 100%]  44.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  534 of  690 MB written (fifo  99%) [buf 100%]  47.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  535 of  690 MB written (fifo 100%) [buf 100%]  44.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  536 of  690 MB written (fifo  97%) [buf 100%]  46.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  537 of  690 MB written (fifo  98%) [buf 100%]  44.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  538 of  690 MB written (fifo 100%) [buf 100%]  46.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  539 of  690 MB written (fifo  99%) [buf 100%]  45.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  540 of  690 MB written (fifo  99%) [buf 100%]  46.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  541 of  690 MB written (fifo 100%) [buf 100%]  44.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  542 of  690 MB written (fifo  99%) [buf 100%]  46.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  543 of  690 MB written (fifo  99%) [buf 100%]  45.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  544 of  690 MB written (fifo 100%) [buf 100%]  46.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  545 of  690 MB written (fifo  99%) [buf 100%]  42.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  546 of  690 MB written (fifo 100%) [buf 100%]  48.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  547 of  690 MB written (fifo  99%) [buf 100%]  44.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  548 of  690 MB written (fifo  99%) [buf 100%]  46.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  549 of  690 MB written (fifo  98%) [buf 100%]  44.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  550 of  690 MB written (fifo  99%) [buf 100%]  46.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  551 of  690 MB written (fifo  99%) [buf 100%]  45.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  552 of  690 MB written (fifo 100%) [buf 100%]  46.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  553 of  690 MB written (fifo 100%) [buf 100%]  44.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  554 of  690 MB written (fifo  99%) [buf 100%]  45.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  555 of  690 MB written (fifo  99%) [buf 100%]  45.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  556 of  690 MB written (fifo 100%) [buf 100%]  46.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  557 of  690 MB written (fifo  96%) [buf 100%]  45.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  558 of  690 MB written (fifo  99%) [buf 100%]  46.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  559 of  690 MB written (fifo 100%) [buf 100%]  44.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  560 of  690 MB written (fifo  99%) [buf 100%]  46.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  561 of  690 MB written (fifo  99%) [buf 100%]  47.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  562 of  690 MB written (fifo  99%) [buf 100%]  45.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  563 of  690 MB written (fifo  99%) [buf 100%]  47.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  564 of  690 MB written (fifo 100%) [buf 100%]  45.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  565 of  690 MB written (fifo  99%) [buf 100%]  46.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  566 of  690 MB written (fifo  99%) [buf 100%]  47.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  567 of  690 MB written (fifo 100%) [buf 100%]  47.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  568 of  690 MB written (fifo 100%) [buf 100%]  46.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  569 of  690 MB written (fifo 100%) [buf 100%]  47.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  570 of  690 MB written (fifo  99%) [buf 100%]  45.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  571 of  690 MB written (fifo  99%) [buf 100%]  47.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  572 of  690 MB written (fifo 100%) [buf 100%]  45.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  573 of  690 MB written (fifo  99%) [buf 100%]  47.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  574 of  690 MB written (fifo  99%) [buf 100%]  45.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  575 of  690 MB written (fifo  99%) [buf 100%]  47.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  576 of  690 MB written (fifo 100%) [buf 100%]  45.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  577 of  690 MB written (fifo  97%) [buf 100%]  47.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  578 of  690 MB written (fifo  99%) [buf 100%]  45.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  579 of  690 MB written (fifo  99%) [buf 100%]  48.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  580 of  690 MB written (fifo  99%) [buf 100%]  45.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  581 of  690 MB written (fifo  99%) [buf 100%]  47.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  582 of  690 MB written (fifo 100%) [buf 100%]  45.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  583 of  690 MB written (fifo 100%) [buf 100%]  47.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  584 of  690 MB written (fifo 100%) [buf 100%]  46.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  585 of  690 MB written (fifo  99%) [buf 100%]  46.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  586 of  690 MB written (fifo  97%) [buf 100%]  46.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  587 of  690 MB written (fifo 100%) [buf 100%]  47.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  588 of  690 MB written (fifo  99%) [buf 100%]  45.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  589 of  690 MB written (fifo  99%) [buf 100%]  46.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  590 of  690 MB written (fifo 100%) [buf 100%]  45.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  591 of  690 MB written (fifo  99%) [buf 100%]  47.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  592 of  690 MB written (fifo 100%) [buf 100%]  47.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  593 of  690 MB written (fifo 100%) [buf 100%]  47.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  594 of  690 MB written (fifo 100%) [buf 100%]  48.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  595 of  690 MB written (fifo  99%) [buf 100%]  47.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  596 of  690 MB written (fifo  99%) [buf 100%]  48.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  597 of  690 MB written (fifo 100%) [buf 100%]  47.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  598 of  690 MB written (fifo  98%) [buf  98%]  47.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  599 of  690 MB written (fifo  99%) [buf 100%]  48.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  600 of  690 MB written (fifo  98%) [buf 100%]  48.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  601 of  690 MB written (fifo 100%) [buf 100%]  46.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  602 of  690 MB written (fifo  98%) [buf 100%]  48.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  603 of  690 MB written (fifo  98%) [buf 100%]  46.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  604 of  690 MB written (fifo 100%) [buf 100%]  48.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  605 of  690 MB written (fifo  99%) [buf 100%]  46.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  606 of  690 MB written (fifo  99%) [buf 100%]  47.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  607 of  690 MB written (fifo 100%) [buf 100%]  47.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  608 of  690 MB written (fifo  99%) [buf 100%]  47.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  609 of  690 MB written (fifo  99%) [buf 100%]  47.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  610 of  690 MB written (fifo  99%) [buf 100%]  47.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  611 of  690 MB written (fifo 100%) [buf 100%]  47.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  612 of  690 MB written (fifo 100%) [buf 100%]  48.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  613 of  690 MB written (fifo  98%) [buf 100%]  46.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  614 of  690 MB written (fifo 100%) [buf 100%]  48.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  615 of  690 MB written (fifo  99%) [buf 100%]  46.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  616 of  690 MB written (fifo  99%) [buf 100%]  47.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  617 of  690 MB written (fifo  99%) [buf 100%]  46.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  618 of  690 MB written (fifo  99%) [buf 100%]  45.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  619 of  690 MB written (fifo  97%) [buf 100%]  48.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  620 of  690 MB written (fifo  99%) [buf 100%]  47.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  621 of  690 MB written (fifo  99%) [buf 100%]  47.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  622 of  690 MB written (fifo  99%) [buf 100%]  47.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  623 of  690 MB written (fifo  99%) [buf 100%]  49.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  624 of  690 MB written (fifo  99%) [buf 100%]  48.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  625 of  690 MB written (fifo  99%) [buf 100%]  49.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  626 of  690 MB written (fifo  99%) [buf 100%]  47.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  627 of  690 MB written (fifo  99%) [buf 100%]  49.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  628 of  690 MB written (fifo  99%) [buf 100%]  47.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  629 of  690 MB written (fifo  99%) [buf 100%]  49.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  630 of  690 MB written (fifo 100%) [buf 100%]  48.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  631 of  690 MB written (fifo  99%) [buf 100%]  49.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  632 of  690 MB written (fifo 100%) [buf 100%]  47.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  633 of  690 MB written (fifo 100%) [buf 100%]  49.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  634 of  690 MB written (fifo  99%) [buf 100%]  48.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  635 of  690 MB written (fifo  99%) [buf 100%]  49.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  636 of  690 MB written (fifo 100%) [buf 100%]  47.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  637 of  690 MB written (fifo  99%) [buf 100%]  49.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  638 of  690 MB written (fifo  99%) [buf 100%]  47.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  639 of  690 MB written (fifo  99%) [buf 100%]  49.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  640 of  690 MB written (fifo  99%) [buf 100%]  47.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  641 of  690 MB written (fifo 100%) [buf 100%]  48.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  642 of  690 MB written (fifo  99%) [buf 100%]  47.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  643 of  690 MB written (fifo  99%) [buf 100%]  48.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  644 of  690 MB written (fifo 100%) [buf 100%]  47.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  645 of  690 MB written (fifo 100%) [buf 100%]  49.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  646 of  690 MB written (fifo  99%) [buf 100%]  45.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  647 of  690 MB written (fifo  99%) [buf 100%]  52.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  648 of  690 MB written (fifo 100%) [buf 100%]  46.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  649 of  690 MB written (fifo 100%) [buf 100%]  48.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  650 of  690 MB written (fifo  99%) [buf 100%]  48.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  651 of  690 MB written (fifo  99%) [buf 100%]  49.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  652 of  690 MB written (fifo  99%) [buf 100%]  47.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  653 of  690 MB written (fifo  98%) [buf 100%]  48.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  654 of  690 MB written (fifo  98%) [buf 100%]  50.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  655 of  690 MB written (fifo  97%) [buf 100%]  46.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  656 of  690 MB written (fifo  97%) [buf 100%]  53.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  657 of  690 MB written (fifo 100%) [buf 100%]  48.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  658 of  690 MB written (fifo 100%) [buf 100%]   0.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  659 of  690 MB written (fifo 100%) [buf 100%]   0.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  660 of  690 MB written (fifo 100%) [buf 100%]   0.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  661 of  690 MB written (fifo 100%) [buf 100%]   0.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  662 of  690 MB written (fifo 100%) [buf 100%]   0.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  663 of  690 MB written (fifo 100%) [buf 100%]   0.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  664 of  690 MB written (fifo 100%) [buf 100%]   0.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  665 of  690 MB written (fifo  99%) [buf 100%]   0.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  666 of  690 MB written (fifo  99%) [buf 100%]  49.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  667 of  690 MB written (fifo  99%) [buf 100%]  48.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  668 of  690 MB written (fifo 100%) [buf 100%]  50.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  669 of  690 MB written (fifo  98%) [buf 100%]  47.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  670 of  690 MB written (fifo  99%) [buf 100%]  51.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  671 of  690 MB written (fifo 100%) [buf 100%]  48.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  672 of  690 MB written (fifo  99%) [buf 100%]  50.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  673 of  690 MB written (fifo  99%) [buf 100%]  48.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  674 of  690 MB written (fifo 100%) [buf 100%]  49.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  675 of  690 MB written (fifo  99%) [buf 100%]  48.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  676 of  690 MB written (fifo 100%) [buf 100%]  49.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  677 of  690 MB written (fifo 100%) [buf 100%]  48.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  678 of  690 MB written (fifo 100%) [buf 100%]  50.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  679 of  690 MB written (fifo 100%) [buf 100%]  46.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  680 of  690 MB written (fifo 100%) [buf 100%]  51.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  681 of  690 MB written (fifo 100%) [buf 100%]  48.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  682 of  690 MB written (fifo 100%) [buf 100%]  49.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  683 of  690 MB written (fifo 100%) [buf 100%]  48.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  684 of  690 MB written (fifo 100%) [buf 100%]  49.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  685 of  690 MB written (fifo 100%) [buf 100%]  50.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  686 of  690 MB written (fifo 100%) [buf 100%]  48.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  687 of  690 MB written (fifo 100%) [buf 100%]  51.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  688 of  690 MB written (fifo 100%) [buf 100%]  49.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  689 of  690 MB written (fifo 100%) [buf 100%]  49.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  690 of  690 MB written (fifo 100%) [buf 100%]  47.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01: Total bytes read/written: 724353024/724353024 (353688 sectors).
BraseroWodim stdout: Writing  time:  489.645s
BraseroWodim stdout: Average write speed   9.9x.
BraseroWodim stdout: Min drive buffer fill was 98%
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stderr: Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  5B 00 02 00 00 00 00 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Fixating time:   30.419s
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 03 00 05 65 9A 0A 00 00 00 00 0C 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x3 Medium Error, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 353690 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 30.397s timeout 480s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 30.397s timeout 480s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Cannot fixate disk.
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
    error        = 15
    message    = "An error occurred while writing to disc"
BraseroWodim stopping
BraseroWodim got killed
Session error : An error occurred while writing to disc (brasero_burn_record brasero-burn.c:2808)  
I looked and there are files on the disc so im gonna do another copy on the laptop and give it a go

---

### Post by rgbargee on 2009-12-02
ok everyone i now have a clean install of karmic to play with, i tried the 64bit script unfortunately only partial success , i think the test bed (rollercoaster kingdom on facebook) is a particularly stiff task but if windows flash can play shouldnt karmic flash too? after all its still adobe flash anyway the other issue i was having re my burner not working seems actually to mean it burns but incorrectly (possibly how it finalises the disc , and finally (for now :) ) my joypad still doesnt work  plug it in-nothing ,play a game (alien arena) - nothing im gonna try a few more games to see if i can get any input from it so all in all i needent have reinstalled lol . hey ho you wins some you lose some and it made me dump all the rubbish ebooks n lame music i had collected - any ideas ?

---

### Post by rgbargee on 2009-12-06
i guess everyones busy at the mo , the new release seems to be bringing some griping pains, i dont know why but ive got a feeling my usb ports may be a problem regarding the controller, ive just tried a pen drive that doesnt work and a samsung mobile same deal , could usb be the problem or am i clutching the proverbial

---

### Post by natex on 2009-12-06
If you don't have more that 4 gigs of RAM you are probably better off using 32 bit for now.

---

### Post by rgbargee on 2009-12-06
@natex wow i never thought 1 gig of ram could be the problem , i couldnt get 32 bit to install have you seen a work round on your travels ?

---

### Post by natex on 2009-12-06
I just mean that you are not likely to see any benefits using a 64bit OS unless you have more than 4 gigs of RAM. 

What kind of processor is it? I am using an intel core2 quad 6600 with Karmic 64 bit and it runs *flawlessly*. 

natex

---

### Post by rgbargee on 2009-12-06
now thats a processor lol mines an amd64 4000+ x2 or something like that  but im struggling with so many things i was kinda hoping that i could find a way to install 32 bit guess i should download the image and post the problems im having , it may be the best way to get it up and running first ill have to install 32 on my boyz pc so i can post the problems lol

---


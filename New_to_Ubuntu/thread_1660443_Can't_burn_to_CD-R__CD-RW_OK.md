---
title: "Can't burn to CD-R : CD-RW OK"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by s1wood on 2011-01-05
My computer will not burn ISOs onto CD-R discs.
Kfb said 'probably the writer does not like the medium.'
It burns OK onto CD-RW disks.
This computer has burned to CD-R on previous occasions but this is a new batch of disks from a different manufacturer.
The new CD-R disks can be burned on my older computer (running Puppy) so the disks are not faulty.
The main computer will not burn data to these CD-R disks either - 'writer does not like medium' again

I have a pack of 50 of these new disks, they were a present so I can't even take them back. Is there any way I might be able to persuade this DVD writer to accept them? I suppose swapping the writer from the other machine might be the answer but I was hoping for something less labour intensive. 

regards,

Susan

---

### Post by TeoBigusGeekus on 2011-01-05
Try with wodim from command line
```
wodim -v dev=/dev/cdrw path/to/image/imagename.iso
```
Replace /dev/cdrw with whatever applies to your system (ie. sr0, dvd, etc).

---

### Post by laidback on 2011-01-05
I get the impression that you're trying with K3b which is normally excellent. But, have you also tried with Brasero, the default burner on my system. It doesn't seem to be quite as picky as K3b in my experience.

---

### Post by s1wood on 2011-01-06
I used Brasero at first then tried kfb because it kept getting recommended, xfburn has the same problem as well. 
I tried the terminal command and it came up with an identification of the writer and a load of info about it but then said 'command not found' over the 'path' section. I can redo it and paste it if it would help.
My old external CD writer seems happy with these disks but I really don't like all the extra wires and plugs when I've got an internal drive I should be able to use.

regards,

Susan

---

### Post by TeoBigusGeekus on 2011-01-06
Could you please post us the command you executed and the full error message?

---

### Post by laidback on 2011-01-06
Perhaps it needs cleaning. I believe you can get a disc that once inserted cleans the lens but I have no experience of it.

---

### Post by s1wood on 2011-01-07
susan@Carrera:~$ wodim -v dev=/dev/sr0 path/to/image/imagename.iso
wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.10
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'SONY    '
Identification : 'DVD RW DRU-500A '
Revision       : '2.0e'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0000 (Reserved/Unknown)
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 8112896 = 7922 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Drive DMA Speed: 21361 kB/s 121x CD 15x DVD
FIFO size      : 12582912 = 12288 KB
wodim: No such file or directory. Cannot open 'path/to/image/imagename.iso'.
susan@Carrera:~$ 

Does that mean anything to you? 

Susan

(You may be right about the cleaning - this is an old machine and I certainly haven't cleaned the DVD writer, but I can't see why that should affect one type of disk and not another.)

---

### Post by QLee on 2011-01-07
[QUOTE=s1wood]susan@Carrera:~$ wodim -v dev=/dev/sr0 path/to/image/imagename.iso
...
wodim: No such file or directory. Cannot open 'path/to/image/imagename.iso'.
susan@Carrera:~$ 

Does that mean anything to you? 

...[/QUOTE]

Yes and it should to you too Susan. See the last line, I believe it was meant for you to try the burn on an actual  filename that exists on your system. It would be a good choice to use one of the ones that you have tried that is not working.

---

### Post by wep940 on 2011-01-07
If you don't understand what QLee is saying, right now you are just using path/to/image/imagename.iso as the identity of the file.  Obviously that string is just meant as a sample to you so you could substitute the real values.
 
For example, if you have a file xyz.iso, and if it is in a folder of my/isoimages, then you would substitute the string as:
 
my/isoimages/xyz.iso
 
Hopefully you know where your iso image is -> just substitute the path to it and the filename of the actual iso and it should work.

---

### Post by s1wood on 2011-01-07
Thank you, I need to have these things explained to me in very simple terms.
I will try and work out what the path is and give it a go.

Susan

---

### Post by QLee on 2011-01-08
[QUOTE=s1wood]Thank you, I need to have these things explained to me in very simple terms.
I will try and work out what the path is and give it a go.

Susan[/QUOTE]

I know from working with you previously that you are not stupid or challenged and can grasp concepts once they make sense to you. I'd guess what gets in your way is that when you see a long readout you assume you don't understand any of it and thus don't read it carefully. Always consider at least the last line when it is an error message, it often contains a hint of what went wrong. You'll get better at this stuff as time passes, there are much worse manifestations of mid-life crisis, computers can be fun.

---

### Post by wep940 on 2011-01-08
+1 - life's too short to make something that is basically as stupid as a computer (yes, they are dumb, lacking intelligence without us) bother us.  It's best to go at it as something fun, something you can set aside for an hour, a day, whatever, when it starts to bother you.  I think that is the biggest mistake people make when they want to try linux of any flavor - they jump right into it without trying something like the dual-boot option first.  At least when you dual-boot you still have a useable computer while you can take your time getting the linux side set up and running.
 
It also applies, like you said, to every other portion of these things.  Documents, especially when long and you are looking for a solution quickly, can be daunting.  New verbage, new ideas, new concepts.  Most, if not all, of us need to re-read something more than once (except of course for those things which we consider simple or easy based on our experience).  We need to digest what's being said.  Sometimes we even just have to try what's being said to see what happens.
 
So, nobody is ever stupid.  Don't ever feel that way!

---

### Post by s1wood on 2011-01-09
Thank you for reassuring remarks. :)

Here is the result of the test (just the end section):(

ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 10651
Speed set to 4234 KB/s
Starting to write CD/DVD at speed  24.0 in real TAO mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 12 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 46.260s timeout 60s
wodim: OPC failed.
Writing  time:   46.298s
wodim: fifo had 192 puts and 0 gets.
wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

Any suggestions? Like: get the screwdriver out and swap drives?

Susan

---

### Post by wep940 on 2011-01-09
I would try swapping the drive.  I don't really think it is defective, and it sounds like the media is okay, but I have seen several posts lately about errors trying to burn with Brasero (which it turn uses wodim).  These errors are usually rather strange, with no clear reason for the failure.  Some think it may be something with the "talking" to the drive, so swapping the drive can't hurt, just can't guarantee it's going to fix anything.
 
Also, when it does fail, you do just use the disk for a coaster, right?  Can't re-use a cd-r after a failure since you're not sure if it wrote to it or not.

---

### Post by s1wood on 2011-01-10
Screwdriver and horrible fiddly little screws it is then. 
Actually I have reused some of those CDRs successfully - nothing to lose by it, they either work or they don't. I've mainly been burning liveCDs and they've all been working OK. I certainly don't put the CDs back in the pack unidentified though.

Thanks for all the advice.

Susan

---

### Post by wep940 on 2011-01-13
I hope it works - let us know either way.
 
Perfect description of those dang little screws.  When you have hands about the size of Hagrid's it's pretty hard to even grab those dang things!

---


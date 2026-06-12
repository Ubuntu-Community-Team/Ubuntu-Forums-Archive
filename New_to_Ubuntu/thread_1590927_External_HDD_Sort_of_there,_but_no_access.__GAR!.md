---
title: "External HDD Sort of there, but no access.  GAR!"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by jakwriter on 2010-10-08
Still consider myself noob, but know just enough to send everything fubar.

80G HDD out of an old HP laptop that has been formatted many times while living in a USB case.  For the last year it has served as my Ubuntu backup/archive.  Worked fine with Lucid until about a month ago. For what I'm sure is a good reason, it's gone haywire.

Disk Utility picks it up, but without complete information.  "Myson Century Inc. USB Mass Storage Device."  Then it lists it as both /dev/sdb under one Device spot, and /dev/sdb1 under the other.  Partition Type: Unknown.  However it does know it's and 80G drive.

Here's some output
 Drive disconnected

```
dax@Hoth:~$ dmesg | tail
[ 3736.986550] sd 5:0:0:0: [sdb] Sense Key : Illegal Request [current] 
[ 3736.986560] sd 5:0:0:0: [sdb] Add. Sense: Invalid command operation code
[ 3736.986572] sd 5:0:0:0: [sdb] CDB: Read(6): 08 00 00 00 08 00 00 00 00 00 00 00
[ 3736.986599] end_request: I/O error, dev sdb, sector 0
[ 3736.987554] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3736.987564] sd 5:0:0:0: [sdb] Sense Key : Illegal Request [current] 
[ 3736.987574] sd 5:0:0:0: [sdb] Add. Sense: Invalid command operation code
[ 3736.987586] sd 5:0:0:0: [sdb] CDB: Read(6): 08 00 00 00 08 00 00 00 00 00 00 00
[ 3736.987613] end_request: I/O error, dev sdb, sector 0
[ 3944.624338] usb 1-1: USB disconnect, address 6

```

Drive Connected
```

dax@Hoth:~$ ls /dev/sd?
/dev/sda

```

Still connected
```
dax@Hoth:~$ dmesg | tail -n 20
[ 4150.687198] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4150.687208] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
[ 4150.687219] sd 6:0:0:0: [sdb] Add. Sense: Invalid command operation code
[ 4150.687232] sd 6:0:0:0: [sdb] CDB: Read(6): 08 00 10 3f 08 00 00 00 00 00 00 00
[ 4150.687259] end_request: I/O error, dev sdb, sector 4159
[ 4150.688328] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4150.688338] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
[ 4150.688349] sd 6:0:0:0: [sdb] Add. Sense: Invalid command operation code
[ 4150.688361] sd 6:0:0:0: [sdb] CDB: Read(6): 08 00 00 00 20 00 00 00 00 00 00 00
[ 4150.688388] end_request: I/O error, dev sdb, sector 0
[ 4150.689326] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4150.689336] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
[ 4150.689347] sd 6:0:0:0: [sdb] Add. Sense: Invalid command operation code
[ 4150.689359] sd 6:0:0:0: [sdb] CDB: Read(6): 08 00 00 00 08 00 00 00 00 00 00 00
[ 4150.689386] end_request: I/O error, dev sdb, sector 0
[ 4150.690322] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4150.690332] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current] 
[ 4150.690343] sd 6:0:0:0: [sdb] Add. Sense: Invalid command operation code
[ 4150.690355] sd 6:0:0:0: [sdb] CDB: Read(6): 08 00 00 00 08 00 00 00 00 00 00 00
[ 4150.690382] end_request: I/O error, dev sdb, sector 0
```

And just for G.P. with the drive connected

```
dax@Hoth:~$ /dev/sd
bash: /dev/sd: No such file or directory
dax@Hoth:~$ /dev/sd?
bash: /dev/sda: Permission denied
dax@Hoth:~$ 
```

```
dax@Hoth:~$ cd /media
dax@Hoth:/media$ ls -l
total 0
dax@Hoth:/media$ 

```

Does the above mean my /media file is completely empty?  *Should* there be something in it? 

Now while I've some idea that some of this out put *might* be useful, I have no idea what too look for.  Any hints, tips, or plain old directions would be greatly appreciated.  Pictures, music, stories, it'd be nice to avoid losing them.

Thanks

---

### Post by DarthScape on 2010-10-08
#1: Does it work on another computer?
#2: Does it happen with multiple ports on the computer?
#3: If you boot the Ubuntu Live CD, or another Live CD, does it mount on there?

---

### Post by jakwriter on 2010-10-09
> #1: Does it work on another computer?
#2: Does it happen with multiple ports on the computer?
#3: If you boot the Ubuntu Live CD, or another Live CD, does it mount on there?

On the Mac I get "The disk you inserted was not readable by this computer."  It's Disk Utility doesn't pick up the external either.

I've tried it in all three of my USB ports with no change.

And (hadn't thought of this) no luck running the 10.04 Live CD.  In terminal it still returns a 'total 0' to the ls -l in /media.

I'm sure I'm missing something in Terminal Land.  Having no idea what it all means is definitely getting in the way.  I'd bet a gig stick that three or four commands would fix it, if only I knew what they were . . . .

---

### Post by DarthScape on 2010-10-09
> **jakwriter said:**
> On the Mac I get "The disk you inserted was not readable by this computer."  It's Disk Utility doesn't pick up the external either.

I've tried it in all three of my USB ports with no change.

And (hadn't thought of this) no luck running the 10.04 Live CD.  In terminal it still returns a 'total 0' to the ls -l in /media.

I'm sure I'm missing something in Terminal Land.  Having no idea what it all means is definitely getting in the way.  I'd bet a gig stick that three or four commands would fix it, if only I knew what they were . . . .

Dood, if the mac disk utility does not pick it up, then there is definitely a problem with the drive.

---

### Post by theozzlives on 2010-10-09
So far all we know is you're not recognizing the format of the filesystem. What filesystem you trying to use?

---

### Post by DarthScape on 2010-10-09
NO! If the Mac Disk Utility doesn't even show the drive on the left side, then it does not recognize it as a drive, therefor, not format-able, even to a readable format. With that disk utility, you can change everything about the drive, partition table and all. Unless we aren't being told something.

---

### Post by srs5694 on 2010-10-09
The dmesg output indicates I/O errors, which screams "hardware fault" to me; I doubt if it's just a damaged filesystem.

On the glass-is-half-full side, it could be the USB interface hardware that's at fault, rather than the hard disk itself. I recommend running a SMART test on the drive, assuming you can get the SMART utility to recognize the drive. (Try GSmartControl or smartctl, among others.) If the SMART utility recognizes the drive and reports errors, then you can be pretty sure the drive has gone south.

If the SMART utility can't find the drive, then you may need to pull the disk from the external enclosure and either connect the disk directly to a computer or put another drive into the enclosure. You can then test -- if the drive connected directly exhibits problems, you can be pretty confident that it's at fault; or if the external enclosure with another disk shows the same symptoms, you can be pretty sure it's gone bad.

---

### Post by jakwriter on 2010-10-11
As to the file system . . . I can't say for sure.  I formatted it so long ago that I wasn't even paying attention to anything but erasing it.  Whatever the default file system of probably Karmic was, FAT?

I think there may be an issue with the hardware though.  I will try it in a case that does function, but the drive is old enough that it may be wearing out.  That HDD did spend about six months in the laptop I had in Baghdad in '04.  

I appreciate the help.  I'll get the results of a different case up here as soon as I get home.

Update:  Switched HDD from Coolmax to NexStar-SX case to no avail.  The disk spun for a couple minutes that's all.  Same result from ls -l.

---


---
title: "Flash drive issues"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by cloyd on 2010-01-31
I have 2 issues with flash drives.  One I took out one day without properly unmounting it. It hasn't worked on UNR 9.10 since.  I have reformatted it, and it still doesn't work.  Interestingly enough, it works on a machine running 9.04.

The other is trying to use Sandisk Cruzer drives.  When I try to mount them, I get "Error mounting: mount exited with exit code 1: helper failed . . ." I can mount these drives with gparted, but must unmount with gparted also.  And  . . . I can view the drives contents, but cannot write to or copy from them in 9.10 because it says "permission denied."  No such issues in 9.04. 

I've seen similar threads, but none have solved my problem.

This isn't the end of the world, but I'd really like to solve this.  Any ideas?

---

### Post by cloyd on 2010-02-11
bump

I don't know if the solution is too obvious, and nobody wants to answer, or nobody knows the answer. I get the same problem with an external hard drive, and my old Sandisk Mp3 player. I'l like a little help. I would sure appreciate it. If I need to post more information, I'll try to get it.

One thing I just realized. When I mount with gparted, I can copy files *from* the external drives, but not *to* them.  I had kept trying to write to the drives. I just realized that I could copy from them.

---

### Post by cloyd on 2010-02-11
Ok, I have at least partially solved it.  I can mount my sandisk drive by

mkdir usb

sudo mount -t vfat /dev/sdb1 /media/usb -o uid=1000,gid=100,utf8,dmask=027,fmask=137

the drive is totally usable this way, but must be unmounted with umount.  Don'[ seem to need anything after -o, but still must mount with this entire command again to use again. Will not automount. I need to try this on the usb hard drive, and the mp3 player. But this is a victory for me.  I  do wish I understood all the code that I entered.   

Does this solution help anyone else?

---

### Post by ScottinSoCal on 2010-02-11
I'm not a guru, but I'll throw my wild guesses on here, based on a dangerously small knowledge base.

I think it depends on how your computer recognizes the drive. When I put in a flash drive, it mounts to my desktop, and I can read/write. When I put in my notebook's hdd module, I had to edit things to make it mount under my home directory. Before I edited fstab, it wouldn't automount, I had to use a utility to do it. It also mounted as was owned by root, and I didn't have access to write to it. I have an mp3 player that does the same thing - it's recognized as a hard drive, not an mp3 player. When I changed it so it mounts under my home folder, problem was gone.

---

### Post by samantha_ on 2010-02-11
> **cloyd said:**
> Ok, I have at least partially solved it.  I can mount my sandisk drive by

mkdir usb

sudo mount -t vfat /dev/sdb1 /media/usb -o uid=1000,gid=100,utf8,dmask=027,fmask=137

the drive is totally usable this way, but must be unmounted with umount.  Don'[ seem to need anything after -o, but still must mount with this entire command again to use again. Will not automount. I need to try this on the usb hard drive, and the mp3 player. But this is a victory for me.  I  do wish I understood all the code that I entered.   

Does this solution help anyone else?

add this to /etc/fstab
```

/dev/sdb1	/media/usb	vfat	rw,noauto,id=1000,gid=100,utf8,dmask=027,fmask=137	0 0
```

---

### Post by cloyd on 2010-02-11
Thanks for chiming in. I will make that change to fstab . . . tomorrow.  I have experimented a bit this evening. It works with my Sandisk flash drives, it works with the Seagate hard drive, and it works with the mp3 player.  One more thing learned.  

This took a while, but I like the fact that I do actually learn something (yes, I understood some of that command, but not near all of it).  In the old days, in Windows, I'd call on a help line, and the answer was invariably "reinstall the software, or the driver, or whatever".  I never learned anything.

Having fun here. 

I'm looking forward to the time when I can help someone else.

---

### Post by samantha_ on 2010-02-11
> **cloyd said:**
> Thanks for chiming in. I will make that change to fstab . . . tomorrow.  I have experimented a bit this evening. It works with my Sandisk flash drives, it works with the Seagate hard drive, and it works with the mp3 player.  One more thing learned.  

This took a while, but I like the fact that I do actually learn something (yes, I understood some of that command, but not near all of it).  In the old days, in Windows, I'd call on a help line, and the answer was invariably "reinstall the software, or the driver, or whatever".  I never learned anything.

Having fun here. 

I'm looking forward to the time when I can help someone else.

oh, btw, if your curious, that above line will hopefully override how ubuntu mounts the drives. Which means that ubuntu will mount the drive according to the commands that you said worked for you (I translated the command you posted into the fstab format)

---

### Post by JKyleOKC on 2010-02-11
> **cloyd said:**
> sudo mount -t vfat /dev/sdb1 /media/usb -o uid=1000,gid=100,utf8,dmask=027,fmask=137

I do wish I understood all the code that I entered.The "-o" is the short form for the "options" argument, and what follows are the options themselves. The uid and gid numbers are your own user ID and group ID, making you the owner of the device and thus having full read-write control of it. The two masks establish permissions for directories (d) and files (f): read-only for other group members, and no access for anyone else. These masks are XORed with default permissions of 777 to create the permissions: 750 for directories and 640 for files. If you need more info about the permission flags, try "man chmod" for it -- or just ask here!

Hope this helps.

---

### Post by cloyd on 2010-02-12
> **samantha_ said:**
> add this to /etc/fstab
```

/dev/sdb1    /media/usb    vfat    rw,noauto,id=1000,gid=100,utf8,dmask=027,fmask=137    0 0
```

I tried changing that line in fstab. I tried putting it in place of another line which referenced media/usb. I Put a #in front of  the old line . . . did not erase it.  Did not key in the line, but pasted it (finally learned that in terminal it is (control *shift* v, not just control shift).  Hey, I'm green.

It still will not automount,  Still had to use the whole long command to mount.  

The thought occurred to me.  Pardon me thinking bash is anything like DOS, but I remember writing batch files in DOS. So could I give that whole long command (less the sudo) one name and run it like that?   That would be almost as good as auto mounting.  I think that is a very elementary question, but at this point, I have to ask.

Bought a new book today on command line. I plan on learning a bit more.

---

### Post by cloyd on 2010-02-12
Ok, again, I was able to find an answer.

I always need to remember: Google is my friend.  Just need to figure out how to phrase the question.

  First, use gedit and create file Sandisk (because the primary use of this is to manage Sandisk usb's, and also others) by simply pasting the long command (including the sudo) into gedit.  Save the file. run chmod 755 Sandisk.  Then exectule the command by typing ./Sandisk. Wrote a similar uSandisk to unmount.

Told my wife I was proud of myself for writing my first executable script file. She said it didn't take too much to make me feel that way. 

Oh, well. . .
Having fun.

---

### Post by spiderbatdad on 2010-02-12
a clue to finding out why the drive is mounting read only is to run the command ```
dmesg | tail
``` After fist plugging the drive in...that is do not run any mount commands, just see what dmesg says about the device.

---

### Post by cloyd on 2010-02-12
Output of dmesg | tail is

[ 2787.776794] sr 8:0:0:1: [sr0] Unhandled sense code
[ 2787.776800] sr 8:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 2787.776805] sr 8:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 2787.776812] sr 8:0:0:1: [sr0] Add. Sense: No additional sense information
[ 2787.776819] end_request: I/O error, dev sr0, sector 196600
[ 2787.781430] sr 8:0:0:1: [sr0] Unhandled sense code
[ 2787.781434] sr 8:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 2787.781440] sr 8:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 2787.781446] sr 8:0:0:1: [sr0] Add. Sense: No additional sense information
[ 2787.781452] end_request: I/O error, dev sr0, sector 196600
steve@steve-laptop:~$ dmesg | tail
[ 3096.047053] sr 9:0:0:1: [sr0] Unhandled sense code
[ 3096.047059] sr 9:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 3096.047065] sr 9:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 3096.047071] sr 9:0:0:1: [sr0] Add. Sense: No additional sense information
[ 3096.047078] end_request: I/O error, dev sr0, sector 196600
[ 3096.051300] sr 9:0:0:1: [sr0] Unhandled sense code
[ 3096.051304] sr 9:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 3096.051309] sr 9:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 3096.051315] sr 9:0:0:1: [sr0] Add. Sense: No additional sense information
[ 3096.051322] end_request: I/O error, dev sr0, sector 196600


Feel good so far. Learned a lot. But I'm sure what I see here. I do see several "Hardware Error"


Looks like I have the output for running the command twice

---

### Post by spiderbatdad on 2010-02-12
not sure. I would try two things. First make sure you have usb mount installed. ```
sudo apt-get install usbmount
```
Test..

If not fixed try fsck

```
sudo fsck /dev/sdb1 (or whatever the dev is)
```

---

### Post by spiderbatdad on 2010-02-12
need to see more of dmesg...from the time it first sees the device...
 like: 
```
dmesg | tail -n 50
```

---

### Post by cloyd on 2010-02-12
Here it is:

[ 9444.341837] sr 12:0:0:1: [sr0] Add. Sense: No additional sense information
[ 9444.341845] end_request: I/O error, dev sr0, sector 196600
[ 9444.341853] Buffer I/O error on device sr0, logical block 49150
[ 9444.342085] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 9444.342098] ISOFS: changing to secondary root
[ 9444.355687] sr 12:0:0:1: [sr0] Unhandled sense code
[ 9444.355695] sr 12:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 9444.355702] sr 12:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 9444.355709] sr 12:0:0:1: [sr0] Add. Sense: No additional sense information
[ 9444.355717] end_request: I/O error, dev sr0, sector 196600
[ 9444.371209] sr 12:0:0:1: [sr0] Unhandled sense code
[ 9444.371218] sr 12:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 9444.371224] sr 12:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 9444.371232] sr 12:0:0:1: [sr0] Add. Sense: No additional sense information
[ 9444.371239] end_request: I/O error, dev sr0, sector 196600
[ 9444.379932] sr 12:0:0:1: [sr0] Unhandled sense code
[ 9444.379940] sr 12:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 9444.379947] sr 12:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 9444.379954] sr 12:0:0:1: [sr0] Add. Sense: No additional sense information
[ 9444.379962] end_request: I/O error, dev sr0, sector 196600
[ 9444.384803] sr 12:0:0:1: [sr0] Unhandled sense code
[ 9444.384808] sr 12:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 9444.384814] sr 12:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 9444.384820] sr 12:0:0:1: [sr0] Add. Sense: No additional sense information
[ 9444.384826] end_request: I/O error, dev sr0, sector 196600
[ 9444.390434] sr 12:0:0:1: [sr0] Unhandled sense code
[ 9444.390441] sr 12:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 9444.390448] sr 12:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 9444.390455] sr 12:0:0:1: [sr0] Add. Sense: No additional sense information
[ 9444.390462] end_request: I/O error, dev sr0, sector 196600
[ 9444.395563] sr 12:0:0:1: [sr0] Unhandled sense code
[ 9444.395568] sr 12:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 9444.395573] sr 12:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 9444.395580] sr 12:0:0:1: [sr0] Add. Sense: No additional sense information
[ 9444.395586] end_request: I/O error, dev sr0, sector 196536
[ 9444.407692] sr 12:0:0:1: [sr0] Unhandled sense code
[ 9444.407700] sr 12:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 9444.407706] sr 12:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 9444.407713] sr 12:0:0:1: [sr0] Add. Sense: No additional sense information
[ 9444.407721] end_request: I/O error, dev sr0, sector 196592
[ 9444.414942] sr 12:0:0:1: [sr0] Unhandled sense code
[ 9444.414950] sr 12:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 9444.414957] sr 12:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 9444.414964] sr 12:0:0:1: [sr0] Add. Sense: No additional sense information
[ 9444.414972] end_request: I/O error, dev sr0, sector 196600
[ 9444.419683] sr 12:0:0:1: [sr0] Unhandled sense code
[ 9444.419687] sr 12:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 9444.419693] sr 12:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 9444.419699] sr 12:0:0:1: [sr0] Add. Sense: No additional sense information
[ 9444.419705] end_request: I/O error, dev sr0, sector 196600

---

### Post by spiderbatdad on 2010-02-13
lol. we seem to be getting nowhere. Try unmounting the device, then plug it in again...tail dmesg and try to find the section that begins with the device being recognized and mounted.

---

### Post by cloyd on 2010-02-13
Spiderbatdad, I don't know if I even know how to recongize that now. 

However, I can use the drive without undo trouble. It will not automount, but I can mount it using the command I mentioned earlier.  AND

I've put that command into an executable script file named "Sandisk"
and another unmount script command namned "uSandisk"  

So I can mount and unmount by simply clicking on the files, then clicking on "run in terminal" and entering my administrator's password.   Unmounting is easier. Doesn't demand the password.  

It is almost as easy as automount. Not quite, but almost.

I really appreciate the interest.

---

### Post by cloyd on 2010-02-13
Well, I tried, and here is a lot of text. It may be almost overwhelming.

[ 2066.531823] Initializing USB Mass Storage driver...
[ 2066.533715] scsi6 : SCSI emulation for USB Mass Storage devices
[ 2066.533994] usbcore: registered new interface driver usb-storage
[ 2066.534000] USB Mass Storage support registered.
[ 2066.534966] usb-storage: device found at 3
[ 2066.534970] usb-storage: waiting for device to settle before scanning
[ 2071.532192] usb-storage: device scan complete
[ 2071.532844] scsi 6:0:0:0: Direct-Access     SanDisk  SanDisk Cruzer   8.02 PQ: 0 ANSI: 0 CCS
[ 2071.533258] scsi 6:0:0:1: CD-ROM            SanDisk  SanDisk Cruzer   8.02 PQ: 0 ANSI: 0
[ 2071.533908] sd 6:0:0:0: Attached scsi generic sg1 type 0
[ 2071.555619] sr0: scsi3-mmc drive: 48x/48x tray
[ 2071.555628] Uniform CD-ROM driver Revision: 3.20
[ 2071.555826] sr 6:0:0:1: Attached scsi CD-ROM sr0
[ 2071.555931] sr 6:0:0:1: Attached scsi generic sg2 type 5
[ 2071.562402] sd 6:0:0:0: [sdb] 31301631 512-byte logical blocks: (16.0 GB/14.9 GiB)
[ 2071.567881] sd 6:0:0:0: [sdb] Write Protect is off
[ 2071.567891] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08
[ 2071.567896] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2071.575649] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2071.575659]  sdb: sdb1
[ 2071.589884] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2071.589895] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 2071.823405] sr 6:0:0:1: [sr0] Unhandled sense code
[ 2071.823413] sr 6:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 2071.823420] sr 6:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 2071.823428] sr 6:0:0:1: [sr0] Add. Sense: No additional sense information
[ 2071.823436] end_request: I/O error, dev sr0, sector 196352
[ 2071.823443] Buffer I/O error on device sr0, logical block 49088
[ 2071.823448] Buffer I/O error on device sr0, logical block 49089
[ 2071.829657] sr 6:0:0:1: [sr0] Unhandled sense code
[ 2071.829665] sr 6:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 2071.829671] sr 6:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 2071.829678] sr 6:0:0:1: [sr0] Add. Sense: No additional sense information
[ 2071.829685] end_request: I/O error, dev sr0, sector 196352
[ 2071.829694] Buffer I/O error on device sr0, logical block 49088
[ 2071.829699] Buffer I/O error on device sr0, logical block 49089
[ 2071.835535] sr 6:0:0:1: [sr0] Unhandled sense code
[ 2071.835542] sr 6:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 2071.835548] sr 6:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 2071.835555] sr 6:0:0:1: [sr0] Add. Sense: No additional sense information
[ 2071.835563] end_request: I/O error, dev sr0, sector 196584
[ 2071.835571] Buffer I/O error on device sr0, logical block 49146
[ 2071.835577] Buffer I/O error on device sr0, logical block 49147
[ 2071.916189] sr 6:0:0:1: [sr0] Unhandled sense code
[ 2071.916197] sr 6:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 2071.916204] sr 6:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 2071.916212] sr 6:0:0:1: [sr0] Add. Sense: No additional sense information
[ 2071.916220] end_request: I/O error, dev sr0, sector 196584
[ 2071.916228] Buffer I/O error on device sr0, logical block 49146
[ 2071.916234] Buffer I/O error on device sr0, logical block 49147
[ 2071.924305] sr 6:0:0:1: [sr0] Unhandled sense code
[ 2071.924313] sr 6:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 2071.924320] sr 6:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 2071.924327] sr 6:0:0:1: [sr0] Add. Sense: No additional sense information
[ 2071.924335] end_request: I/O error, dev sr0, sector 196600
[ 2071.924343] Buffer I/O error on device sr0, logical block 49150
[ 2071.936301] sr 6:0:0:1: [sr0] Unhandled sense code
[ 2071.936308] sr 6:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 2071.936315] sr 6:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 2071.936322] sr 6:0:0:1: [sr0] Add. Sense: No additional sense information
[ 2071.936330] end_request: I/O error, dev sr0, sector 196600
[ 2071.936339] Buffer I/O error on device sr0, logical block 49150
[ 2071.941125] sr 6:0:0:1: [sr0] Unhandled sense code
[ 2071.941129] sr 6:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 2071.941134] sr 6:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 2071.941141] sr 6:0:0:1: [sr0] Add. Sense: No additional sense information
[ 2071.941147] end_request: I/O error, dev sr0, sector 196600
[ 2071.945794] sr 6:0:0:1: [sr0] Unhandled sense code
[ 2071.945798] sr 6:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 2071.945804] sr 6:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 2071.945810] sr 6:0:0:1: [sr0] Add. Sense: No additional sense information
[ 2071.945816] end_request: I/O error, dev sr0, sector 196600
[ 2071.952056] sr 6:0:0:1: [sr0] Unhandled sense code
[ 2071.952063] sr 6:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 2071.952070] sr 6:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 2071.952077] sr 6:0:0:1: [sr0] Add. Sense: No additional sense information
[ 2071.952090] end_request: I/O error, dev sr0, sector 196600
[ 2071.957722] sr 6:0:0:1: [sr0] Unhandled sense code
[ 2071.957729] sr 6:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 2071.957735] sr 6:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 2071.957742] sr 6:0:0:1: [sr0] Add. Sense: No additional sense information
[ 2071.957749] end_request: I/O error, dev sr0, sector 196600
[ 2071.963554] sr 6:0:0:1: [sr0] Unhandled sense code
[ 2071.963561] sr 6:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 2071.963567] sr 6:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 2071.963574] sr 6:0:0:1: [sr0] Add. Sense: No additional sense information
[ 2071.963582] end_request: I/O error, dev sr0, sector 196600
[ 2071.970560] sr 6:0:0:1: [sr0] Unhandled sense code
[ 2071.970568] sr 6:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 2071.970574] sr 6:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 2071.970581] sr 6:0:0:1: [sr0] Add. Sense: No additional sense information
[ 2071.970589] end_request: I/O error, dev sr0, sector 196536
[ 2071.973043] UDF-fs: No VRS found
[ 2071.973050] UDF-fs: No partition found (1)
[ 2071.976951] sr 6:0:0:1: [sr0] Unhandled sense code
[ 2071.976957] sr 6:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 2071.976963] sr 6:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 2071.976970] sr 6:0:0:1: [sr0] Add. Sense: No additional sense information
[ 2071.976977] end_request: I/O error, dev sr0, sector 196592
[ 2071.981550] sr 6:0:0:1: [sr0] Unhandled sense code
[ 2071.981555] sr 6:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 2071.981560] sr 6:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 2071.981566] sr 6:0:0:1: [sr0] Add. Sense: No additional sense information
[ 2071.981573] end_request: I/O error, dev sr0, sector 196600
[ 2071.986930] sr 6:0:0:1: [sr0] Unhandled sense code
[ 2071.986938] sr 6:0:0:1: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 2071.986944] sr 6:0:0:1: [sr0] Sense Key : Hardware Error [current] 
[ 2071.986951] sr 6:0:0:1: [sr0] Add. Sense: No additional sense information
[ 2071.986959] end_request: I/O error, dev sr0, sector 196600
[ 2071.996278] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2071.996300] ISOFS: changing to secondary root


There is a partition in this flash drive.  It has some programs on it that help use the disk in Win XP.  I have noticed Ubuntu tends to interpret this partition as a CD drive . . . or so it looks to a beginner.

Again, thanks for the help. I am interested in learning "why" some drives won't autoboot, but I have figured out a reasonable workaround.

---

### Post by JKyleOKC on 2010-02-13
> **cloyd said:**
> I am interested in learning "why" some drives won't autoboot, but I have figured out a reasonable workaround.Way back there before you put together your script, you posted the line you added to fstab. One of the options it showed was "noauto" which disables auto-mounting. Try changing that to "auto" and see what happens; it should solve the problem and make the script unnecessary. However that special partition on the Cruzer may be what's bollixing things up; I delete those partitions on my flash drives since I have no need for them...

---

### Post by spiderbatdad on 2010-02-13
it usually is not necessary to have special fstab entry just to mount external storage. I do believe it is the partition you mentioned causing the issue, and it may be as simple as installing ntfs-3g from synaptic package manager. If you are satisfied with what you have via script then that's great.

---

### Post by cloyd on 2010-02-13
Tried changing the line in fstab.   It didn't make any difference as far as I could see. Maybe there is something wrong with my syntax. Linux doesn't seem to be big on screaming "syntax error!" like some other things I've tried in the past. 

Thanks for the suggestion on the partition on the Sandisk drives.  I've wondered about those. I never took them off because . . . well, I just never tried.  I guess I thought they were permanently burned in there.  They take up bout half a gig . . . that would hold a lot of music, which is one use I want to put these drives to.

Yet, I really don't think that is the problem (though I do intend to try it out), because:

I have one 1/2 gig generic "office depot" drive that used to work, but for some reason, I pulled it out of the machine without unmounting one day. It hasn't worked in the 9.10 netbook since, despite reformating. It will work in Vista, and will work in 9.04. It will work in 9.10 with the script file.

I have a old sandisk mp3 player. It will work with the script file  in 9.10, but will not automount.

I have a 100 gig seagate usb drive. It will not automount in 9.10, but will in vista and 9.04. It will mount in 9.10 with the script file.

I have a cheap 2 gig flash drive labeled "EMTC". Got it out of a bargain basket at Office Depot. Works everywhere like it is supposed to.
 
I think I like this because it keeps me wondering about something all the time, but at the same time is dependable playing my music, doing my word processing, balancing my checkbook, and surfing the net. It works like it should, but gives me something to figure out and keeps me interested.

---

### Post by cloyd on 2010-02-13
Newbie that I am, just thought about something. I am mouting  these drives.  I seem to remember that removable drives were to be mounted with pmount.  I haven't have much luck with this either. But pmount . . .  does it use fstab??

On the other hand, that long command I put in the script file, I found in the Ubuntu community documentation. And, it said, something to the effect of, if a flash drive won't automount, then use the long command.  I sure didn't put that thing together myself.  Nor am I likely to be the only one who has ever had this problem. It made it into the documentation.

---

### Post by lyall on 2010-02-14
see the following link for more info about USB
[https://help.ubuntu.com/community/USB]("https://help.ubuntu.com/community/USB")

good luck and have fun learning

---

### Post by cloyd on 2010-02-14
Thanks for the link.   At this point, my drives are functional w/o jumping thru difficult hoops. Still, I am wanting to understand . . . and maybe learn more about what devices will work with Ubuntu, or how to make them work.

It is strange.  I was making no progress. Then I figured out a little for myself, and posted what I learned. And people responded to the posts.  I do certainly appreciate it.

I just looked at at the link briefly, and noted that I found my mount command on a page linked to this one.  I've relied on  books and the forums for advice.  I like the forums, but there is a wealth of information on the community documentation that I was missing. I intend to make better use of it. Again, thanks to all.

---

### Post by cloyd on 2010-04-14
Here is an update on this . . . just read something that may have made this process easier. I see something I may do in the future. 

1st development: the cheap Office Depot drive suddenly started automounting . . . go figure!

2nd thing: the sandisk drives are U3 drives.  I saw the "U3" in Windows, but really didn't know the significance. It might have helped to post this information had I understood it's importance. I just read that there is an open source tool available to remove the partition on the drive that the machine seems to think is a cd drive. When I get time, I'll try this.  Anyway, the thread is solved, but this seemed like additional information that may help somebody else who stumbles across this thread.

---


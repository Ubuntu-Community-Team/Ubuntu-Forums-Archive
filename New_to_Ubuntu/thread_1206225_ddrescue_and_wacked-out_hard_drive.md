---
title: "ddrescue and wacked-out hard drive"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by technodestructo on 2009-07-06
Hey guys, 

I hope that this post won't be too long, but I'll try to be as thorough as possible.  If any of you have the time and patience to read through it and have any suggestions, I'd greatly appreciate it.  I'm pretty much at the end of my rope here, and this is kind of a last ditch-effort after scouring forums on this topic for the past couple of weeks. 

So I've got a 150GB WD Raptor running XP, a 150GB Velociraptor running Ubuntu (Jaunty), and a 400GB WD Caviar that I've been using as storage for all of my Windows based app files (photoshop, etc., I work as a graphic designer).  So I keep all my photography, portfolio stuff, etc. on the 400GB Caviar.  I had it partitioned into 4 separate drives, one for art, one for photo, music, and storage.    

Should have had it set up to dump to another drive just in case, but I never saw it coming when it crashed recently.  Got the "Delayed Write Fail" message in XP, and then it was just gone.  

I tried all the usual stuff, testing the SATA cables, ports, etc...  tried firing it up in Ubuntu and nothing.  So I ordered an external enclosure and tried hooking it up that way.  XP recognized all four partitions, but froze when I tried to access them.  So then I booted to Ubuntu and lo and behold, it recognized two of the four partitions.  I was able to just drag and drop copy most of the stuff from the two it was able to mount to another external, but it still doesn't want to mount the other two.

Updated the BIOS, flashed the CMOS... what else... sheesh.  

So, I ordered a new WD Caviar Black 1TB, got it all set up and formatted, and am hoping I can dump everything from the 400GB Caviar to the new 1TB using ddrescue.  And this is where I've hit a wall.

I've gone through a lot of posts online about using ddrescue and tried a few different commands and approaches, but so far I'm just getting errors when I try to get it going.  I know I've correctly identified the drives by their "sda, sdb..." signatures using fdisk, but when I try to run ddrescue and write the image from one to the other I get errors such as "not a directory", etc. 

There has to be something I'm missing here, right?  The drive can't be totally FUBAR if it's recognized on the external, so there's gotta be some data on there that I can image with ddrescue.  I can't help but think I'm just doing something wrong.  Do I need to partition the TB drive so it has somewhere more specific to drop the image of each of the 4 partitions from the 400GB, or is there just some command I'm missing?  

Thanks in advance to anyone who can offer any help.  I'll be happy to post any outputs you may need or provide any other info that will make this easier.  I really don't want to reformat this drive and start over until I'm sure there's nothing else that can be done to save it, and I can't feel that way until I actually get ddrescue going and see what it can do.  

Thank you all, again.  I will respond to any follow up questions ASAP.

---

### Post by DGortze380 on 2009-07-06
Since you have plenty of space, the FIRST thing I'd do is make a bit-wise copy of the drive you hope to salvage. 

dd can do this for you.

EDIT: for syntax
```

sudo dd if=/dev/sda of=/mount/myExternal/image.dd

```

replace sda with the correct id of the drive you want to image, /mount/myExternal should be the mount point of your new 1TB storage drive.

---

### Post by glennric on 2009-07-06
There are also some partition and file system recovery programs you could try.  gpart and sleuthkit are two that I have used.  gpart is probably the easiest (for a cli program).  Just run
```
sudo gpart /dev/sda
```
and it will scan the drive /dev/sda and try to guess its partitions.  Then it will prompt you to write the guessed partition table if you want it to.

It would probably be a good idea to do the dd backup that DGortze380 suggested first just in case this doesn't work.

---

### Post by technodestructo on 2009-07-06
Sweet!  Thanks so much, guys.  I'm amazed at the quickness of the replies.  This site, and everyone on it, is awesome.  

I'll give both of those suggestions a try and post back with an update.

Thanks again!!!

---

### Post by technodestructo on 2009-07-07
hmm...  seems like I'm on the right track, but still getting an error.  Here's the output of fdisk -l, and below that is what I was entering in with dd.  Am I off the mark, here?  

Thanks again, guys.

_______________________________________________________________________

stuart@obelinux:~$ sudo fdisk -l

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55b755b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18240   146512768+   7  HPFS/NTFS

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e05ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8693    69826491   83  Linux
/dev/sdb2            8694       18241    76694310    5  Extended
/dev/sdb5           17496       18241     5992213+  82  Linux swap / Solaris
/dev/sdb6            8694       17130    67770139+  83  Linux
/dev/sdb7           17131       17495     2931831   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x023220fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdd: 30.0 GB, 30005821440 bytes
255 heads, 62 sectors/track, 3706 cylinders
Units = cylinders of 15810 * 512 = 8094720 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1          11       80293+   0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sdd2              11        3707    29222234+   b  W95 FAT32

Disk /dev/sde: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12c5c273

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       12560   100888168+   7  HPFS/NTFS
/dev/sde2           12561       48641   289820632+   f  W95 Ext'd (LBA)
/dev/sde5           12561       24418    95249353+   7  HPFS/NTFS
/dev/sde6           24419       36131    94084641    7  HPFS/NTFS
/dev/sde7           36132       48641   100486543+   7  HPFS/NTFS
stuart@obelinux:~$ sudo dd /dev/sde /mount/dev/sdc/image.dd
dd: unrecognized operand `/dev/sde'
Try `dd --help' for more information.
stuart@obelinux:~$ sudo dd /dev/sde2 /mount/dev/sdc1/image.dd
dd: unrecognized operand `/dev/sde2'
Try `dd --help' for more information.
stuart@obelinux:~$ sudo dd /dev/sde1 /mount/sdc1/image.dd
dd: unrecognized operand `/dev/sde1'
Try `dd --help' for more information.

---

### Post by glennric on 2009-07-07
Sorry, I didn't look at DGortze380's dd command closely.  He doesn't quite have the syntax correct.  It should be
```
dd if=/dev/sda1 of=/mount/dev/sdc/image.dd
```

---

### Post by DGortze380 on 2009-07-07
> **glennric said:**
> Sorry, I didn't look at DGortze380's dd command closely.  He doesn't quite have the syntax correct.  It should be
```
dd if=/dev/sda1 of=/mount/dev/sdc/image.dd
```

Sorry about that typo, you need to specif if= (in file is ...) and of= (out file is ...).

use just /dev/sde to copy the whole drive, including partition informations. /dev/sde1 would only copy the first partition and is not what you want.

And while I'm at it ... image.dd is simply a file name, call it whatever you like. .dd is an extension commonly used in forensics for this type of image, but shouldn't matter much in this case.

---

### Post by niteshifter on 2009-07-07
Hi,

I will now predict your future: dd will not work for you :)

dd will die at the first I/O error. You really want ddrescue - the GNU version in the repositories (gddrescue is the package name). The package ddrescue is the Debian version, dd_rescue.

Both versions will not stop on I/O error(s). Both will try hard to get sectors. The GNU version works well with RAW I/O setup. The Debian version does not.

I've used both, and prefer the GNU version. It's more aggressive at retrieval of data.

You do not want to do the entire device, that is, NOT /dev/sde. Do only those bad partitions. Put the log file(s) on a good drive.

The man page for ddrescue is terse. The complete manual is in the info file:
```
info ddrescue
```
Also,
```
man raw
```

Some hints:

Run ddrescue with the -v (verbose) option and watch the output. When accessing the partition normally gives no new recovered sectors, setup RAW I/O and run it again.

Try the freezer trick - put the drive in the fridge for a couple of hours. Helps with failing internal electronics issues.

Be patient. This is going to take hours, many of them.

---

### Post by Grenage on 2009-07-07
I would recommend against any partition or data editing; those you can mess around with that afterwards.

First off, plug in both of the drives (the defective and the new), then run:

ddrescue /dev/hda /dev/hdb

Replacing hda and hdb for your actual source and destination drives.  It's going to take a **long** time, but bear with it.  Once you have that copy, you can try getting the data off it.  Don't mess around with your existing drive until you have that copy.

P.S: For the record:

> put the drive in the fridge for a couple of hours. Helps with failing internal electronics issues

This is not true.  It 'can' free a stuck arm or head (mechanical components), but it will do nothing for the electronics.  People also generally use a frost-free freezer with the drive in a bag, fridges don't get cold enough to do anything.

---

### Post by unutbu on 2009-07-07
The gddrescue package provides /sbin/ddrescue.
The ddrescue package provides /bin/dd_rescue.

ddrescue and dd_rescue are different programs, which do similar things. That gddrescue provides a program with the same name as an unrelated package makes for some confusion. 

Here is some good information on using gddrescue: [http://www.forensicswiki.org/wiki/Ddrescue](http://www.forensicswiki.org/wiki/Ddrescue)

The wiki also shows how to use the --direct flag so you don't have to use the raw command manually.

---

### Post by niteshifter on 2009-07-07
> **Grenage said:**
> 

P.S: For the record:



This is not true.  It 'can' free a stuck arm or head (mechanical components), but it will do nothing for the electronics.  People also generally use a frost-free freezer with the drive in a bag, fridges don't get cold enough to do anything.

It is true for drives that are failing due to heat: They start fine, run fine then start giving errors after some period of time. You can leave it in the fridge while recovering - it's just providing extra cooling. Or take it out. Or use the freezer part of the fridge - it really doesn't matter which:

Fridge temp =  around 4C
Freezer temp = around -6C
"Shirt sleeve" temp = around 23C
Operating temp = 35C and higher.

That 'extra' -10C of a freezer for the coefficients of expansion of the various metals isn't going to matter as much as the -19C drop from 'shirt sleeve' environment temperatures will - and once it breaks free and is keep moving by the controller it tends to stay free until a period of rest occurs.

It's a general solution to what really is an unknown problem. People assume mechanical failure (and it frequently is) but the only way to know is disassemble the drive.

I've done the fridge trick many times over the years, it works. I've also used the freezer, it works. Essentially no difference between the two.

Were I work, we've access to LN2 (liquid nitrogen) - that doesn't work, -190C seems a bit too much :) as there's no drive there until it warms up to a bit below freezer / fridge temperatures.

By the way use ddresuce (GNU) like this (in Ubuntu):

```
sudo ddresuce /dev/<fail-drive> /dev/<good-drive> **/good-drive-path/logfile**

```
The valuable thing is that logfile. It is used on successive passes to go directly to the failed portions, saving time. It is just human readable text and also yields useful information: as the block size on most ext2/3 (and NTFS) file systems is 4k bytes if you're seeing "holes" reported as 0x1000 - you're missing entire blocks (courtesy of the kernel and file system interface), switch to RAW I/O and those holes should shrink to 0x0200 (512 bytes, a sector's worth).

---

### Post by technodestructo on 2009-07-07
Okay, now we're cookin'!  Grenage, your syntax worked... ddrescue is now running, and, it appears to be attempting to copy all of the 400GB to the 1TB.  Fingers crossed!

Many, many thanks - and to the rest of you for all of your help, as well.  I'm going to let this do its thing, and I'll post an update when it's done.  I uh... might ask for help when it comes time to fsck...  :>D   

Thanks again, everyone.

---

### Post by Grenage on 2009-07-08
Hi **technodestructo**, glad to hear that it's churning away.  The duration of the imaging depends on the errors; there are ways to check on the % done, but hey, it's not like you aren't going to wait anyhow.

**niteshifter**: Ah I see what you mean; I assumed you were going down the angle of mechanical issues, as I haven't used a fridge/freezer simply to cool a unit down when there is excessive heat.  Cheers for the elaboration!

---

### Post by kung fu buntu on 2009-08-17
[COLOR="Red"]**background:**[/COLOR]

My HDD is (almost?) dead.
I think the heat got it :(
I have 2 partitions and both of them are non-mountable.

I think it helped turning of the computer for a while, since the HDD gave signs of live again.
But it was a mistake using fsck! Very weird errors started poping out.

Right now even though it's not mounted, it's doing this "tchk tchk" noise, every 2 seconds or so. Well... I think it's the dying HDD, but I have a total of 3 HDDs on this computer.



[COLOR="#ff0000"]**real question:**[/COLOR]

I'm thinking on the freeze/fridge approach... but I'm fearfull of condensation.
Even using the ziplock bag... isn't there the risk of condensation?
I mean, the HDD is vacuum inside or is there air? If so, there is water vapor in air, which can condensate.

Also, it's **not** possible for me to have the HDD inside the fridge/freezer while gddrescue works on it.

I've heard of people [leaving the HDD in the freezer for a whole day in order to gain 20m of working status]("http://geeksaresexy.blogspot.com/2006/01/freeze-your-hard-drive-to-recover-data.html").

Can I leave it in the fridge for 1 or 2 hours without risk of condensation?
Would it be better to put some ice on a plastic bag and put it over the HDD while gddrescue works?

What if the ziplock bag has a small hole... air would pass by... so it's useless, right?

EDIT: I just reminded on the possibility of using a water bag!
I would put very cold water and ice cubes in it and press it against the HDD while gddrescue backups the drive.

I'm thinking on:
run gddrescue
put drive in fridge wrapped in paper towels inside a platic bag for 1 hour or so
run gddrescue again


Any comments on all this?

---

### Post by niteshifter on 2009-08-20
Hi,

@kung fu buntu: HDD aren't vacuumed, they vent through a micro-pore filter that's usually moisture repellent.

If you're worried about condensation after chilling the drive (justifiably) then place the drive with cable(s) attached in a ziplock bag (no paper towels needed) and seal around the cable(s) with package tape.

---

### Post by Go_Big_Blue on 2009-08-23
Hey guys.  Just read through the thread, and I have attempted to use the GNU ddrescue.  But I am a bit concerned.

Here is the scenario:
I dropped my laptop off of my lap while sitting in a chair.  It fell about 12 inches (~24cm), but kept running.  Then about 15 minutes later it locked up on me.  So, following the advice of a friend, I downloaded Ubuntu-Rescue-Remix 9.04 and burned a live CD.  I took the old 320GB HDD out of the laptop and put it and a new 500GB HDD and put them in my desktop and ran the liveCD.  I started ddrescue 2 days ago, and it appears that it is still working.  However, I was wondering how long it can take?

I had ~150GB of data on the old HDD.  The command line that I used was
```

sudo ddrescue -r 3 -C /dev/sda /dev/sdb logfile

```

Again, I started this 48 hours ago (Friday night 8/21/09).  Right now, the screen keeps scrolling several messages that goes something like this:

```

rescued:  320038 MB, errsize:  34389 kB, current rate:  0B/s
   ipos:   32581 MB,  errors:    667,   average rate:  2146 kB/s
   opos:   32581 MBer  I/O Error on device sda, logical block 7954625
Splitting error areas...
[1615188.100553] ata2.00: status: {DRDY ERR}
[1615188.100553] ata2.00: status: {ABRT} 
...
...
...
(it repeats the above two lines a few times and then goes back to the "rescued: ...)
```


Now, it does seem to be making progress, but I'm not sure how much longer it has to go, and I really need to get a feel for where it is at in this whole process and how much longer it could take.

---

### Post by kung fu buntu on 2009-08-25
> **niteshifter said:**
> Hi,

@kung fu buntu: HDD aren't vacuumed, they vent through a micro-pore filter that's usually moisture repellent.

If you're worried about condensation after chilling the drive (justifiably) then place the drive with cable(s) attached in a ziplock bag (no paper towels needed) and seal around the cable(s) with package tape.

I was able to recover all my data, without having to resort to the fridge/freezer.
However, for posteriority, I would like to understand what you mean.
You are saying to plug the sata and power cables to the drive and leave their other end (the one not plugged) outside the bag?
I would like to understand how does that prevent condensation?
Does air goes through the cables and also cools the drive inside?
Where is that micro-pore? Couldn't we just duct tape it for a while?



@ Go_Big_Blue
You really need to read the manual to better understand things.
**info ddrescue**

I also got those
ata2.00: status: {DRDY ERR}
ata2.00: status: {ABRT} 
errors when I tried to fsck the drive, but not when using gddrescue.

It already says on the message what is the current status:
> rescued:  320038 MB, errsize:  34389 kB

If you're stuck at these 34MB, what you could try -- and I did it several times -- stop it for the day. Then the next day leave an air fan pointing to the drive for 30m or 1h, and then immediatly plug it in your computer, turn it on, and continue ddrescue.

---

### Post by eklem on 2009-09-14
> **unutbu said:**
> 
Here is some good information on using gddrescue: [http://www.forensicswiki.org/wiki/Ddrescue](http://www.forensicswiki.org/wiki/Ddrescue)

The wiki also shows how to use the --direct flag so you don't have to use the raw command manually.

Thanks Unutbu!
That link just saved me a whole lot of trouble. Got most of the content from a WinXP 250 GB disk that had crashed.

---

### Post by unutbu on 2009-09-14
That's great news, eklem! I'm glad to know it worked for you.

---


---
title: "Need help!!! Install Ubuntu-only to Dell hard disk (prev. Dual boot w/ Xubuntu &amp; XP)"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by NUboon2Age on 2010-05-24
I (a newbie) need some expert advice here.  **I think I need some kind of really low level special utility **that will do whatever is required to make a Dell hard disk (originally XP and has those crazy Dell recovery partitions on it which are maybe part of the problem -- and later dual boot with Xubuntu) completely available to be _just_ an Ubuntu disk.  **I don't want to rescue anything from the disk, I just want to be able to use the disk soley for my new Ubuntu install.**

**I started to do an install of Lucid Lynx from CD, told it to use the whole disk** (which is exactly what I want) and it got errors so I stopped it.  After having tried various things i'm in a fix :confused:, but i don't think the situation is completely irretrievable -- just very tough to retrieve :(.  I'm getting read/write errors in various utilities, including TestDisk, gparted, parted, and others but TestDisk can still see the previous partition table and the files that are there and sfdisk was able to do some of its operations successfully.

Right now I'm booted up with the SystemRescueCD.  If I have confidence that a different LiveCD or utility than what is on this disk I have a few resources for alternatives (like burning a different livedisk), but it will be difficult and quite time consuming so I want to see if what I need is available on this disk *or that people have lots o confidence in a tool before I go down an alternative route.*

```

% sfdisk -l /dev/sda 

disk /dev/sda: 4864 cylinders, 255 heads, 63 sectors/track
read: Input/output error

sfdisk: read error on /dev/sda - cannot read sector 0
 /dev/sda: unrecognized partition table type

```

Please let me know what further info I need to provide you in order to clarify the situation.  I've attached the Boot Info Script.

---

### Post by NUboon2Age on 2010-05-24
Trying to add Boot Info Script attachment again

---

### Post by sandyd on 2010-05-24
> **NUboon2Age said:**
> I (a newbie) need some expert advice here.  **I think I need some kind of really low level special utility **that will do whatever is required to make a Dell hard disk (originally XP and has those crazy Dell recovery partitions on it which are maybe part of the problem -- and later dual boot with Xubuntu) completely available to be _just_ an Ubuntu disk.  **I don't want to rescue anything from the disk, I just want to be able to use the disk soley for my new Ubuntu install.**

**I started to do an install of Lucid Lynx from CD, told it to use the whole disk** (which is exactly what I want) and it got errors so I stopped it.  After having tried various things i'm in a fix :confused:, but i don't think the situation is completely irretrievable -- just very tough to retrieve :(.  I'm getting read/write errors in various utilities, including TestDisk, gparted, parted, and others but TestDisk can still see the previous partition table and the files that are there and sfdisk was able to do some of its operations successfully.

Right now I'm booted up with the SystemRescueCD.  If I have confidence that a different LiveCD or utility than what is on this disk I have a few resources for alternatives (like burning a different livedisk), but it will be difficult and quite time consuming so I want to see if what I need is available on this disk or that people have lots o confidence in a tool before I go down an alternative route.

```

% sfdisk -l /dev/sda 

disk /dev/sda: 4864 cylinders, 255 heads, 63 sectors/track
read: Input/output error

sfdisk: read error on /dev/sda - cannot read sector 0
 /dev/sda: unrecognized partition table type

```Please let me know what further info I need to provide you in order to clarify the situation.  I've attached the Boot Info Script.
Go to System -> Administration -> Gparted
Click on "devices" and choose "create partition table"

then try again.

---

### Post by NUboon2Age on 2010-05-24
Gparted says "No devices detected" and the devices button is grayed out. Clicking on "Refresh devices" still gives "No devices detected"

---

### Post by nhasian on 2010-05-24
> **NUboon2Age said:**
> **I think I need some kind of really low level special utility **....
**I started to do an install of Lucid Lynx from CD, told it to use the whole disk** (which is exactly what I want) and it got errors so I stopped it.

get the latest ubuntu 10.04 (32 bit or 64 bit whichever is appropriate for your system) and either make a bootable usb-thumbdrive for it or burn it to a CD (NOT DVD) at the slowest speed possible for your optical drive and media.

Boot from the ubuntu live CD/USB.  once you reach the ubuntu desktop go to System-> Administration-> Disk Utility and see if your hard disk is healthy or if it has bad sectors, fails the SMART test, etc.  if all is well,

go to System-> Administration-> Gparted (Partition Editor) and delete all the Windows and Dell system restore partitions.  Now you can either create your root, home and swap partitions yourself, or simply double click on the ubuntu installer icon on the desktop to continue installation.

---

### Post by NUboon2Age on 2010-05-24
> **nhasian said:**
> get the latest ubuntu 10.04 (32 bit or 64 bit whichever is appropriate for your system) and either make a bootable usb-thumbdrive for it or burn it to a CD (NOT DVD) at the slowest speed possible for your optical drive and media.

Boot from the ubuntu live CD/USB.  once you reach the ubuntu desktop go to System-> Administration-> Disk Utility and see if your hard disk is healthy or if it has bad sectors, fails the SMART test, etc.  if all is well,

Okay, I didn't know about that utility (see how new I am to ubuntu!) Do you know what the name of the program is to run from the command line (-- maybe I have it on the SystemRescueCD and don't know it)?

> **nhasian said:**
> 
go to System-> Administration-> Gparted (Partition Editor) and delete all the Windows and Dell system restore partitions.  Now you can either create your root, home and swap partitions yourself, or simply double click on the ubuntu installer icon on the desktop to continue installation.  

Well unless I have some corrective action i can take with the above or some other utility, Gparted will just continue to act as I posted above and won't allow me to delete the previous partitions because it can't read the old partition table apparently.

---

### Post by nhasian on 2010-05-24
the name of the application is palimpsest.  you can start it from the ubuntu live cd with the terminal command:

```
sudo palimpsest
```

> **NUboon2Age said:**
> Okay, I didn't know about that utility (see how new I am to ubuntu!) Do you know what the name of the program is to run from the command line

---

### Post by NUboon2Age on 2010-05-24
gdisk verify reports:

> 
No problems found. 78140093 free sectors (37.3 GiB) available in 1
segments, the largest of which is 78140093 (37.3 GiB) in size.


---

### Post by srs5694 on 2010-05-24
> **NUboon2Age said:**
> Okay, I didn't know about that utility (see how new I am to ubuntu!) Do you know what the name of the program is to run from the command line (-- maybe I have it on the SystemRescueCD and don't know it)?

In addition to palimpsest, you could try typing smartctl (text-mode) or gsmartcontrol (GUI). Both provide access to SMART data, which should reveal whether the drive has hardware problems.

---

### Post by NUboon2Age on 2010-05-24
> **nhasian said:**
> the name of the application is palimpsest.  you can start it from the ubuntu live cd with the terminal command:

```
sudo palimpsest
```

Darn, palimpsest doesn't seem to be on the SystemRescueCD. :(

---

### Post by srs5694 on 2010-05-24
> **NUboon2Age said:**
> gdisk verify reports:

These aren't very informative, at least not about hardware problems. That just tells you about serious partition table problems, such as overlapping partitions. Also, gdisk is a tool for handling GUID Partition Table (GPT) disks, but your disk is almost certain a Master Boot Record (MBR) disk. Although gdisk does a non-destructive MBR-to-GPT conversion, some types of MBR errors will be ignored by gdisk's 'v' option because they become non-issues after the conversion.

---

### Post by NUboon2Age on 2010-05-24
> **srs5694 said:**
> In addition to palimpsest, you could try typing smartctl (text-mode) or gsmartcontrol (GUI). Both provide access to SMART data, which should reveal whether the drive has hardware problems.

Thank you! smartctl is there (trying to figure out how to use it), but gsmartcontrol isn't.

---

### Post by warfacegod on 2010-05-24
> **srs5694 said:**
> In addition to palimpsest, you could try typing smartctl (text-mode) or gsmartcontrol (GUI). Both provide access to SMART data, which should reveal whether the drive has hardware problems.

An excellent tool, recommend it often. It needs to be installed though, it doesn't come installed by default.

```
sudo apt-get install gsmartcontrol
```

---

### Post by NUboon2Age on 2010-05-24
> **srs5694 said:**
> These aren't very informative, at least not about hardware problems. That just tells you about serious partition table problems, such as overlapping partitions. Also, gdisk is a tool for handling GUID Partition Table (GPT) disks, but your disk is almost certain a Master Boot Record (MBR) disk. Although gdisk does a non-destructive MBR-to-GPT conversion, some types of MBR errors will be ignored by gdisk's 'v' option because they become non-issues after the conversion.

Is gdisk a reasonable way to side-step these problems and get the disk workable?

---

### Post by NUboon2Age on 2010-05-24
> **srs5694 said:**
> In addition to palimpsest, you could try typing smartctl (text-mode) or gsmartcontrol (GUI). Both provide access to SMART data, which should reveal whether the drive has hardware problems.

Okay, this is what I'm getting so far.  I only have smartctl (not gsmartcontrol) on this (gentoo-based and therefore unfamiliar w/ how to update) SystemRescueCD -- all I doing it right?

```

smartctl --all --tolerance=verypermissive /dev/sda
smartctl version 5.38 [i486-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Short INQUIRY response, skip product id
SMART Health Status: OK
Read defect list: asked for grown list but didn't get it

Error Counter logging not supported
Device does not support Self Test logging

```


Here's the smartctl help info:

```
smartctl -h                     
smartctl version 5.38 [i486-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Usage: smartctl [options] device

============================================ SHOW INFORMATION OPTIONS =====

  -h, --help, --usage
         Display this help and exit

  -V, --version, --copyright, --license
         Print license, copyright, and version information and exit

  -i, --info                                                       
         Show identity information for device

  -a, --all                                                        
         Show all SMART information for device

================================== SMARTCTL RUN-TIME BEHAVIOR OPTIONS =====

  -q TYPE, --quietmode=TYPE                                           (ATA)
         Set smartctl quiet mode to one of: errorsonly, silent, noserial

  -d TYPE, --device=TYPE
         Specify device type to one of: ata, scsi, marvell, sat, 3ware,N

  -T TYPE, --tolerance=TYPE                                           (ATA)
         Tolerance: normal, conservative, permissive, verypermissive

  -b TYPE, --badsum=TYPE                                              (ATA)
         Set action on bad checksum to one of: warn, exit, ignore

  -r TYPE, --report=TYPE
         Report transactions (see man page)

  -n MODE, --nocheck=MODE                                             (ATA)
         No check if: never, sleep, standby, idle (see man page)

============================== DEVICE FEATURE ENABLE/DISABLE COMMANDS =====

  -s VALUE, --smart=VALUE
        Enable/disable SMART on device (on/off)

  -o VALUE, --offlineauto=VALUE                                       (ATA)
        Enable/disable automatic offline testing on device (on/off)

  -S VALUE, --saveauto=VALUE                                          (ATA)
        Enable/disable Attribute autosave on device (on/off)

======================================= READ AND DISPLAY DATA OPTIONS =====

  -H, --health
        Show device SMART health status

  -c, --capabilities                                                  (ATA)
        Show device SMART capabilities

  -A, --attributes                                                         
        Show device SMART vendor-specific Attributes and values

  -l TYPE, --log=TYPE
        Show device log. TYPE: error, selftest, selective, directory,
                               background, scttemp[sts,hist]

  -v N,OPTION , --vendorattribute=N,OPTION                            (ATA)
        Set display OPTION for vendor Attribute N (see man page)

  -F TYPE, --firmwarebug=TYPE                                         (ATA)
        Use firmware bug workaround: none, samsung, samsung2,
                                     samsung3, swapid

  -P TYPE, --presets=TYPE                                             (ATA)
        Drive-specific presets: use, ignore, show, showall

============================================ DEVICE SELF-TEST OPTIONS =====

  -t TEST, --test=TEST
        Run test. TEST: offline short long conveyance select,M-N
                        pending,N afterselect,[on|off] scttempint,N[,p]

  -C, --captive
        Do test in captive mode (along with -t)

  -X, --abort
        Abort any non-captive test on device

=================================================== SMARTCTL EXAMPLES =====

  smartctl --all /dev/hda                    (Prints all SMART information)

  smartctl --smart=on --offlineauto=on --saveauto=on /dev/hda
                                              (Enables SMART on first disk)

  smartctl --test=long /dev/hda          (Executes extended disk self-test)

  smartctl --attributes --log=selftest --quietmode=errorsonly /dev/hda
                                      (Prints Self-Test & Attribute errors)
  smartctl --all --device=3ware,2 /dev/sda
  smartctl --all --device=3ware,2 /dev/twe0
  smartctl --all --device=3ware,2 /dev/twa0
          (Prints all SMART info for 3rd ATA disk on 3ware RAID controller)
  smartctl --all --device=hpt,1/1/3 /dev/sda
          (Prints all SMART info for the SATA disk attached to the 3rd PMPort
           of the 1st channel on the 1st HighPoint RAID controller)

```

---

### Post by NUboon2Age on 2010-05-24
> **NUboon2Age said:**
> Is gdisk a reasonable way to side-step these problems and get the disk workable?

Gdisk command menu:

```

Command (? for help): ?
b	back up GPT data to a file
c	change a partition's name
d	delete a partition
i	show detailed information on a partition
l	list known partition types
n	add a new partition
o	create a new empty GUID partition table (GPT)
p	print the partition table
q	quit without saving changes
r	recovery and transformation options (experts only)
s	sort partitions
t	change a partition's type code
v	verify disk
w	write table to disk and exit
x	extra functionality (experts only)
?	print this menu

Command (? for help): v
No problems found. 78140093 free sectors (37.3 GiB) available in 1
segments, the largest of which is 78140093 (37.3 GiB) in size.

Command (? for help):
```

And then if you go to "r" -- Recovery/transformation -- you get:

```

Recovery/transformation command (? for help): ?
b	use backup GPT header (rebuilding main)
c	load backup partition table from disk (rebuilding main)
d	use main GPT header (rebuilding backup)
e	load main partition table from disk (rebuilding backup)
f	load MBR and build fresh GPT from it
g	convert GPT into MBR and exit
h	make hybrid MBR
i	show detailed information on a partition
l	load partition data from a backup file
m	return to main menu
o	print protective MBR data
p	print the partition table
q	quit without saving changes
t	transform BSD disklabel partition
v	verify disk
w	write table to disk and exit
x	extra functionality (experts only)
?	print this menu

Recovery/transformation command (? for help): 

```

or "x" for Expert commands:

```

Expert command (? for help): ?
a	set attributes
c	change partition GUID
d	display the sector alignment value
e	relocate backup data structures to the end of the disk
g	change disk GUID
i	show detailed information on a partition
l	set the sector alignment value
m	return to main menu
n	create a new protective MBR
o	print protective MBR data
p	print the partition table
q	quit without saving changes
r	recovery and transformation options (experts only)
s	resize partition table
t	transpose two partition table entries
v	verify disk
w	write table to disk and exit
z	zap (destroy) GPT data structures and exit
?	print this menu

Expert command (? for help): 

```

---

### Post by NUboon2Age on 2010-05-24
When trying to create a partition table and then use gdisk w (write) it gave:

```
Warning! An error  was reported when writing the partition table! 
```

And then when I restarted
```

root@sysresccd /bin % gdisk
GPT fdisk (gdisk) version 0.6.7

Type device filename, or press <Enter> to exit: /dev/sda
Warning! Read error 5; strange behavior now likely!
Warning! Read error 5; strange behavior now likely!
Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.

Command (? for help): i
No partitions

```

So unless there's some other combo of gdisk commands that I'm overlooking...

---

### Post by Perkins on 2010-05-24
One thing I have had luck with in the past (assuming you truly want to just wipe *everything* out and start from scratch) is to just run badblocks on the entire device in read-write mode.  (Exemplia gratia: badblocks -s -w /dev/sda  (Substitute proper device handle for sda))This does two things:

a) writes and reads every sector of the disk, so you can be sure it's still good.
b) completely obliterates every last scrap of information from the disk beyond the possibility of all but the most advanced forensic methods to recover.

If you're having hardware failure problems, odds are this will reveal that fact.  If you're having issues with corrupted partition tables that are confusing the utilities you are trying to use, this will wipe them out entirely and let you start over.

If there is *any* data you wish to save, copy it off before doing this however.  Unless you're willing to spend twenty grand or so to get it back.

---

### Post by NUboon2Age on 2010-05-25
> **Perkins said:**
> One thing I have had luck with in the past (assuming you truly want to just wipe *everything* out and start from scratch) is to just run badblocks on the entire device in read-write mode.  (Exemplia gratia: badblocks -s -w /dev/sda  (Substitute proper device handle for sda))This does two things:

a) writes and reads every sector of the disk, so you can be sure it's still good.
b) completely obliterates every last scrap of information from the disk beyond the possibility of all but the most advanced forensic methods to recover.

If you're having hardware failure problems, odds are this will reveal that fact.  If you're having issues with corrupted partition tables that are confusing the utilities you are trying to use, this will wipe them out entirely and let you start over.

If there is *any* data you wish to save, copy it off before doing this however.  Unless you're willing to spend twenty grand or so to get it back.

Yes, I think it might be the corrupted partition tables kinda problem and since I don't care about anything on the disk that is an option.  I guess 'wipe' would be similar?

Okay, I started it:```

badblocks -s -w /dev/sda 
```
Let's see what happens. (saying prayer)

---

### Post by nhasian on 2010-05-25
I think its about time you started that Ubuntu liveCD iso download...

---

### Post by NUboon2Age on 2010-05-25
So far it seems to be doing its thing.  Block numbers are flying by on the terminal as it goes through the disk.  So if it succeeds, what is my next step?

---

### Post by warfacegod on 2010-05-25
> **NUboon2Age said:**
> So far it seems to be doing its thing.  Block numbers are flying by on the terminal as it goes through the disk.  So if it succeeds, what is my next step?

See post #20

---

### Post by Perkins on 2010-05-25
Wipe is similar, except it doesn't necessarily spit out a nifty list of bad sectors.

If it succeeds without listing off a bunch of bad spots, then you should be able to just pop in an Ubuntu install CD and go.  Last time I tried it the installer was more than capable of formatting a completely empty disk from scratch.

---

### Post by NUboon2Age on 2010-05-25
> **nhasian said:**
> I think its about time you started that Ubuntu liveCD iso download...

Well I had a live Lucid Lynx disc on hand.  Before I started the badblocks operation (which btw currently says its Reading and Comparing with different test patterns, 11 hours in), I tried to boot off the disk, but it was soooooo slow (something related to this disk was slowing it down) it came to a point where I wasn't sure if it was hung or not, so I rebooted with a USB PeppermintOS pendrive, and while it was extremely slow (like an hour) it finally booted and that's how I got back onto the forum here and got the advice about badblocks.  I don't know if it would boot to the CD now or not.  But now that I'm booted in an Ubuntu-based OS, what would the next step be after this finishes?

---

### Post by NUboon2Age on 2010-05-25
> **Perkins said:**
> Wipe is similar, except it doesn't necessarily spit out a nifty list of bad sectors.

If it succeeds without listing off a bunch of bad spots, then you should be able to just pop in an Ubuntu install CD and go.  Last time I tried it the installer was more than capable of formatting a completely empty disk from scratch.

Still running badblocks...
So far after listing all the block numbers it was working on it said:

```

{...}
214865% done, 4:13:57 elapsed
21487
21488
214896% done, 4:13:58 elapsed
21490
21491
214926% done, 4:13:59 elapsed
21493
214946% done, 4:14:00 elapsed
21495
21496
214976% done, 4:14:01 elapsed
21498
21499
215006% done, 4:14:02 elapsed
21501
21502
215036% done, 4:14:03 elapsed
done                                
Testing with pattern 0x55: done                                
Reading and comparing: done                                
Testing with pattern 0xff: done                                
Reading and comparing: done                                
Testing with pattern 0x00: 13.06% done, 11:05:24 elapsed

```

So how much longer should I expect this to go for?

---

### Post by nhasian on 2010-05-25
yeah i have to admit when i installed ubuntu 10.04 on my new htpc (which has an intel i930 CPU, 6 gigs ram, and an nvidia GPU) it took **20 mins** for it to finally reach the desktop.  It may look like it is hanging but let it sit for a while.  I dont know what its doing, but eventually it will continue.  That doesn't happen with previous releases of ubuntu so i'm guessing it has something to do with all the tweaks they did to make ubuntu boot faster.

---

### Post by NUboon2Age on 2010-05-25
> **NUboon2Age said:**
> Still running badblocks...
So far after listing all the block numbers it was working on it said:

```

{...}
21501
21502
215036% done, 4:14:03 elapsed
done                                
Testing with pattern 0x55: done                                
Reading and comparing: done                                
Testing with pattern 0xff: done                                
Reading and comparing: done                                
Testing with pattern 0x00: 13.06% done, 11:05:24 elapsed

```

So how much longer should I expect this to go for?

I see the man page says:
> 
-w
    Use write-mode test. With this option, badblocks scans for bad blocks by writing some patterns (0xaa, 0x55, 0xff, 0x00) on every block of the device, reading every block and comparing the contents. 


So maybe that means it'll be done after testing w/ pattern 0xaa???

---

### Post by NUboon2Age on 2010-05-25
How can I tell how many blocks a hard drive has?

---

### Post by NUboon2Age on 2010-05-25
> **NUboon2Age said:**
> I see the man page says:


So maybe that means it'll be done after testing w/ pattern 0xaa???

```

{...}
215036% done, 4:14:03 elapsed
done                                
Testing with pattern 0x55: done                                
Reading and comparing: done                                
Testing with pattern 0xff: done                                
Reading and comparing: done                                
Testing with pattern 0x00: done                                
Reading and comparing: done 
$
```

Well it didn't go to 0xaa but it just stopped (some 13+ hours) for 40G drive.  Okay, I'll start checking it out.

---

### Post by NUboon2Age on 2010-05-25
> **NUboon2Age said:**
> ```

{...}
215036% done, 4:14:03 elapsed
done                                
Testing with pattern 0x55: done                                
Reading and comparing: done                                
Testing with pattern 0xff: done                                
Reading and comparing: done                                
Testing with pattern 0x00: done                                
Reading and comparing: done 
$
```

Well it didn't go to 0xaa but it just stopped (some 13+ hours) for 40G drive.  Okay, I'll start checking it out.

Hmmm... well I haven't rebooted yet, so I'm not sure if I should expect any difference, but I tried the Peppermint installer  and it didn't see the disk.gparted and "Disk Utility" don't see it.  I restarted gparted as gparted /dev/sda and it sort of saw it ("unallocated" 37.26 GiB), but when I tried to create a partition table to it had "error while creating partition table".  Let's see... what else might I try before trying to reboot to the Lucid Lynx installer?

---

### Post by SRST Technologies on 2010-05-25
The answer to this problem was clear back on the first page, everyone.  If you don't understand the output of programs, don't disregard the output, find out what it means.  And for the love of god, stop giving advice on here if you don't know what you're doing.  Converting a drive to GPT is not going to correct failed hardware that can't read a bootsector.

---

### Post by NUboon2Age on 2010-05-25
Tried parted ...

```

(parted) mklabel                                                          
New disk label type? msdos                                                
Error: Input/output error during read on /dev/sda 
```   

Doesn't surprise me since gparted had problems...  Let's see what else can I try before trying rebooting...

The reason I'm trying everything else I can before rebooting is that it took more than an hour last time to boot off Lucid Lynx (and I wasn't sure it was actually working) with this disk problem and I won't have wireless access even if it works whereas w/ Peppermint or SystemRescueCD I know will boot AND have wireless configured.

---

### Post by NUboon2Age on 2010-05-25
> **SRST Technologies said:**
> The answer to this problem was clear back on the first page, everyone.  If you don't understand the output of programs, don't disregard the output, find out what it means.  And for the love of god, stop giving advice on here if you don't know what you're doing.  Converting a drive to GPT is not going to correct failed hardware that can't read a bootsector.

No badblocks were reported by the badblocks program... Not sure if its really failed hardware.  Still hoping not.

---

### Post by SRST Technologies on 2010-05-25
Alright, I'll just wait until you decide to find out what the real problem is then.

---

### Post by NUboon2Age on 2010-05-25
Rebooting with Lucid Lynx CD.  Taking a looooong time....

---

### Post by NUboon2Age on 2010-05-25
> **SRST Technologies said:**
> Alright, I'll just wait until you decide to find out what the real problem is then.

Well if it were failed hardware, wouldn't badblocks have given errors?   Are there other tests that could check if its failed hardware?

---

### Post by NUboon2Age on 2010-05-25
Okay, still booting, but just gave an error and the Ubuntu splash screen is not visible any more.  This is what happened last time that I gave up on the boot eventually.

I think the error is a standard one that everyone booting from the CD gets about getpwuid failing.  That one doesn't concern me, but losing the splash screen that at least has the activity indicator does concern me.  If the system stops working the HD as it did last time, I have no way to tell if its still booting or not.  Any advice as to how I could bring that splash screen back up or other way to tell if its still trying to boot or has hung?

---

### Post by NUboon2Age on 2010-05-25
Okay, like last time the HD and CD activity lights went off and its just got a screen with the error message I described above on a black background.  I can't tell if its still working on booting up.  Is there any way to pull up the splash screen back up or other way to tell if its hung or still trying to boot up?  The screen saver is still working giving a blank screen.

---

### Post by srs5694 on 2010-05-25
> **NUboon2Age said:**
> Is gdisk a reasonable way to side-step these problems and get the disk workable?

No. I'm the author of gdisk, and you're expecting things of it that it just can't deliver. Although gdisk includes some recovery features, those are features for fixing *GPT data structure problems,* caused by software bugs or user error that corrupts the on-disk GPT data. Since your disk doesn't, as far as I know, use GPT, gdisk will be completely useless for recovering data on your disk; it has no GPT data structures to be corrupted.

My suspicion is that you've got a bad disk. Your smartctl --all output should have included significant amounts of debugging information, but it didn't. I notice that you included the --tolerance=verypermissive option to smartctl. If you needed this option, it suggests that the disk isn't responding to SMART commands -- either it's so old that it doesn't support SMART or it's very badly broken. In the former case, replacing the disk makes sense on principle (old disks are seldom reliable). If the latter, the disk is known to be unreliable. The other errors you've reported all point to a bad disk. The fact that badblocks didn't return any errors isn't conclusive evidence to the contrary, and whatever your theory, it must account for the failure of various tools to successfully access the disk. (There's one point here where gdisk provides useful data: It couldn't write to the disk. It should have been able to. The fact that it couldn't strongly suggests that there's something very badly wrong with the disk.)

You can continue to investigate all you want, and you might luck out and find a solution; but it's very likely that your time will be better spent shopping for a new disk.

---

### Post by warfacegod on 2010-05-26
Have you tried to install to a different HDD? If you can finish an install to another HDD that would go a long way to verifying that your first HDD is failing.

You may also want to check that the jumpers on your HDD are set properly. Master for the first, Slave for the second.

---

### Post by Perkins on 2010-05-26
> **NUboon2Age said:**
> 
```

{...}
214865% done, 4:13:57 elapsed
21487
21488
214896% done, 4:13:58 elapsed
21490
21491
214926% done, 4:13:59 elapsed
21493
214946% done, 4:14:00 elapsed
21495
21496
214976% done, 4:14:01 elapsed
21498
21499
215006% done, 4:14:02 elapsed
21501
21502
215036% done, 4:14:03 elapsed
done                                
Testing with pattern 0x55: done                                
Reading and comparing: done                                
Testing with pattern 0xff: done                                
Reading and comparing: done                                
Testing with pattern 0x00: 13.06% done, 11:05:24 elapsed

```

Badblocks spits out a list of *bad* sectors.  Every number that wasn't part of the "6% done" is a block that didn't read properly.  Looks like you have disk issues.  :(

---

### Post by Perkins on 2010-05-26
Furthermore, from the very large number of sequential blocks that are bad, odds are that the problem was not caused by a head crash or other, isolated physical incident.  So the odds of you being able to reformat around the bad sectors and have it work for any significant period of time are infinitesimally small.  

If the disk uses a SATA interface, Tigerdirect.com has a 1TB drive on sale for 75USD.

---

### Post by NUboon2Age on 2010-05-26
> **SRST Technologies said:**
> The answer to this problem was clear back on the first page, everyone... failed hardware that can't read a bootsector.

> **srs5694 said:**
> ...
My suspicion is that you've got a bad disk. Your smartctl --all output should have included significant amounts of debugging information, but it didn't...


> **Perkins said:**
> Badblocks spits out a list of *bad* sectors.  Every number that wasn't part of the "6% done" is a block that didn't read properly.  Looks like you have disk issues.  :-(


> **Perkins said:**
> Furthermore, from the very large number of sequential blocks that are bad, odds are that the problem was not caused by a head crash or other, isolated physical incident.  So the odds of you being able to reformat around the bad sectors and have it work for any significant period of time are infinitesimally small.  


Thank you so much everyone for your support and knowledge sharing about Linux disk utilities and especially to Perkins for explaining that output.  I had mistakenly thought that the numbers were just showing progress on which blocks and been checked, and I didn't realize it was saying those were actually bad.:-(

So when I saw Perkins notes earlier today (I missed srs5694's note until just now) it was the confirmation that I needed that this disk is having some kind of physical breakdown.

The computer previously was a dual boot, Windoze XP and Xubuntu system, but the Windoze part started getting blue screens and even after taking some XP recovery steps, stopped booting from Windoze but would still boot fine from Xubuntu.  I'm not sure if it got some kind of serious viral infection (ie. it was directly Windoze related) or if it was just experiencing general disk failure that just happened to begin in the Windoze partition.  

When I saw Perkins confirmation I went ahead and replaced the drive.  Now I have an all-Ubuntu 160Gib system and things are looking good.  I wanted to make sure I was giving the old disk every last chance I could, and with the help of all the folks that posted here we accomplished that and y'all taught me a lot more about Linux disk utilities and disks in general. :popcorn:

---

### Post by warfacegod on 2010-05-26
Too bad about that drive but these things happen. You might consider giving that 80 GB you were talking about a thorough shakedown as well.

---

### Post by NUboon2Age on 2010-05-26
Thanks go out to 
carlee
nhasian
srs5694
warfacegod
SRST Technologies
Perkins

---


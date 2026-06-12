---
title: "Mount drives"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by cartisdm on 2009-04-15
Ok, I was given a desktop computer from a friend to fix.  All they knew about it was "someone else tried to fix it and it still doesn't work."  Well, it doesn't boot into Windows.  I know they want to save their information on it, so I thought to myself the easiest thing to do was boot up using a LiveCD.

I have pretty much all ubuntu disks 7.04-8.10 but I can't seem to pick up their harddrive.  I know it's seen by the computer because it is listed in the BIOS.

Can anyone help me out on where to go next?

---

### Post by halitech on 2009-04-15
in the Live CD, open a terminal and post the results of 
```
sudo fdisk -l
```

Edit: you say it's listed, is it on auto and being found or has the info been entered in? Also try going back into the BIOS and auto detecting the drive again just to make sure.

---

### Post by cartisdm on 2009-04-15
> **halitech said:**
> in the Live CD, open a terminal and post the results of 
```
sudo fdisk -l
```

Edit: you say it's listed, is it on auto and being found or has the info been entered in? Also try going back into the BIOS and auto detecting the drive again just to make sure.

It's been detected via Auto.  Already re-detected the drive just to make sure.

Just tried sudo fdisk -1 and got

"sudo: unable to execute /sbin/fdisk: Input/output error"

---

### Post by halitech on 2009-04-15
okay, just wanted to make sure it wasn't manually entered settings.

```
: unable to execute /sbin/fdisk: Input/output error"
```

no help from google on that message, only 1 hit and the person said they rebooted and the sudo fdisk -l command worked.

---

### Post by cartisdm on 2009-04-15
Rebooted......their cd player literally chewed up my liveCD and now it's ruined. Awesome.

I'm rebooting now with a 8.04 liveCD

---

### Post by halitech on 2009-04-15
sounds like maybe their cdrom is having some issues and thats why the command didn't work. 

would love to see a pic of a damaged cd done by a cdrom, never seen one in all my days (not saying I don't believe, just never had it happen to me)

---

### Post by cartisdm on 2009-04-15
sudo fdisk -1 gave me this:

```
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
```


As for the disk, I took a quick picture with my phone.  Didn't show up very well but you can at least tell it's scratched!

---

### Post by halitech on 2009-04-15
ok, its actually a lower case L, not the number 1.

sudo fdisk -l

re pics: well I'll be, I've heard of that happening but never seen it. something must have been out of alignment for that to happen.

---

### Post by cartisdm on 2009-04-15
> **halitech said:**
> 
re pics: well I'll be, I've heard of that happening but never seen it. something must have been out of alignment for that to happen.

That's what happens when a broken computer lands in your lap and you have no idea where to begin when it comes to fixing it:)



As for the fdisk, my bad. I'm trying to do 100 things at once and didn't even pay attention to the output!

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
86 heads, 15 sectors/track, 484606 cylinders
Units = cylinders of 1290 * 512 = 660480 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      208090   134217727+   4  FAT16 <32M

Disk /dev/sda1: 137.4 GB, 137438952960 bytes
86 heads, 15 sectors/track, 208089 cylinders
Units = cylinders of 1290 * 512 = 660480 bytes
Disk identifier: 0x00000001

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   *           1      208090   134217727+   4  FAT16 <32M

```

---

### Post by halitech on 2009-04-15
> **cartisdm said:**
> That's what happens when a broken computer lands in your lap and you have no idea where to begin when it comes to fixing it:)

Been there myself but usually I get a phone call saying 'It's not working!' with no other information ~L~

> As for the fdisk, my bad. I'm trying to do 100 things at once and didn't even pay attention to the output!

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
86 heads, 15 sectors/track, 484606 cylinders
Units = cylinders of 1290 * 512 = 660480 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      208090   134217727+   4  FAT16 <32M

Disk /dev/sda1: 137.4 GB, 137438952960 bytes
86 heads, 15 sectors/track, 208089 cylinders
Units = cylinders of 1290 * 512 = 660480 bytes
Disk identifier: 0x00000001

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   *           1      208090   134217727+   4  FAT16 <32M

```

ok, it looks like they have a 320 gig hard drive but only 137gig is being seen by windows and its formatted in FAT16. What operating system was on the drive prior to you getting it? Also, what type of system? (ie, P4, P2, AMD?)

maybe post the output of ```
lshw -C cpu
```

---

### Post by thane1 on 2009-04-15
Blasphemy I know, but if you cannot get it sorted with Ubuntu, you could probably do it through the Evil Empire OS. Assuming the Win drive can in fact be read, the HDD can be disconnected, set to slave via the jumpers, and another drive (set to master) can be connected to the computer if there's an available connector. Install Windows onto the new master drive and then the computer can be booted up with the new Windows and files can then be accessed from the old drive (as I said, assuming that drive can in fact be read). In this way, you can pull home directory files/directories off the old drive to make sure they're safely backed up onto the media of your choice (sounds like the computer owner didn't back anything up or else they probably wouldn't be in a panic.) When the files are safely removed you can just reinstall Windows on the messed up computer drive and/or check the integrity of the drive. Probably a good idea to give the owner a new installation of Windows anyway - their fat 16 seems pretty outdated. Also their Windows installation seems like its probably so old (fat 16), that a new installation might well clear up other (ie - speed) problems.  This is a bit of a hardware type of fix, but its a good way to reinstall Windows/back up user files and get around Windows' resistance to letting you reinstall Windows on a machine, which already has a copy of Windows installed.

---

### Post by nyk on 2009-04-15
If all you want to do is recover the hdd's data, testdisk is a really powerful program that can scan your entire disk, and find any partitions that have ever been on it, then you can copy all of the files out of the drive to a back up.

---

### Post by cartisdm on 2009-04-15
> **halitech said:**
> ok, it looks like they have a 320 gig hard drive but only 137gig is being seen by windows and its formatted in FAT16. What operating system was on the drive prior to you getting it? Also, what type of system? (ie, P4, P2, AMD?)

It was running Windows XP on AMD.  I plan on just reinstalling that after I recover the data, it's just becoming more of a hassle than I had planned for (thought this was a 1 beer fix...it's already working on a 3 beer problem)


maybe post the output of ```
lshw -C cpu
```

```
  *-cpu:0                 
       description: CPU
       product: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
       vendor: Advanced Micro Devices [AMD]
       physical id: 6
       bus info: cpu@0
       version: 15.11.2
       slot: Socket M2
       size: 1GHz
       capacity: 3GHz
       width: 64 bits
       clock: 200MHz
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps cpufreq
  *-cpu:1
       description: CPU
       vendor: AMD
       physical id: 7
       bus info: cpu@1
       version: 15.11.2
       slot: Socket M2
       size: 1GHz
       capacity: 3GHz
       clock: 200MHz
       capabilities: cpufreq
```

---

### Post by halitech on 2009-04-15
the board should handle more then a 137gig drive so not sure why its only showing that... I wonder if it had 98 or ME on it and they've upgraded and were using a drive overlay program on an older system that didn't see over the 137gig limit. 

Can you check the BIOS again and see if LBA is on 48bit or not.

---

### Post by cartisdm on 2009-04-15
> **halitech said:**
> the board should handle more then a 137gig drive so not sure why its only showing that... I wonder if it had 98 or ME on it and they've upgraded and were using a drive overlay program on an older system that didn't see over the 137gig limit. 

Can you check the BIOS again and see if LBA is on 48bit or not.

Not 100% how to check for that.  Access mode is on Auto and
Capacity: 320gb
Cylinder: 65535
Head: 16
Precomp: 0
Landing Zone: 65534
Sector: 16

if that helps the situation. Not quite sure what we're getting at here - this all goes over my head, there isn't a way to just force mount this drive so I can copy over the data?

---

### Post by halitech on 2009-04-15
not sure if it will work but check the info from the bottom of this page

[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by cartisdm on 2009-04-15
> **halitech said:**
> not sure if it will work but check the info from the bottom of this page

[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

nope

---

### Post by halitech on 2009-04-15
didn't think so .... I think the drive is totally farked. what happens when you try to boot into windows?

---

### Post by cartisdm on 2009-04-15
> **halitech said:**
> didn't think so .... I think the drive is totally farked. what happens when you try to boot into windows?

To be honest, I'm not sure it's even installed anymore (he had someone else "work" on it before me). That's why I wanted to mount the drive and see what was on there. After the POST it just hangs.  No NTDLR error or anything. I just emailed the guy who owns the computer to ask how important the data is to him - I never mind working on a friend's computer who needs a computer but at some point you gotta call it quits

---

### Post by halitech on 2009-04-15
well there is definately something screwy going on here and got to love those "friends" who "know" something about computers that end up making things worse then they were originally.

Hopefully its nothing more important then his daughters mp3 collection and you can try to wipe and reinstall.

got 2 ideas, not sure if either will really help but worth a shot

1. Use Gparted live cd to see what it sees

2. Use SuperGrub boot disk to see if we can repair the MBR on the drive and get some idea whats going on.

---

### Post by cartisdm on 2009-04-15
> **halitech said:**
> 
got 2 ideas, not sure if either will really help but worth a shot

1. Use Gparted live cd to see what it sees

2. Use SuperGrub boot disk to see if we can repair the MBR on the drive and get some idea whats going on.

Already tried Gparted.  From what I remember (it was two weeks ago) it didn't say anything out of the ordinary.  It picked up the harddrive as normal and showed all 320gb.  Hopefully I'll hear back from him and I can just reinstall XP.

I really appreciate the time you put in for helping me out, I might be back here trying to get to the bottom of this!

---

### Post by halitech on 2009-04-15
did gparted show a single partition or 2? (if you remember)

---

### Post by cartisdm on 2009-04-15
> **halitech said:**
> did gparted show a single partition or 2? (if you remember)

Unfortunately, I don't remember.  I already disconnected the desktop tower (was using my lcd TV so it's a real pain to set up a work station), but next time I'm working on it I will check

(although I feel like there was only one partition)

---

### Post by halitech on 2009-04-15
no worries, just thought if you happened to remember it might give me an idea

---

### Post by cartisdm on 2009-04-16
Just an update:

- He doesn't care about the data, so I tried to just install Windows
- Computer randomly shuts off after pressing a key on the keyboard during installation (Enter, F8, D, L etc.)
- Tried different RAM sticks
- Tried removing all PCI cards
- Tried different power supply
- Tried 3 different Windows XP disks
- Tried monitoring the temperatures, everything seemed ok
- Finally tried a new harddrive.  That got me through the initial windows setup part, but then when it reboots and tries to actually load the Windows Splash screen I started getting different BSODs (Video driver load error, memory dump, and a few other can't remember)

My conclusion, there must be something wrong with the motherboard.  Unfortunately, I'm at college and don't have much other stuff to try and test out the computer with.  Oh well, I tried.

---


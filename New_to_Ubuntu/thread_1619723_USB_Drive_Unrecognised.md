---
title: "USB Drive Unrecognised"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by widda on 2010-11-12
Greetings. 
USB storage drive 120Gb is not recognised. It was recognised some months ago.
Since then seen so many threads on UUID, Mount, fstab mtab, and written and deleted things, I can't remember what suggestions I followed or guessed at interpreting. and left with nothing but confusion.
Totally fried on the subject, I yelp if I see the word mount.
Wondering if any hardy person would care to speak to me about how to make all settings right so that when I plug it in, it appears on system, and I can use it. 
All I know is that I used to do it, and now I can't.
And this notice has been appearing on screen during boot without and with drive - 
"The disk drive for media/D4 is not ready yet or not present.Wait,S for skip,Mfor manual"

---

### Post by tarps87 on 2010-11-12
I'm afraid I am going to use that word again, can you post the output of mounting it manually
```
fdisk -l
```
Find drive location e.g. /dev/***sdb***
```
sudo mkdir /media/usbhere
sudo mount /dev/***sdb1*** /media/usbhere
```

Note ***sdb1*** replace sdb with your drive from fdisk -l

I am expecting this to fail as I am working on the assumption this has also been used with a windows machine and has failed to umount it's self, the output from mounting it should confirm this

---

### Post by widda on 2010-11-12
Thank you tarps

```
laptop:~$ sudo fstab -l
[sudo] password for : 
sudo: fstab: command not found
laptop:~$ fstab -l
fstab: command not found
laptop:~$ sudo mkdir /media/usbhere
mkdir: cannot create directory `/media/usbhere': File exists
laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x75d475d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19272   154802308+  83  Linux
/dev/sda2           19273       19457     1486012+   5  Extended
/dev/sda5           19273       19457     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 2057 MB, 2057830400 bytes
52 heads, 51 sectors/track, 1515 cylinders
Units = cylinders of 2652 * 512 = 1357824 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1516     2009478+   6  FAT16
laptop:~$ sudo mount /dev/sdb1 /media/usbhere
```And then just blinking as tho it did something.

---

### Post by widda on 2010-11-12
I looked now at  /media,and in /media/usbhere are the contents of 2gb camcard (called just sdb in the terminal list.)
 also in /media is:
 /disk containing same
 /sdb1 containing nothing
 /D4 (name of problem usbdrive)
 These 3 were there before.

---

### Post by Trevster on 2010-11-12
Hello,

The USB drive partition is not seen at all with the fdisk -l command. The USB drive should automount. Is this a NTFS formated drive?

You could try the lsusb command to list all usb connected devices.

---

### Post by Verbeck on 2010-11-12
> **widda said:**
> 

```

laptop:~$ sudo mount /dev/sdb1 /media/usbhere
```And then just blinking as tho it did something.

you should press enter after that last command

---

### Post by widda on 2010-11-12
```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 008: ID 058f:6390 Alcor Micro Corp. USB 2.0-IDE bridge
Bus 002 Device 005: ID 046d:c043 Logitech, Inc. MX320/MX400 Laser Mouse
Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 003: ID 04d9:1400 Holtek Semiconductor, Inc. 
Bus 002 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 19d2:0031 ONDA Communication S.p.A. ZTE MF636
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Computer has slowed down since this process and maybe will be unable . Prob drive is whirring quietly and comp twittering, quite slow

---

### Post by widda on 2010-11-12
Good point!
laptop:~$ sudo mount /dev/sdb1 /media/usbhere
[sudo] password for : 
mount: special device /dev/sdb1 does not exist

---

### Post by widda on 2010-11-12
Thanks trev , verb, ..when i say slow means2-3min to open terminal,2-3 sec move cursor, 1-2 sec make letter

---

### Post by widda on 2010-11-12
> Is this a NTFS formated drive?

don't know, think yes bcoz tried some g-ntfs3? stuff awhile there for the cure

---

### Post by tarps87 on 2010-11-12
Right let clear things up. If your card reader is an external reader please disconnect it.
Disconnect the usb drive and run
```
lsusb
```
Now plug the hard drive in and type lsusb again
```
lsusb
```

Please post the output from both times.
Does this drive work on other PCs?

From what I can see, the drive is not recognised and it has actually mounted your card reader in the first steps

Oh and sorry about the wrong command name, I have corrected the post

---

### Post by widda on 2010-11-12
```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 046d:c043 Logitech, Inc. MX320/MX400 Laser Mouse
Bus 002 Device 003: ID 04d9:1400 Holtek Semiconductor, Inc. 
Bus 002 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 19d2:0031 ONDA Communication S.p.A. ZTE MF636
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 058f:6390 Alcor Micro Corp. USB 2.0-IDE bridge
Bus 002 Device 006: ID 046d:c043 Logitech, Inc. MX320/MX400 Laser Mouse
Bus 002 Device 003: ID 04d9:1400 Holtek Semiconductor, Inc. 
Bus 002 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 19d2:0031 ONDA Communication S.p.A. ZTE MF636
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I don't know if works in other PC, I'll try it when I get to the town, but it will be windows.

---

### Post by widda on 2010-11-12
btw, I'm using Dell Latitude D660 512Mb 1.6Gh
And the drastic speed loss of last night is over.

---

### Post by tarps87 on 2010-11-15
It looks like it is being recognised, just not as a hard drive. After plugging the drive type
```
dmesg | tail
```
and post the output here, this should show us what the machine does when it detects the hard drive

---

### Post by widda on 2010-11-15
```
[24956.984634] scsi 12:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
[24956.991476] sd 12:0:0:0: Attached scsi generic sg7 type 0
[24957.000581] sd 12:0:0:0: [sdg] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[24957.005561] sd 12:0:0:0: [sdg] Write Protect is off
[24957.005571] sd 12:0:0:0: [sdg] Mode Sense: 03 00 00 00
[24957.005580] sd 12:0:0:0: [sdg] Assuming drive cache: write through
[24957.015574] sd 12:0:0:0: [sdg] Assuming drive cache: write through
[24957.015587]  sdg: sdg1 sdg2 sdg3
[24957.082553] sd 12:0:0:0: [sdg] Assuming drive cache: write through
[24957.082563] sd 12:0:0:0: [sdg] Attached SCSI disk
```

---

### Post by tarps87 on 2010-11-15
Interesting, what is the output of
```
sudo fdisk -l /dev/sdg
```
Assuming you have not disconnected the drive

It appears that the drive is detected correctly, I do not understand why fdisk -l did not show it

> **widda said:**
> ```
[24956.984634] scsi 12:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
[24956.991476] sd 12:0:0:0: Attached scsi generic sg7 type 0
[24957.000581] sd 12:0:0:0: [sdg] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[24957.005561] sd 12:0:0:0: [sdg] Write Protect is off
[24957.005571] sd 12:0:0:0: [sdg] Mode Sense: 03 00 00 00
[24957.005580] sd 12:0:0:0: [sdg] Assuming drive cache: write through
[24957.015574] sd 12:0:0:0: [sdg] Assuming drive cache: write through
[24957.015587]  **sdg: sdg1 sdg2 sdg3**
[24957.082553] sd 12:0:0:0: [sdg] Assuming drive cache: write through
[24957.082563] sd 12:0:0:0: [sdg] Attached SCSI disk
```

---

### Post by widda on 2010-11-15
Thanks 
I've never seen ref. to 'sdg' before.
```
Disk /dev/sdg (Sun disk label): 255 heads, 63 sectors, 14593 cylinders
Units = cylinders of 16065 * 512 bytes

   Device Flag    Start       End    Blocks   Id  System
/dev/sdg1             0     14587 117170077+  83  Linux native
/dev/sdg2  u      14587     14593     48195   82  Linux swap
/dev/sdg3             0     14593 117218272+   5  Whole disk

```

---

### Post by tarps87 on 2010-11-17
Ok this is strange now, it looks like this drive is formatted for a Linux install. Did you try this on another machine?

Could you try this again:
```
sudo mkdir /media/sdg
sudo mount /dev/sdg1 /media/sdg
```

Relying on this appearing after plugging the USB drive in
[24957.015587]  **sdg: sdg1 sdg2 sdg3**
else change sdg1 accordingly

---

### Post by philinux on 2010-11-17
Tarps,

Maybe sys>admin>disk utility might see it and thus reformat it?

---

### Post by tdapower on 2010-11-17
Open the terminal and type
sudo rm -r /media/usb*
and press return

Now try reconnect the usb drive

---

### Post by tarps87 on 2010-11-17
> **philinux said:**
> Tarps,

Maybe sys>admin>disk utility might see it and thus reformat it?

I was thinking a reformat maybe but I am not confident which drive is the correct one or if the data is important. It is certainly worth trying to detect it using the disk utility tool

---

### Post by widda on 2010-11-17
Hey **thanks** for all the help, now I dont want to mix and match procedures here, so :
I won't do tda's rm -r just yet in case it crosses train of thought of Tarps,
 and I can't do yours yet Tarps, because I don't quite understand it. But you agree with philinux about Disk Utility, which I'd never seen before:redface:.so here's screenshot.  - sd**f** now!
(Sorry not very good at hopping from forum to reply and back and managing quotes and not losing reply halfway through, so we're a bit clunky.) 
I can't go back to yr exact words safely Tarps, but I understand the code-entering part, but don't know what you mean by sdg etc 'appearing', 
Also , while I was in Disk Utility, I pressed 'safely remove drive', and it disappeared from list at left, I unplugged it, replugged it, and it re-appeared in Disk Utility as before.
Also:data on disk: would prefer to keep, but am prepared to lose in DiskUtil formatting experiment if advised.

---

### Post by widda on 2010-11-17
Oh, and no, not yet tried on another machine

---

### Post by ironic.demise on 2010-11-17
> **widda said:**
> Hey **thanks** for all the help, now I dont want to mix and match procedures here, so :
I won't do tda's rm -r just yet in case it crosses train of thought of Tarps,
 and I can't do yours yet Tarps, because I don't quite understand it. But you agree with philinux about Disk Utility, which I'd never seen before:redface:.so here's screenshot.  - sd**f** now!
(Sorry not very good at hopping from forum to reply and back and managing quotes and not losing reply halfway through, so we're a bit clunky.) 
I can't go back to yr exact words safely Tarps, but I understand the code-entering part, but don't know what you mean by sdg etc 'appearing', 
Also , while I was in Disk Utility, I pressed 'safely remove drive', and it disappeared from list at left, I unplugged it, replugged it, and it re-appeared in Disk Utility as before.
Also:data on disk: would prefer to keep, but am prepared to lose in DiskUtil formatting experiment if advised.
According to the screenshot, the drive is unformatted entirely...

I'm sure if you erase all partitions and place an entire ext4 or ntfs partition on there it will work as intended, though if you want to save some of the data (probably won't work very well) use photorec or foremost.

Correct me if I'm wrong people?

ALSO, the "free partition"... You can just click "create partition" and make a maximum size partition with no problems hopefully giving you nearly all 120gb back

BUT it's got an unknown partition table, I would recommend formatting the WHOLE disk as MBR.

---

### Post by widda on 2010-11-17
> BUT it's got an unknown partition table, I would recommend formatting the WHOLE disk as MBR.
Ironic.,is that a simple procedure to explain or do I need to research? It sounds like the cleanest and surest solution, and I really dont care about the data I guess, most of it I have anyway -

---

### Post by ironic.demise on 2010-11-17
Very simple and easy
>System >Administration >Disk Utility
Select the 120gb drive
click Format drive *(erase or partition the drive)*
choose MBR (Compatable with most things, except things like Mac, I assume you aren't using MAC).

WARNING: This will clean the drive of all data and partitions

Then click the large white block saying "free", this will highlight it
then click create partition (or something to that effect).
Choose the filesystem (NTFS, FAT, EXT4 most will be fine) and just verify.

I'm telling you, for your own sake DOUBLE, TRIPLE check the drive you are formatting, though it's hard to get it wrong if you know the size of the drive and it looks like you won't make a mistake, it usually happens to people who are used to formatting and can rush.

---

### Post by tarps87 on 2010-11-18
Based on the screenshot you can ignore my instructions, it look like your partition table has been corrupted. Based on you already using this disk it must have been formatted a one stage.
It may be possible to recreate the partition table, however I have not actually tried doing this. Somebody else may have more experience with this.
If you can not find a way to recreate the table a format will be the quickest and easiest way, however you will lose your data

---

### Post by widda on 2010-11-18
Thanks tarps, ironic,I am just fooling with it now again
This morning I did format. and then went to create partition (ext4) and the "this is happening" signal just rotates for hours. When I try to change tack, like delete partition or format again, it says drive is busy.
I'm fine with losing all data

---

### Post by Mark Phelps on 2010-11-18
Others may (or probably, WILL) disagree, but I don't trust the new Disk Utility; instead, I prefer the old "tried and true" Partition Editor -- GParted.

If that's not already there, I would install it and look at the drive using that.

Also, if you haven't done so already, open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  It will list all the partitions on the disk.

It will be interesting to compare the outputs of these two with the disk utility screen.

---

### Post by ironic.demise on 2010-11-18
> **widda said:**
> Thanks tarps, ironic,I am just fooling with it now again
This morning I did format. and then went to create partition (ext4) and the "this is happening" signal just rotates for hours. When I try to change tack, like delete partition or format again, it says drive is busy.
I'm fine with losing all data

"Device Busy" usually means the drive is mounted somewhere or doing something...

Ok, this "should" be a failsafe method.
1: Boot into an Ubuntu LiveCD
2: Open >System >Administration >GParted
3: Using GParted follow the same method as before
```
IT IS VERY POSSIBLE YOUR DRIVE IS NOT sdf! I cannot warn you enough, from a LiveCD it is easier to format the wrong drive, double and TRIPLE check you have the right drive selected
``````
1: Select /dev/sdf
2: Format drive
3: Create ext4 partition
```
I don't have GParted open right now so I don't know the *exact* method but it shouldn't be too hard.

: oh btw. on my PC (1gb ram, 120gb HDD) the formats AND partition creation take no more than a minute :

---

### Post by widda on 2010-11-19
So: It doesnt show on onboard Gparted,
shows on Diskutility as sdf
shows on fdisklu command as sdc!
There's only one 120Gb drive ever used, so no worries about which one's being referred to.
Hope this helps .
here are the screenshots

---

### Post by widda on 2010-11-19
Well after a prompted Update Manage, and 3 or 4 Restarts

 (trying to "run 86+ memtest on boot" to check Ram, which on lshw has the 2 slots? listed as 64bit and i know my system is 32),
AND, what do i see on the desktop, New Volume, opened it, i item  (Lost+Found).
This looks a lot like success to me, if anyone has an idea which of the things I did might have done it?
Anyway, now I.m going to Remove Drive Safely" and plug it in again and watch the desktop.
Thanks to you all for the help.
 I wouldn't have got there on my own in a long time!

---

### Post by widda on 2010-11-19
YES, it's plug'n'play!

---

### Post by tarps87 on 2010-11-19
> **Mark Phelps said:**
> Others may (or probably, WILL) disagree, but I don't trust the new Disk Utility; instead, I prefer the old "tried and true" Partition Editor -- GParted.

If that's not already there, I would install it and look at the drive using that.

Also, if you haven't done so already, open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  It will list all the partitions on the disk.

It will be interesting to compare the outputs of these two with the disk utility screen.

Never used the Disk Utility but definitely agree with gparted

> **widda said:**
> YES, it's plug'n'play!

That's good to hear, I still have not got a clue why this happened in the first place though

---

### Post by widda on 2010-11-21
Dear reader, this thread is marked SOLVED, but maybe no-one knows which of the suggestions if any, solved it.
But at the least you will find in these pages some likely helpful areas to look into for usbdrive probs.
And thanks again tarps,ironic,mark,phil,verbeck, this has been an insistent problem, and your help enabled me to see that there was only one choice, to reformat.

---


---
title: "mounting /dev on /root/dev failed: No such file or directory (different)"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by Golden_Ocelot on 2011-04-17
Already read this thread which was a great help, however, still unable to use ubuntu : [http://ubuntuforums.org/showthread.php?t=1244466](http://ubuntuforums.org/showthread.php?t=1244466)

My computer is an Acer Aspire 5335 running ubuntu 10.1, so similar issues all around. This occured after sleep mode recovery after the latest update.

sudo fdisk -l gives me 


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units= cylinders of 16065 * 512 bytes/ 512 bytes
I/O size (minimum/optimal): 512 bytes/ 512 bytes
Disk Identifier: 0x23c460d1

......Device....Boot...Start....End..........Blocks....Id.....System
/dev/sda1...................1...1275....10240000.....27....Unknown
/dev/sda2.........*...1275..15839..116984832.....7....HPFS/NTFS
/dev/sda3............15839..20979...41282360......7....HPFS/NTFS
/dev/sda4...........20979...30402...75689985......5....Extended
/dev/sda5...........20979...30012...72560640.....83....Linux
/dev/sda6...........30012...30402.....3128320.....82....Linux swap/Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016
255 heads, 63 sectors/track, 121601 cylinders
Units= cylinders of 16505 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes/ 512 bytes
[FONT=monospace]I/O size (minimum/optimal): 512 bytes/ 512 bytes
Disk identifier: 0xa2dd331e

Device..Boot... Start..... End.........Blocks...Id...System
/dev/sdc1..........1....121601......976760001....c...W95 FAT32 (LBA)

(sorry for the bad formatting, its all typed out ><)


[/FONT]sudo mkdir /mnt/ubuntu && sudo mount /dev/sda1 /mnt/ubuntu gives me mkdir cannot create directory, file exists

ftab comes up blank.

when attempting to mount /dev/sdc1, can't find /dev/scd1 in /ect/mtab

cat /*/*/etc/fstab gives no such file or directory

sudo e2fsck -fyv /dev/sda1
gives me "no such file or directory when trying to open"

The superblock could not be read or does not describe a correct ext2 filesystem., etc

Theres more instructions i could follow from the other thread, but theres a lot of deviations from what was working, so... I implore thee for help!

Plus, would like to be able to wipe out all by 2 of the partitions, but cannot get it to work properly, however, getting the computer working properly before i try that project is a bit more important.

---

### Post by Golden_Ocelot on 2011-04-18
ahh, i should mention that i have no experience with linux, was installed using cd for 10.10 ubuntu, have searched through the forums to find similar threads (and followed their instructions to no avail), and that the system was working fine until the last update batch and recovered from hibernate mode to find that error.

---

### Post by CMPounder on 2011-04-18
I too have the same problem with similar outputs/results. 10.04 LTS. I've tried the same fixes and am getting nowhere. NEWB, too.
 
Thanks!

---

### Post by nothingspecial on 2011-04-18
> **Golden_Ocelot said:**
> Already read this thread which was a great help, however, still unable to use ubuntu : [http://ubuntuforums.org/showthread.php?t=1244466](http://ubuntuforums.org/showthread.php?t=1244466)

My computer is an Acer Aspire 5335 running ubuntu 10.1, so similar issues all around. This occured after sleep mode recovery after the latest update.

sudo fdisk -l gives me 


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units= cylinders of 16065 * 512 bytes/ 512 bytes
I/O size (minimum/optimal): 512 bytes/ 512 bytes
Disk Identifier: 0x23c460d1

......Device....Boot...Start....End..........Blocks....Id.....System
/dev/sda1...................1...1275....10240000.....27....Unknown
/dev/sda2.........*...1275..15839..116984832.....7....HPFS/NTFS
/dev/sda3............15839..20979...41282360......7....HPFS/NTFS
/dev/sda4...........20979...30402...75689985......5....Extended
/dev/sda5...........20979...30012...72560640.....83....Linux
/dev/sda6...........30012...30402.....3128320.....82....Linux swap/Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016
255 heads, 63 sectors/track, 121601 cylinders
Units= cylinders of 16505 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes/ 512 bytes
[FONT=monospace]I/O size (minimum/optimal): 512 bytes/ 512 bytes
Disk identifier: 0xa2dd331e

Device..Boot... Start..... End.........Blocks...Id...System
/dev/sdc1..........1....121601......976760001....c...W95 FAT32 (LBA)

(sorry for the bad formatting, its all typed out ><)


[/FONT]sudo mkdir /mnt/ubuntu && sudo mount /dev/sda1 /mnt/ubuntu gives me mkdir cannot create directory, file exists

ftab comes up blank.

when attempting to mount /dev/sdc1, can't find /dev/scd1 in /ect/mtab

cat /*/*/etc/fstab gives no such file or directory

sudo e2fsck -fyv /dev/sda1
gives me "no such file or directory when trying to open"

The superblock could not be read or does not describe a correct ext2 filesystem., etc

Theres more instructions i could follow from the other thread, but theres a lot of deviations from what was working, so... I implore thee for help!

Plus, would like to be able to wipe out all by 2 of the partitions, but cannot get it to work properly, however, getting the computer working properly before i try that project is a bit more important.

First off you need to do all this from a live cd.

Second, you need to fsck /dev/sda5

Third don't try to fsck a mounted file system, so if you are going to ```
sudo mkdir /mnt/ubuntu && sudo mount -t ext4 /dev/sda5 /mnt/ubuntu
```

and it works, Don't fsck it until you have done ```
sudo umount /mnt/ubuntu
``` first.

And if you have no idea what I'm blabbering on about, post back before you do anything.

---

### Post by CMPounder on 2011-04-18
"and that the system was working fine until the last update batch and recovered from hibernate mode to find that error."
 
me too!
 
Thanks,
Chris

---

### Post by Golden_Ocelot on 2011-04-18
well, thank you very much, nothingspecial. and Thanks to all the great programs and users here, i've been able to figure a good bit out by reading, and am glad to share what little ive learned with our other new users

Live CD- any ubuntu bootable CD, including install disks, as they contain "try ubuntu", which will let you access the O/S.

To enter those commands (notably sudo), Accessories-> Accessories-> Terminal

the Terminal is the non-GUI interface of ubuntu (much like ms-dos for older windows, which i have quite a bit of experience with)

GUI- Graphical User Interface- ie.. Windows, Ubuntu interactive folders and mouse pointer, etc.



aaaand fsck gave me permission denied, must have r/w access to the file system or be root

---

### Post by nitstorm on 2011-04-18
Add **sudo  **before fsck...

---

### Post by Golden_Ocelot on 2011-04-18
sudo fsck /dev/sda5
device or resource busy while trying to open /dev/sda5
filesystem mounted or opened exclusively by another program?

sudo umount /dev/sda5
not mounted

sudo fsck /dev/sda5
device or resource busy while trying to open /dev/sda5
filesystem mounted or opened exclusively by another program?

edit: sudo umount /mnt/ubuntu
not mounted

---

### Post by nothingspecial on 2011-04-18
It may be mounted somewhere else

Go to your places menu and click the little eject icons to the right of anything.........

.....if you see what I mean, then fsck again.

---

### Post by Golden_Ocelot on 2011-04-18
> **nothingspecial said:**
> It may be mounted somewhere else

Go to your places menu and click the little eject icons to the right of anything.........

.....if you see what I mean, then fsck again.

checked, none, it asks to mount them all when i hover, just to be sure

okay, i've been trying to work on this for 3 days straight, i'm tired of having all my very little free time taken up with it, i will be formatting the entire ubuntu drive at this point and reinstalling from scratch, unless there's anything else that can be done

i do thank you for the help, though, at least i understand ubuntu/debian better with the forums here, i just dont have enough time to wait to recover a week's worth of data (that's as long as we'd been using ubuntu here..)


EDIT (again): Alright, all formatted and reinstalled. after tinkering around in windows for a bit, found out that the partition holding ubuntu had become corrupted >< ouch. tried to fix it, and got the lovely grub recovery screen. Thanks to your help, and the wonderful people all over the forum, was able to poke around on the live cd and get it fully formatted and recovered, so I'm back on a full ubuntu version! it seems as though errors in the partition were half the problem, so if theres any further advice, please help CMPounder (and anyone else who winds up in this position).

So thank you all very much, its very appreciated (despite my lack of patience at having a several hundred dollar paperweight, haha)

---


---
title: "Ubuntu won't boot, and I need to recover some important files. :("
date: 2011-06-24
forum: New to Ubuntu
---

### Post by Noirtheater on 2011-06-24
Hello there y'all,

I've been checking some threads around here and trying some of the recommended stuff, but nothing worked, I hope you guys can help me out, since I'm kind of desperate as I'm trying to recover some important files for work that are due next Monday. :(

I updated my system last night before going to bed and turned the laptop off, and when I tried to boot it up again this morning, it wouldn't boot. It says the following:

```
mount: mounting /dev/disk/by-uuid/d7006343-535e-4b63-9c40-c1ed66cf37af on /root failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init founf. Try passing init= bootarg.
```

As suggested in [this thread]("http://ubuntuforums.org/showthread.php?t=1701311"), I ran Ubuntu 10.04 from the CD and ran the Boot Info Script, and these are the results:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       En algunos casos se encuentra informaciÃ³n en syslog, pruebe
   dmesg | tail   o algo parecido


sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 8192.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disco /dev/sda: 64.6 GB, 64592281600 bytes
255 cabezas, 63 sectores/pista, 7852 cilindros, 126156800 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
TamaÃ±o de sector (lÃ³gico / fÃ*sico): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   120,918,015   120,915,968  83 Linux
/dev/sda2         120,920,062   126,154,751     5,234,690   5 Extended
/dev/sda5         120,920,064   126,154,751     5,234,688  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disco /dev/sdb: 4034 MB, 4034838528 bytes
255 cabezas, 63 sectores/pista, 490 cilindros, 7880544 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
TamaÃ±o de sector (lÃ³gico / fÃ*sico): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     7,871,849     7,871,787  83 Linux


Drive: sdc _____________________________________________________________________

Disco /dev/sdc: 16.0 GB, 16039018496 bytes
255 cabezas, 63 sectores/pista, 1949 cilindros, 31326208 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
TamaÃ±o de sector (lÃ³gico / fÃ*sico): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               8,192    31,326,207    31,318,016   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        d7006343-535e-4b63-9e40-c1ed66ef37af   ext4       
/dev/sda5        68dd5ce3-5272-46e0-9c33-fb3f84da0182   swap       
/dev/sdb1        ac92bce5-c70e-40bc-a9b5-b321e2d0bf89   ext4       
/dev/sdc1        6D94-2646                              vfat       Shrine

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 e0 4f 00 00 00  |............O...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

I hope you guys can help me out with my problem. Thank you very much in advance! :)

---

### Post by Bachstelze on 2011-06-24
From the Live CD, mount your Linux partition

```
sudo mount /dev/sda1 /mnt
```

And post the contents of /mnt/etc/fstab. Also you should be able to back up your files from /mnt in case you need a reinstall.

---

### Post by jtarin on 2011-06-24
What version of Ubuntu are you running?

---

### Post by owiknowi on 2011-06-24
workaround in order to rescue your files.
where are your personal files normally stored?
usually you'll find them in /ome/yourname unfortunately located in the system partition. or did you create a separate partition for /home? 

if you know where they are stored you could try a live cd like knoppix, or even ubuntu, and try to access them and copy(!) them to a external device (usb, hdd, cd/dvd, etc.)

---

### Post by erasmusp on 2011-06-24
Although, just a thought, you could recover these important files onto a flash disk or something while you booted up with the Live CD......;)

---

### Post by erasmusp on 2011-06-24
SNAP! owiknowi and I had the same bright suggestion! :D

---

### Post by jtarin on 2011-06-24
Would one of you good souls tell the OP how to accomplish recovering his files step by step?

---

### Post by owiknowi on 2011-06-24
think bachstelze has it allready covered...

---

### Post by Bachstelze on 2011-06-24
> **jtarin said:**
> Would one of you good souls tell the OP how to accomplish recovering his files step by step?

Mount the root partition as I said. The files will be under /mnt, copy them to a USB drive or something like that.

---

### Post by Noirtheater on 2011-06-24
@Bachstelze
I just tried your suggestion, but it didn't work. I got the following error message:

```
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
missing codepage or helper program, or other error
Sometimes information can be found on syslog, try dmesg | tail or so.
```

---

@ jtarin
I'm using Ubuntu 10.04, both as my Live CD and as the version I had installed on my laptop.

---

@owiknowl & erasmusp
I had all my files stored at /home/angel (my username), which is in the same partition as the system partition (but now that you mention it, for my next reinstall I'm creating a separate partition for my /home folder, that will probably save me from any further problems like this, thanks for the tip!)

The problem is that I can't access that partition as I get the error message stated above in Live CD whenever I try to mount/access it, so I can't take the files to an external USB hard-drive. :(

---

### Post by Bachstelze on 2011-06-24
> **Noirtheater said:**
> @Bachstelze
I just tried your suggestion, but it didn't work. I got the following error message:

```
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
missing codepage or helper program, or other error
Sometimes information can be found on syslog, try dmesg | tail or so.
```

That's bad. It means your filesystem might be corrupted. Do you have something interesting in [FONT="monospace"]dmesg [ tai[/FONT]l?

---

### Post by Noirtheater on 2011-06-24
> **Bachstelze said:**
> That's bad. It means your filesystem might be corrupted. Do you have something interesting in [FONT="monospace"]dmesg [ tai[/FONT]l?

This is what I got:

```
[ 2318.484699]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2318.484741]         06 80 0a 38 
[ 2318.484759] sd 0:0:1:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 2318.484780] sd 0:0:1:0: [sda] CDB: Write(10): 2a 00 06 80 0a 38 00 00 08 00
[ 2318.484818] end_request: I/O error, dev sda, sector 109054520
[ 2318.484833] Buffer I/O error on device sda1, logical block 13631559
[ 2318.484844] lost page write due to I/O error on sda1
[ 2318.484902] ata1: EH complete
[ 2318.484957] JBD: recovery failed
[ 2318.484967] EXT4-fs (sda1): error loading journal

```

---

### Post by owiknowi on 2011-06-24
as a last resort you could try a data recovery program like ontrack or something similar.

also take a look at [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

meanwhile i'll search a bit more for you on how we can best proceed i.m.h.o.

first of all: don't change anything to your hdd with your files at this moment!

---

### Post by Bachstelze on 2011-06-24
> **owiknowi said:**
> as a last resort you could try a data recovery program like ontrack or something similar.

also take a look at [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

meanwhile i'll search a bit more for you on how we can best proceed i.m.h.o.

first of all: don't change anything to your hdd with your files at this moment!

Wow, not too fast!

@Noirtheater: try a filesystem check

```
sudo fsck /dev/sda1
```

---

### Post by Noirtheater on 2011-06-24
> **owiknowi said:**
> as a last resort you could try a data recovery program like ontrack or something similar.

also take a look at [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

meanwhile i'll search a bit more for you on how we can best proceed i.m.h.o.

first of all: don't change anything to your hdd with your files at this moment!

Thanks for the link! I'll try all the instructions in there right now, and post the results. :)

---

### Post by owiknowi on 2011-06-24
as i understand it you've got 3 drives (sda, sdb and sdc)?
if your files are stored on sda (boot / system partition) we don't have to look at the other drives for now.

@Bachstelze: sorry, i'll hold my horses

---

### Post by Noirtheater on 2011-06-24
> **Bachstelze said:**
> Wow, not too fast!

@Noirtheater: try a filesystem check

```
sudo fsck /dev/sda1
```

I just tried that, and it said the following:

```
fsck desde util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero lenght partition?
```

---

### Post by e79 on 2011-06-24
```
[ 2318.484699] 72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00  [ 2318.484741]         06 80 0a 38  [ 2318.484759] sd 0:0:1:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed [ 2318.484780] sd 0:0:1:0: [sda] CDB: Write(10): 2a 00 06 80 0a 38 00 00 08 00 [ 2318.484818] end_request: I/O error, dev sda, sector 109054520 [ 2318.484833] Buffer I/O error on device sda1, logical block 13631559 [ 2318.484844] lost page write due to I/O error on sda1 [ 2318.484902] ata1: EH complete [ 2318.484957] JBD: recovery failed [ 2318.484967] EXT4-fs (sda1): error loading journal 
```I'd suggest the filesystem check as Bachstelze recommended, you seem to have some bad blocks/sectors on your disk and the information could not be reallocated somewhere else...

EDIT : I posted this a little late sry

EDIT 2 :  The only time I saw this error is when the disk was dieing....not looking good...

---

### Post by Noirtheater on 2011-06-24
> **owiknowi said:**
> as i understand it you've got 3 drives (sda, sdb and sdc)?
if your files are stored on sda (boot / system partition) we don't have to look at the other drives for now.

Yep, /sda1 is the boot/system partition and that's where my files are stored. The other two drives are an extra 4GB drive my lappy came with (It's an Asus Eee PC 901 that came with both a 16GB SSD drive and another 4GB one... I replaced the 16GB one with a 64GB one last year), which I don't really use for anything, and the other one I'm guessing that it's the 16GB SD card I have inserted in it right now.

---

### Post by owiknowi on 2011-06-24
@ everyone helping:

in the first post i see: Unknown Bootloader on sda2.
shouldn't the bootloader be installed on sda1 since there's only one os and sda1 is the boot / system partition?

disk is 64Gb with 3 partitions: sda1 (boot flag), sda 2 and sda5 (swap).

---

### Post by Noirtheater on 2011-06-24
> **e79 said:**
> ```
[ 2318.484699] 72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00  [ 2318.484741]         06 80 0a 38  [ 2318.484759] sd 0:0:1:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed [ 2318.484780] sd 0:0:1:0: [sda] CDB: Write(10): 2a 00 06 80 0a 38 00 00 08 00 [ 2318.484818] end_request: I/O error, dev sda, sector 109054520 [ 2318.484833] Buffer I/O error on device sda1, logical block 13631559 [ 2318.484844] lost page write due to I/O error on sda1 [ 2318.484902] ata1: EH complete [ 2318.484957] JBD: recovery failed [ 2318.484967] EXT4-fs (sda1): error loading journal 
```I'd suggest the filesystem check as Bachstelze recommended, you seem to have some bad blocks/sectors on your disk and the information could not be reallocated somewhere else...

EDIT : I posted this a little late sry

EDIT 2 :  The only time I saw this error is when the disk was dieing....not looking good...

I'm not sure about drive dying part since it's kinda new (I bought it back in Christmas, a 64GB SSD drive). I think the problem comes from a botched update attempt last night. The update manager said that some files were missing after it downloaded all the stuff and, silly me, I clicked "Proceed" anyways. I have done so in the past and I never had a problem with it, but I guess it wasn't a very clever move on my part anyways. :/

---

### Post by oldfred on 2011-06-24
I see you ran fsck, but I still would try this:

#From liveCD so everything is unmounted,swap off if necessary, change sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors:
sudo e2fsck -f -y -v /dev/sda1

---

### Post by Noirtheater on 2011-06-24
> **oldfred said:**
> I see you ran fsck, but I still would try this:

#From liveCD so everything is unmounted,swap off if necessary, change sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors:
sudo e2fsck -f -y -v /dev/sda1

I tried those two commands already, but I got the same answer as [the one I posted here]("http://ubuntuforums.org/showpost.php?p=10976391&postcount=17"). :/

---

### Post by owiknowi on 2011-06-24
tip:
also take a look on the website of the ssd manufacturer, maybe you'll find useful information there too.
some even have (free) data recovery software for their disks.

---

### Post by oldfred on 2011-06-24
You can also try alternative superblocks.

Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda1 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda1
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

### Post by Noirtheater on 2011-06-25
Good news! After performing a Deeper Search using testdisk while running Ubuntu Live CD, I realized that there was an option (pressing "P") that allowed me to list the files into the "deep searched" drive, and my files are copying to an external USB drive at the moment. :D

As soon as all the files are safely stored and I have checked that no one is missing and that they are working correctly, I'll mark this post as [SOLVED].

Thank you thank you thank you very much to you all guys for all the helpful tips and links! Not to be dramatic here, but you have most probably saved me from losing my job! :)

[EDIT] Yep, all the files were intact! Yay for boss not kicking my lower backside! :D

---

### Post by owiknowi on 2011-06-25
congratulations and thank you!

if your files are save and properly working it is probably time to take a look at the ssd.
just if your interested here's a method i use when a disk gives me trouble (stop reading if you can do without).

1. with killdisk ([http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm)) i write zero's to the entire disk, starting at sector 0 (mbr a.o.). if this goes without a problem nor error messages i'll bet the disk is ok.

2. if the latter is the case i use gparted or partmagic to setup the disk:
first set the disklabel to msdos (in my case) then partition it to your needs (dont forget to set the boot flag to a primary / bootable partition).

example: sda1: xxGB for / (with boot flag); sda2: 4GB linux swap; sda3: rest GB.
sda1 and sda3 format as ext3 or ext4.

3. installing the os is next:
sda1 becomes /
sda2 becomes swap
sda3 becomes /home

in this set up you can install the boot loader to the MBR.

if the disk shows a lot of errors whilst using killdisk you could contact the manufacturer.
if there is a structural problem with a certain series of disks, chances are they'll send you a new one.

for regular back ups of my personal files i use an external 2.5" hdd.

glad it turned out this way for you and please feel free to ask if you have any further questions.

---

### Post by Noirtheater on 2011-06-25
> **owiknowi said:**
> congratulations and thank you!

if your files are save and properly working it is probably time to take a look at the ssd.
just if your interested here's a method i use when a disk gives me trouble (stop reading if you can do without).

1. with killdisk ([http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm)) i write zero's to the entire disk, starting at sector 0 (mbr a.o.). if this goes without a problem nor error messages i'll bet the disk is ok.

2. if the latter is the case i use gparted or partmagic to setup the disk:
first set the disklabel to msdos (in my case) then partition it to your needs (dont forget to set the boot flag to a primary / bootable partition).

example: sda1: xxGB for / (with boot flag); sda2: 4GB linux swap; sda3: rest GB.
sda1 and sda3 format as ext3 or ext4.

3. installing the os is next:
sda1 becomes /
sda2 becomes swap
sda3 becomes /home

in this set up you can install the boot loader to the MBR.

if the disk shows a lot of errors whilst using killdisk you could contact the manufacturer.
if there is a structural problem with a certain series of disks, chances are they'll send you a new one.

for regular back ups of my personal files i use an external 2.5" hdd.

glad it turned out this way for you and please feel free to ask if you have any further questions.

I just finished testing my SSD with Killdisk (not a single error... phew!) and I'm going to do the partitioning and reinstalling tonight.

Thank you very much for the extra tips, owiknowi! :D

---


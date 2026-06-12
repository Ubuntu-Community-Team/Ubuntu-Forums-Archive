---
title: "ubuntu fsck scans"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by scotcella on 2009-07-20
As I understand it, Ubuntu fsck runs approximately every 35 boots. Now everytime I ubuntu runs it, it fails and tells me there are hardware issues and I need to press CTRL D and it runs again and logs into ubuntu as normal.

How do I fix the bad sector?

Many thanks in advance.

---

### Post by marcopalla on 2009-07-20
boot from the CD (is not possible to check a mounted filesystem)

then try:

>fdisk -l
(to have your partitions and disk list)

then:

fsck -t ext3  -V -r /dev/hda

/dev/hda = the partition you want check, you know from fdisk command
-t ext3 = if is your type of filesystem ext2 or ext4 or something else could be
-A = all filesystem
-V = say to me every information while you do it
-r = ask me what to do if you find an error

---

### Post by scotcella on 2009-07-20
Hi there,

I tried following your advice, I loaded the live cd on my laptop and brought up the terminal to have a look at my partitions and disk list...  I put in

```
sudo fdisk -l
```

and the output of this was (The first two is the Vista Partition and the rest is the Ubuntu 9.04 partition)

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3e211c4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1184     9503744   27  Unknown
/dev/sda2   *        1185       12657    92156872+   7  HPFS/NTFS
/dev/sda3           12658       19457    54621000    5  Extended
/dev/sda5           12658       19173    52339738+  83  Linux
/dev/sda6           19174       19457     2281198+  82  Linux swap / Solaris
```

I am not sure what to make of the next command you suggested, nothing came up so I amended it to:
```

sudo fsck -t ext3 -V -r /dev/sda3
```

Output was: (sda3)

```
fsck 1.41.4 (27-Jan-2009)
[/sbin/fsck.ext3 (1) -- /dev/sda3] fsck.ext3 -r /dev/sda3 
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext3: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda3
Could this be a zero-length partition?
```


```
sudo fsck -t ext3 -V -r /dev/sda5
```

Output was: (sda5)

```
fsck 1.41.4 (27-Jan-2009)
[/sbin/fsck.ext3 (1) -- /dev/sda5] fsck.ext3 -r /dev/sda5 
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda5: clean, 142669/3276800 files, 1095974/13084934 blocks
```


```
sudo fsck -t ext3 -V -r /dev/sda6
```

Output was: (sda6)
```

fsck 1.41.4 (27-Jan-2009)
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda6
```



I am not sure where to go next, any advice would be great!!
Thanks in advance!

---

### Post by SunnyRabbiera on 2009-07-20
Did it come up with a corrupted files list?
You can do a filesystem check with Gparted on your ubuntu installer CD, just be careful and back up if possible.

---

### Post by scotcella on 2009-07-21
Yes I have everything backed up, so it's not a problem.

How do i do a filesystem check?

---

### Post by shazbut on 2009-07-21
In your original post you said fsck said there may be a hardware issue.  If that's the case the best course would be to test the drive itself, rather than the filesystem.  Run the apropriate tool for your HDD manufacturer on the drive (eg Western Digital has DLGDiag, Seagate has Seatools, etc), sometimes the tools are able to reallocate bad sectors.
A good source for these tools is the Ultimate Boot CD.
There's no point trying to fix the file system on a drive with unrecoverable bad sectors, providing you have a good backup.

---

### Post by scotcella on 2009-07-21
I have no idea what type of HDD I have, or how to go about doing this? 

Could you please give me some advice?

---

### Post by mcduck on 2009-07-21
All those fsck runs are fine, no problem there. 

Checking sda3 failed because it's extended partition and as such doesn't contain a filesystem (what it contains are your two logical paritions, sda5 and sda6).

..and checking sda6 failed because it's a swap partition, and once again doesn't contain anything that you could check.

NOw, without having the actual error you get from fsck when booting, my guess would be that the actual problem is eithet that fsck is trying to check your windows partiton, or that you have at some point edited or formatted  on of your partitions, which has changed that partitions UUID. But your /etc/fstab still has the old UUID and as a result fsck tries to find a partititon that doesn't exist.

Could you run "blkid" and post the output & contents of your /etc/fstab here?

---

### Post by scotcella on 2009-07-21
HI there,

Thanks for your help, 

Output for blkid:
```

/dev/sda5: UUID="80aa83d3-8419-4f25-9433-83a6757dd483" SEC_TYPE="ext2" TYPE="ext3" 
```

Outpost for /etc/fstab: 
```

bash: /etc/fstab: Permission denied
```

:)

Just so you know I am using the LIVE CD at the moment, do you need me to do this on my laptop rather the LIVE CD?

---

### Post by shazbut on 2009-07-21
> **scotcella said:**
> I have no idea what type of HDD I have, or how to go about doing this? 

Could you please give me some advice?

That's the tricky bit, I don't know how from within Linux (anyone else know?).  Normally I get it from the BIOS messages at startup, or from within the BIOS Setup utility.  What messages are shown, and the key to access the setup depend on the computer manufacturer.  Tier 1 vendors like HP and Dell tend to hide such messages from the user.  Possibly F2 on Dells, F10 on HP.  Also DEL on white boxes with Award bios, F2 for for Phoenix bios.

edit: maybe
```
lshal | grep storage_device
```

---

### Post by scotcella on 2009-07-21
> **shazbut said:**
> That's the tricky bit, I don't know how from within Linux (anyone else know?).  Normally I get it from the BIOS messages at startup, or from within the BIOS Setup utility.  What messages are shown, and the key to access the setup depend on the computer manufacturer.  Tier 1 vendors like HP and Dell tend to hide such messages from the user.  Possibly F2 on Dells, F10 on HP.  Also DEL on white boxes with Award bios, F2 for for Phoenix bios.

edit: maybe
```
lshal | grep storage_device
```

I have a Sony Vaio VGN CR25G

---

### Post by mcduck on 2009-07-21
> **scotcella said:**
> HI there,

Thanks for your help, 

Output for blkid:
```

/dev/sda5: UUID="80aa83d3-8419-4f25-9433-83a6757dd483" SEC_TYPE="ext2" TYPE="ext3" 
```

Outpost for /etc/fstab: 
```

bash: /etc/fstab: Permission denied
```

:)

Just so you know I am using the LIVE CD at the moment, do you need me to do this on my laptop rather the LIVE CD?

Is that all blkid reported? in that case try "sudo blkid" or "ls /dev/disk/by_uuid", you should get UUID's for all your partititons..

And /etc/fstab is a file, not a command. Just open the file with any text editor you like and post the contents here.. (or run "cat /etc/fstab" and post the output).

You should run the commands from the installed system, that's what we are trying to fix, not the live-CD. :)

---

### Post by scotcella on 2009-07-21
Thanks McDuck,

Okay, now I am using my installed system..

the output for  blkid:
```

ella@ella-laptop:~$ blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="48BEDEC1BEDEA72A" LABEL="Recovery" TYPE="ntfs" 
/dev/sda2: UUID="A04239D94239B53E" TYPE="ntfs" 
/dev/sda5: UUID="80aa83d3-8419-4f25-9433-83a6757dd483" TYPE="ext3" 
/dev/sda6: UUID="2011cc8f-b23f-406b-ab74-90f9366e4efc" TYPE="swap"
``` 

Output for cat /etc/fstab:

```
ella@ella-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=80aa83d3-8419-4f25-9433-83a6757dd483 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2011cc8f-b23f-406b-ab74-90f9366e4efc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by mcduck on 2009-07-21
> **scotcella said:**
> Thanks McDuck,

Okay, now I am using my installed system..

the output for  blkid:
```

ella@ella-laptop:~$ blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="48BEDEC1BEDEA72A" LABEL="Recovery" TYPE="ntfs" 
/dev/sda2: UUID="A04239D94239B53E" TYPE="ntfs" 
/dev/sda5: UUID="80aa83d3-8419-4f25-9433-83a6757dd483" TYPE="ext3" 
/dev/sda6: UUID="2011cc8f-b23f-406b-ab74-90f9366e4efc" TYPE="swap"
``` 

Output for cat /etc/fstab:

```
ella@ella-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=80aa83d3-8419-4f25-9433-83a6757dd483 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2011cc8f-b23f-406b-ab74-90f9366e4efc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
Ok, your fstab seems to be OK, the UUID's for your root and swap are correct and the other two partitions aren't mounted.

Then it could really be a hardware problem, although it's still hard to say unless you're able to post the exact error message here. Even knowing if the error is about a disk, partition or filesystem and which one would help a lot. :D

---

### Post by scotcella on 2009-07-21
THanks Mcduck

I restarted my laptop to check the error, did this 3 times as it was really quick,

the warning comes up as "there might be a hardware problem, most likely to be your PCI Bus".

What does this mean?

THanks in advance

---

### Post by marcopalla on 2009-07-21
> **scotcella said:**
> Hi there,

I tried following your advice, I loaded the live cd on my laptop and brought up the terminal to have a look at my partitions and disk list...  I put in

```
sudo fdisk -l
```and the output of this was (The first two is the Vista Partition and the rest is the Ubuntu 9.04 partition)

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3e211c4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1184     9503744   27  Unknown
/dev/sda2   *        1185       12657    92156872+   7  HPFS/NTFS
/dev/sda3           12658       19457    54621000    5  Extended
/dev/sda5           12658       19173    52339738+  83  Linux
/dev/sda6           19174       19457     2281198+  82  Linux swap / Solaris
```I am not sure what to make of the next command you suggested, nothing came up so I amended it to:
```

sudo fsck -t ext3 -V -r /dev/sda3
```Output was: (sda3)

```
fsck 1.41.4 (27-Jan-2009)
[/sbin/fsck.ext3 (1) -- /dev/sda3] fsck.ext3 -r /dev/sda3 
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext3: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda3
Could this be a zero-length partition?
``````
sudo fsck -t ext3 -V -r /dev/sda5
```Output was: (sda5)

```
fsck 1.41.4 (27-Jan-2009)
[/sbin/fsck.ext3 (1) -- /dev/sda5] fsck.ext3 -r /dev/sda5 
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda5: clean, 142669/3276800 files, 1095974/13084934 blocks
``````
sudo fsck -t ext3 -V -r /dev/sda6
```Output was: (sda6)
```

fsck 1.41.4 (27-Jan-2009)
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda6
```I am not sure where to go next, any advice would be great!!
Thanks in advance!

Ok on your file system seems to be all OK

bad blocks are always a bad problems,
if is a soft bad sector you could solve,
if is an harware bad sector (a real scratch) is quite impossible

1° try with the utility of the manufact of your HD 
if you don't know try 
hdparm -I /dev/sda
it could be print  details of HD (only if some conditions are satisfied)
see the model and google

then a more drastic solution is reformat everything, in that case bad blocks would be excluded (the line command is mkfs -c but I think grub does it automatically?)

hope that could be help

---

### Post by scotcella on 2009-07-21
Yeah I did, I reinstalled a fresh copy of 9.04 and the the warning crops up on shut down says that the problem might to be the PCI Bus.

Thanks for your post, I appreicate it.

---


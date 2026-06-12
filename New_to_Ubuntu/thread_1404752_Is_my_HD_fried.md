---
title: "Is my HD fried?"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by TadeoDiaz on 2010-02-11
My computer was working fine (Lenovo 3000 V100 with the latest version of Ubuntu) and suddenly I can't seem to start into Ubuntu. When I go into recovery mode it waits for root device and then gives me the "Gave up waiting for root device"

I did the googling and followed all the advice:
1.Tried changing the rootdelay=90 and even "any" under recovery mode
2.Tried booting into USB drive with Ubuntu and loading the partition (sda1) to try to change the file menu.lst (per ubuntu thread)
3.Tried to mount sda1 to recover data to no avail, I tried:

```
sudo mount -t ext3 /dev/sda1 /home/ubuntu/Desktop
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ dmesg | tail
[   68.269021] [drm] TV-15: set mode NTSC 480i 0
[   76.728074] wlan0: authenticate with AP 00:13:46:19:ee:6a
[   76.729847] wlan0: authenticated
[   76.729851] wlan0: associate with AP 00:13:46:19:ee:6a
[   76.732280] wlan0: RX AssocResp from 00:13:46:19:ee:6a (capab=0x431 status=0 aid=140)
[   76.732284] wlan0: associated
[   76.734182] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   87.556031] wlan0: no IPv6 routers present
[  473.649087] CE: hpet increasing min_delta_ns to 15000 nsec
[  548.143786] EXT3-fs: sda1: couldn't mount because of unsupported optional features (240).

```

It's no biggie if my HD is fried I would just like to know so that I can stop putting in so much time into trying to figure it out. 

I appreciate and thank anyone in advanced for their help, this has been quite frustrating.

---

### Post by samantha_ on 2010-02-11
have you tried
```

sudo fsck -y /dev/sda1
```?

or testdisk?

---

### Post by audiomick on 2010-02-11
Samantha always seems to know what she is talking about, so do what she says.

You could also try running smartmontools on it.
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
That reads out the info that the drive has stored about itself.

---

### Post by The Real Dave on 2010-02-11
Could it be a bad superblock? Try running 
```
sudo fsck -v /dev/xxx
```
to check the filesystem for errors.

If that says its a superblock error, you can use this

```
sudo mke2fs -n /dev/xxx
```
to find where the superblock backups are and finally

```
sudo e2fsck -b block number /dev/xxx
```
to restore from one of the backups.

Its what I use, on ext4. Should be the same for ext3 I presume, but someone stop me please if I'm wrong :)

---

### Post by TadeoDiaz on 2010-02-11
> **samantha_ said:**
> have you tried
```

sudo fsck -y /dev/sda1
```?

or testdisk?

I tried that and it gives me:

```
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda1: clean, 281729/5857280 files, 10623000/23416737 blocks

```

I also recently tried booting into Partition Magic but could not access the sda1 partition (at least it was showing on the desktop though).

Running sudo mke2fs -n /dev/sda1 give me:

```
mke2fs 1.41.9 (22-Aug-2009)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
5857280 inodes, 23416737 blocks
1170836 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
715 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000
```

I have no clue what the above means, is there a bad block? Any other thoughts? Thanks again for your help!

---

### Post by audiomick on 2010-02-11
This looks good
```
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda1: [COLOR=Red]clean[/COLOR], 281729/5857280 files, 10623000/23416737 blocks
```although I am not an expert with that. I think that it tells you if it finds something it doesn't like.

I would still be inclined to run smartmontools on it. You can do that from the live CD if you can't boot into the system properly.

---

### Post by samantha_ on 2010-02-11
I just had an idea spark/flashback
OS X is based on BSD., which is similar to linux.

I had some corrupted SATA/Filesystem drivers once after it kernel paniced and I had to do a hard shutdown.

I ended up with the same error.
I tried disk repair. Disk repair said everything was fine.
I never solved it, I backed up everything and reinstalled.
Later, I looked around (I had really needed my macbook at that time, so i was desperate to get it running ASAP)
[s]and found that that error was caused by bad chipset/filesystem drivers.[/s]
and it turned out to be that the SATA/Chipset drivers were corrupted. (it happenend another time w/ the laptop in my sig after I installed some bad video drivers. and did a hard reset.)

Perhaps [s]try installing the drivers for your chipset/filesystem through the livecd?[/s]
copying the kernel and its modules from the livecd to the ubuntu partition?
wait.
I got a better idea.
Do you have any other kernels that are installed on ubuntu?

---

### Post by TadeoDiaz on 2010-02-11
> **audiomick said:**
> Samantha always seems to know what she is talking about, so do what she says.

You could also try running smartmontools on it.
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
That reads out the info that the drive has stored about itself.

I ran the short test on Smartmontools (Im going out of town until Sunday early tomorrow and I won't be taking my laptop) and this is what I got:

```
sudo smartctl -l selftest /dev/sda1
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      3489         -
# 2  Short offline       Completed without error       00%       458         -
# 3  Short offline       Completed without error       00%        11         -
```

[QUOTE=samantha_]Re: Is my HD fried?
I just had an idea spark/flashback
OS X is based on BSD., which is similar to linux.

I had some corrupted SATA/Filesystem drivers once after it kernel paniced and I had to do a hard shutdown.

I ended up with the same error.
I tried disk repair. Disk repair said everything was fine.
I never solved it, I backed up everything and reinstalled.
Later, I looked around (I had really needed my macbook at that time, so i was desperate to get it running ASAP)
and found that that error was caused by bad chipset/filesystem drivers.
and it turned out to be that the SATA/Chipset drivers were corrupted. (it happenend another time w/ the laptop in my sig after I installed some bad video drivers. and did a hard reset.)

Perhaps try installing the drivers for your chipset/filesystem through the livecd?
copying the kernel and its modules from the livecd to the ubuntu partition?
wait.
I got a better idea.
Do you have any other kernels that are installed on ubuntu? [/QUOTE]

I have several other kernel versions in the grub. I tried booting into one of them without success, just got the same screen than with the most current kernel. I haven't changed anything drastically in the last week or so (not even updates, at least that I can remember)

---

### Post by audiomick on 2010-02-12
Ok, so the short test looks good. You might still want to run the extended just to be sure.

The next thing would be to run meierfra's boot info script to look at your boot setup. There is a nice explanation here:
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
have a look at the output and see if you can make sense of it, and post it back here (in code tags, the # button. It is a long bit of text.) so we can have a look at it.

I don't actually expect to see anything wrong there, but it is never a bad idea to exclude possibilities, so it can't hurt and might divulge more info.

I just went back over the thread. The behaviour you describe is a bit odd. You can run disk checks, but not mount the drive. That means the computer can see the drive as such, it just can't talk to it.

In the output in your first post, there is this
```
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, [COLOR=Red]or othe[/COLOR]r error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```so bad blocks is only a possibility
and then at the end
```
[  548.143786] EXT3-fs: sda1: couldn't mount because of unsupported optional features (240).
```
so the trick is to find out what the "unsupported optional features" are that have "suddenly" appeared.

---

### Post by skymera on 2010-02-12
> **TadeoDiaz said:**
> 
```

[  548.143786] EXT3-fs: sda1: couldn't mount because of unsupported optional features (240).

```


Have you manually edited your /etc/fstab file recently? or GRUB?

---

### Post by audiomick on 2010-02-12
Ah, someone else thinking along the same lines...
I guess the OP wont be back till Monday, said he was going away. I will subscribe this thread and look back in next week. I am curious about this...

---

### Post by TadeoDiaz on 2010-02-14
Ok, just got back in town. I am currently running the extended test as we speak.

> **skymera said:**
> Have you manually edited your /etc/fstab file recently? or GRUB?

I have never messed with the /etc/fstab or the GRUB on my laptop (I do a clean install with each new release)

> **audiomick said:**
> Ok, so the short test looks good. You might still want to run the extended just to be sure.

The next thing would be to run meierfra's boot info script to look at your boot setup. There is a nice explanation here:
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
have a look at the output and see if you can make sense of it, and post it back here (in code tags, the # button. It is a long bit of text.) so we can have a look at it.

I don't actually expect to see anything wrong there, but it is never a bad idea to exclude possibilities, so it can't hurt and might divulge more info.

I just went back over the thread. The behaviour you describe is a bit odd. You can run disk checks, but not mount the drive. That means the computer can see the drive as such, it just can't talk to it.

In the output in your first post, there is this
```
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, [COLOR=Red]or othe[/COLOR]r error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```so bad blocks is only a possibility
and then at the end
```
[  548.143786] EXT3-fs: sda1: couldn't mount because of unsupported optional features (240).
```
so the trick is to find out what the "unsupported optional features" are that have "suddenly" appeared.

That's what surprised me, i turned on my laptop in the morning before leaving to check email and shut it down as I usually do as I leave (didn't open anything but google chrome). Then when I got home in the afternoon the computer just goes into the grub on startup without being able to go into ubuntu

Thanks for following everyone, i will post the results of the extended  test soon.

---

### Post by audiomick on 2010-02-14
Hi. Glad I caught your post, I am about to go to bed.
I'll be interested to see what the test shows, but I have a suspicion that there wont be a problem.

---

### Post by TadeoDiaz on 2010-02-14
Ok here are the results of the long test:

```
sudo smartctl -l selftest /dev/sda1
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      3490         -
# 2  Short offline       Completed without error       00%      3489         -
# 3  Short offline       Completed without error       00%       458         -
# 4  Short offline       Completed without error       00%        11         -

```

and the results of meierfra's boot info script are:

```
                    Boot Info Script 0.54 of  February 14th, 2010                         

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   187,333,964   187,333,902  83 Linux
/dev/sda2         187,333,965   195,366,464     8,032,500   5 Extended
/dev/sda5         187,334,028   195,366,464     8,032,437  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1027 MB, 1027416576 bytes
232 heads, 60 sectors/track, 144 cylinders, total 2006673 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000f1395

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *              1     2,006,672     2,006,672   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       6474ce91-57a0-45fd-acd4-ae13d791305c   ext3                                     
/dev/sda1: ambivalent result (probably more filesystems on the device)
/dev/sda5        15c9b8b6-4fcc-4fd4-a385-7eaa712950e4   swap                                     
/dev/sdb1        931E-C4FF                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)

```

I wish I could interpret the above, but it doesn't look like there is anything wrong (at least from my very limited experience). Thanks again for your help audiomick, at this point Im kind of trying to figure out if it's worth continuing the search for what is wrong or if it's better to cut the losses and move on. However, I don't know if I should be buying another hard drive or if this is due to some other problem needing me to just buy a new laptop. Any ideas?

---

### Post by sailthesea on 2010-02-14
Your HD is fine 
There seems to be a problem with grub It says Grub2 is looking for partition1 which is not recognised 
 You need to fix grub

---

### Post by TadeoDiaz on 2010-02-14
> **sailthesea said:**
> Your HD is fine 
There seems to be a problem with grub It says Grub2 is looking for partition1 which is not recognised 
 You need to fix grub

That would be awesome! But, how do I go about fixing the grub? (kind of a beginner here)

---

### Post by thatguruguy on 2010-02-14
FWIW, my sister's computer recently was having a hard time booting. It would start grub, and then completely reboot.  I finally ran a memory test from the grub menu, and the memory test started showing lots of errors.

I removed one of the memory chips (she was running 2 gigs, with 2 chips of 1 gig each), and she was then able to boot normally.  I've since replaced that chip, and her computer works fine.

I guess what I'm saying here is, run the memory test.  The problem may be there, rather than a problem with your hard drive.

---

### Post by audiomick on 2010-02-15
Hallo.

First of all, the Guru Guy's advice is principally good, but I don't think that there is a RAM problem in this case.

I also don't think that just re-installing Grub is going to solve your problem.

I should add at this point that I am offering my considered opinion, which is not to be confused with really expert advice...;)

Your HD looks like it is OK, at least as far as the checking mechanisms can determine. The smartmontools utility looks, as I understand it, at the physical condition of the drive. It reports back good.
```
=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      3490         -
# 2  Short offline       Completed without error       00%      3489         -
# 3  Short offline       Completed without error       00%       458         -
# 4  Short offline       Completed without error       00%        11         -
```"fsck" looks at the file system, and it also reported back clean, so I don't think there is anything physically wrong with the drive.

The problem seems to be that, whilst the partition sda1 is still there, it's contents can't be read. Also, grub is still there, but what it is trying to read in sda1 is not there or can't be read.
```
                    Boot Info Script 0.54 of  February 14th, 2010                         

============================= Boot Info Summary: ==============================

 =>[COLOR=Red] Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.[/COLOR]
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
[COLOR=Red]mount: unknown filesystem type ''[/COLOR]
```A couple of things occur to me that need to be clear. If your install was a fresh install of 9.10:
Your grub will be grub2, not the older grub legacy that was used up until 9.04. The boot script reports the presence of grub2, so I think if was a fresh install, not an update from a previous Ubuntu version. This also means that you would not have found the file menu.lst. This is no longer used by grub2.
There is info on re-installing and editing grub2 here
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

On a fresh install of 9.10, unless you specified otherwise during the installation, the file system is ext4, not ext3. The mount command that you quoted
```
sudo mount -t ext3 /dev/sda1 /home/ubuntu/Desktop
```specifies ext3, so I don't think it could work, even if the partition were intact. If you want to try it again, leave out the "ext3" or replace it with "ext4", but I think it still wont work. See the man page```
man mount
```for details

One option would be to start looking in the direction of data recovery. You can read about that here
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Another option would be to re-install Ubuntu to the same partition it was in. This would mean that any data in that partition would be irretrievably lost. If you choose the "manual partitioning" option during the install, you can specify exactly where Ubuntu installs to. If you choose to do this, I would strongly recommend creating a separate /home partition while you are at it. This allows you, in situations like this, to simply re-mount the /home partition during a new install and retain all your data and user settings.

What I would try at this point, and I will say once again that I can't guarantee that it will work, is the command that the Real Dave suggested:
```
sudo e2fsck -b block number /dev/xxx
```I have read through the man page for this command, and it looks like it is appropriate. Please have a look at it yourself
```
man e2fsck
```You need to specify the superblock you want it to look at for the backup, and the partition it is to work on.

From here
> Running sudo mke2fs -n /dev/sda1 give me:you could take the first number at the end of the output and try that.
```
Superblock backups stored on blocks: 
    [COLOR=Red]32768[/COLOR], 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000
```which would give you this command```
sudo e2fsck -b 32768 /dev/sda1
```As you can see in the man page, it is not safe to run this on a mounted file system. Since you are running from the live CD/USB, the partition shouldn't be mounted unless you have been successful with the mount command.

If "e2fsck" succeeds in making the partition mountable again, you will possibly still have to re-install grub. The second problem that is visible in the boot script output is this
```
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       6474ce91-57a0-45fd-acd4-ae13d791305c   ext3                                     
[COLOR=Red]/dev/sda1: ambivalent result (probably more filesystems on the device)[/COLOR]
/dev/sda5        15c9b8b6-4fcc-4fd4-a385-7eaa712950e4   swap                                     
/dev/sdb1        931E-C4FF                              vfat
```the UUID for the partition is gone, and grub needs that to find it during boot. I don't know if saving the partition will bring that back, but I have my doubts. I suspect it will acquire a new one, which means that even if the grub boot files that are supposed to be in sda1 reappear, they might be pointing at an UUID that no longer exists.
The quickest way to find out, of course, is to try and boot and see what happens.
If the attempt to retrieve the contents of sda1 is successful, the boot info script should show something like this
```
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img
```if you run it again. **note: this is the output for my computer, which has relics of a grub legacy as well as grub2. The "menu.lst" that is visible is not to be expected in your output.**
If that is the case, but you still can't boot, you might try repairing grub. See the grub2 links I posted above for this. I am a bit hazy on that, and might give you the wrong advice.

I think that is all. I hope it is of some help to you, even if only to shed a bit of light on why the machine wont boot.

The question that remains, of course, is "why did it mess up in the first place?". Assuming that you get it all back together, I would suggest being very diligent about backups, at least until you are reasonably confident that the problem was a once off, and not something that is going to pop up again.

---

### Post by meierfra. on 2010-02-16
Couple of things to try:

1)  Use the "-f" option to run a real file system check even if e2fsck thinks the file system is clean:

```
sudo e2fsk -fyv /dev/sda1
```


2)  Figure out the other file system "blkid" is complaining about:

There is a program called [wipefs ]("http://karelzak.blogspot.com/2009/11/wipefs8.html") which is able to detect the signatures  of most file systems and is also able to erase all the unwanted signatures.  Unfortunately its is very new  and  you will have to compile it from source. If you would like to give that a try, here are the instructions:

Download   [util-linux-ng-2.17.tar.gz]("ftp://ftp.kernel.org/pub/linux/utils/util-linux-ng/v2.17/util-linux-ng-2.17.tar.gz") to your Desktop.

Right click the file and choose "Extract Here"

Open a terminal.

```
cd ~/Desktop
mkdir Util
cd util-linux-ng-2.17
sudo ./configure --prefix=$HOME/Desktop/Util --without-ncurses 
sudo make
sudo make install
```

This installed the Util-Linux package to the folder Util on your desktop.
You will probably get a few error messages from "make" and "make install, but "wipefs" should still work just fine.

Next  run wipefs via

```
cd  ~/Desktop/Util/sbin
sudo ./wipefs /dev/sda1

```

 "wipefs /dev/sda1"  displays some basic information on all the file systems found on /dev/sda1,    but does  not change anything.   Post that  information.

---

### Post by TadeoDiaz on 2010-02-16
> **audiomick said:**
> 

On a fresh install of 9.10, unless you specified otherwise during the installation, the file system is ext4, not ext3. The mount command that you quoted
```
sudo mount -t ext3 /dev/sda1 /home/ubuntu/Desktop
```specifies ext3, so I don't think it could work, even if the partition were intact. If you want to try it again, leave out the "ext3" or replace it with "ext4", but I think it still wont work. See the man page```
man mount
```for details


audiomick you are a genius!!!! the line:

```
sudo mount -t ext4 /dev/sda1 /home/ubuntu/Desktop
```
WORKED!!!! I mounted the partition to the desktop. I think at this point Im going to just backup the data and move on to a fresh install. Thank you so much! I really appreciate all the time you took to explain things to me! I was about to give up and just reformat to lose all my data!

---

### Post by sailthesea on 2010-02-16
Good to see you are on the right track:)
 Kudos to mick et al for coming through on this one I have no experience of grub2 so would not have been much help!
 Now things are working I would recommend a good tidy up on your drive using what you have learned from this
 Good luck!

---

### Post by TadeoDiaz on 2010-02-16
I guess i spoke too soon. 

After making a backup of my info I did a fresh install of 9.10 from USB. It started fine at first and I changed the theme upon restart. I was trying to install the restricted-extras package with some issues so I decided to restart to see if that would help. Lo and behold upon starting up it hangs for a while and some lines come up on my screen (I was dumb and didn't write them down) which looked as if the system had run disk check. Once I restarted (holding down power button) it sends me back to the "GNU GRUB version 1.97~beta4" screen. When I choose the latest kernel (2.6.31-14-generic) ubuntu logo appears for a while, disappears and then it hangs on the following:

```
fsck from util-linux-ng 2.16
/dev/sda1: clean, 131390/5857280 files, 978652/23416737 blocks
```
 
when I choose the recovery mode it hangs at the same line with:

```
[   5.551014] Adding 4016208k swap on /dev/sda5. Priority:-1 extents:1 across:4016208k
```

I am stumped about what to do. Is this unrepairable? At this point I am happy that I was able to recover my data but I want to figure out if I should just move onto another laptop? Again thanks for all the help here.

---

### Post by audiomick on 2010-02-17
Hi.
That is a bit vague.
Given that the install is fresh at this point, I would suggest doing it again, and if you get errors, write then down...;)

---

### Post by TadeoDiaz on 2010-02-18
Ok, it took two additional clean installs but so far things are good. I've run update manager and restarted the system 5+ times without problems. Thanks again everyone for all your help! I would have lost everything without you guys!

---


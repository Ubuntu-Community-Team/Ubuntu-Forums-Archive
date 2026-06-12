---
title: "Bootloader issue"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by Matbenjen on 2011-05-27
Don't know if this should be here or in General Help, but I'm pretty novice, so will try here first! First 2 paras are back story, the meat of the problem is after that :-)

Bought a second hand computer a few months ago and tried dual booting XP and Ubuntu (10.10) - didn't work, so I just put Ubuntu on there. At the end of the install, it told me that there had been an error with the bootloader as well as some other error - however, when I restarted it, it was fine...until this week. It wouldn't boot so I tried installing 11.04 from scratch. This didn't work, so back to 10.10 I went - same thing as the first time, it said there were some errors, but on restarting it seemed fine. 

From here I tried to upgrade to 11.04  but either a) my pc isn't quick enough for 11.04 b) 11.04 is really buggy c) there's some pysical damage with my pc or d) all of the above. Probably d). Anyway, it booted fine, but there were other issues meaning I wanted 10.10 back. Sorely. 

Problem was, this time I got the same errors but it actually wouldn't boot... after BIOS stuff, I just got a black screen with a dash at the top left and no ability to type anything in. First off, I tried the process here 


[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

but got told ```
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
```Not understanding enough to use --force, and slightly puzzled that my terminal was telling me that this process was trying to install GRUB into a partition and not the MBR, when the help page said it would "install GRUB boot loader into the MBR" I thought I'd ask for help here. I've also run the boot info script ([http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)) and got 
```
    Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders, total 241254720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   235,300,863   235,298,816  83 Linux
/dev/sda2         235,302,910   241,254,399     5,951,490   5 Extended
/dev/sda5         235,302,912   241,254,399     5,951,488  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
1 heads, 63 sectors/track, 15504336 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   976,768,127   976,768,065   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        47a7d139-d769-4add-8b04-cc00c3f6871d   ext4       
/dev/sda5        37816ade-a58e-4e7f-9dca-37200638936a   swap       
/dev/sdb1        D80C8E990C8E7274                       ntfs       Expansion Drive

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/47a7d139-d769-4add-8b04-cc00c3f6871d ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=47a7d139-d769-4add-8b04-cc00c3f6871d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=37816ade-a58e-4e7f-9dca-37200638936a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  82.134300232 = 88.191033344   boot/grub/core.img                             1
 106.516601562 = 114.371330048  boot/initrd.img-2.6.35-22-generic              2
  82.132854462 = 88.189480960   boot/vmlinuz-2.6.35-22-generic                 1
 106.516601562 = 114.371330048  initrd.img                                     2
  82.132854462 = 88.189480960   vmlinuz                                        1


``` if this is any use.

Apologies for the length of the post, but wanted to include everything so far. Thanks!

---

### Post by oldfred on 2011-05-27
Drives are sda, sdb. Partitions are sda1, sda2, sdb1 etc.

You must have on the second line said to install to sda1 not sda.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda1 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda1 if not correct:
sudo fdisk -l
#confirm that linux is sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:

---

### Post by fabricator4 on 2011-05-27
>  => No boot loader is installed in the MBR of /dev/sda.

Yep, grub is definitely not installed.

How did you do the installation?  The simplest method would have been to tell the installer to use the whole drive (/dev/sda) and it would/should have set it up for you.

If you selected "manual" when it came to set up the partitions, then you would need to make sure that the grub was being installed on /dev/sda.  At the moment it looks like grub did not get installed at all. (The selector for the device to install grub is at the bottom and should be set to /dev/sda)

The instructions for installing grub2 that you linked to above should also work.  Make sure that the drive is mounted.  In my opinion it is easier to manually mount the drive because you can specify the mount point.  This avoids some of the potential for errors.

To mount /dev/sda1 manually (after booting off the LiveCD) to /mnt
```
sudo mount /dev/sda1 /mnt
```

/mnt will now have the first partition on the hard drive mounted. A shortcut to this mount point will _not_ appear on your desktop but if you do 

```
ls /mnt
```

it should list the contents of your hard drive.

You can then 
```
sudo grub-install --root-directory=/mnt /dev/sda
```

and then reboot if all looks well.

I note you also have a 500Gb HD in the system.  If you want to you can mount this as /home so that re-installs don't wipe out your data all the time.  It makes future installations and fixes a lot simpler.  Note that it would be best to backup this drive and reformat it ext4 if you want to do this.

Chris.

---

### Post by Matbenjen on 2011-05-27
Thanks for the quick replies. Still not having any luck though.

Oldfred - ran your scripts and got told that there were no errors, but this still wouldn't let me boot.

Chris - I've been trying to install it to the whole drive - you're right, it should have set it up on its own, but it doesn't want to! The 500gb drive is my external, I keep all my data there and only boot from the internal, so no important data is ever lost if I have to reinstall. Following your scripts also tells me "installation finished. No errors to report" but then won't boot. This time though, it took me to a screen mentioning Grub and saying I can hit tab for commands, which I didn't get to before.

This sounded the same as this post [http://ubuntuforums.org/showthread.php?t=1594183](http://ubuntuforums.org/showthread.php?t=1594183) , so I've also tried following the advice given there (a link to  [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)).

But when I get to entering ```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
```

it tells me ```
mount: mount point /mnt/temp/dev does not exist
mount: mount point /mnt/temp/dev/pts does not exist
mount: mount point /mnt/temp/proc does not exist
mount: mount point /mnt/temp/sys does not exist
```

and I can get no further.

Any further help would be greatly appreciated, but I won't be able to follow it up until after the weekend as I'm away for a few days. Thanks.

---

### Post by oldfred on 2011-05-27
You are also missing grub.cfg. That is why grub2 stops as it needs to load that. Do you get a grub> or grub rescue prompt.

You should be able to manually boot.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

Otherwise you do need to do the full chroot method and reinstall grub2 as part of the chroot to create a grub.cfg menu file.

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Adjust drive, partition to your install:
sh:grub>ls
#If on (hd0,1) or sda1
sh:grub>ls (hd0,1)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd0,1)/vmlinuz root=/dev/sda1
sh:grub>initrd (hd0,1)/initrd.img
sh:grub>boot

---

### Post by fabricator4 on 2011-05-28
> **Matbenjen said:**
> Thanks for the quick replies. Still not having any luck though.> 

You're getting closer.  It sounds like grub is now installed, but needs to be configured.  Just to be sure, you have installed 10.10 this time around, yes?  It makes a small difference with the configuration files.

[quote]
Chris - I've been trying to install it to the whole drive - you're right, it should have set it up on its own, but it doesn't want to! 


Odd.  The 10.10 installer has seemed to cause a few problems for some people, but I'm not aware of any problems in the "use entire drive" set up.  To my recollection I've only ever run manual partition installs with the 10.10 LiveCD.

[quote]
The 500gb drive is my external, I keep all my data there and only boot from the internal, so no important data is ever lost if I have to reinstall.

The advantage of having a separate /home partition is that keeps not only your data on a separate partition, but all of your personal configuration files as well.  This can save a lot of time configuring the desktop environment and applications after a re-install.  You can do the same thing but a bit more work if you backup all the hidden files and directories in /home and then re-install later.  A separate /home partition also works seamlessly with the file system; /home and therefore /home/username are part of the filesystem, but actually exist on a completely different partition or hard drive.

> But when I get to entering ```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
```

it tells me ```
mount: mount point /mnt/temp/dev does not exist
mount: mount point /mnt/temp/dev/pts does not exist
mount: mount point /mnt/temp/proc does not exist
mount: mount point /mnt/temp/sys does not exist
```

and I can get no further.


Interesting.  As far as I know it _shouldn't_ work because when you use the 'mount' command the directory are trying to use must already work.  If you make all those directories with the following lines:

```
sudo mkdir -p /mnt/temp/dev/pts
sudo mkdir /mnt/temp/proc
sudo mkdir /mnt/temp/sys

```

then it should be fine to execute the mount loop:

```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
```


I'm trying to see where drs305 was going with these instructions, and basically it is chrooting to reinstall/configuring grub.

I agree with oldfred, I don't think you need to re-install grub2 again, just configure it.

Chris.

---

### Post by Matbenjen on 2011-05-31
Sorted! Thanks to both of you for taking the time to give advice - when I have issues with Ubuntu it's people like you who make me stick with it and try to learn something new rather than give up and move to a different OS.

For anyone else that reads this with a similar problem, in answer to oldfreds question,  I was stuck at Grub> not Grub Rescue, and in answer to fabricator4's,  I do indeed have 10.10 installed.

Before hitting on the solution, I also tried the Boot Repair GUI at [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) but got an error message. I then tried the full chroot walkthrough on the same page, this time adding in the extra lines above, suggested by fabricator4, and presto! One thing I did notice though, was that I would often get different errors at different points in the process - once I'd noticed this,  rebooting and trying again from scratch any time I got something unexpected that had worked previously seemed to be the key.  

(Chris - turns out I only needed to make one of those directories - it was obviously having a bit of a blind spot with it! Next job is to look into your suggestion of making my external /home)

Thanks again.

---

### Post by fabricator4 on 2011-06-01
> **Matbenjen said:**
> Sorted! 

Well done!  I know what a steep learning curve the command line is - and you're following a complex set of instructions with no background in CLI to know what the error messages are telling you.

It's worthwhile learning a bit of CLI (mounting drives, making directories, copying and editing files etc) because many of us will give CLI solutions to problems asked.  This is _not_ because we are being ornery or geekish, but because CLI is the easiest and clearest way to communicate a solution.  Also, in most cases the commands can be simply cut and pasted into the terminal.

Chris

---


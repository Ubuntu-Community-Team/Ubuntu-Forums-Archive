---
title: "Can't boot Ubuntu - GRUB error 25"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by Bearly Able on 2009-05-31
Hi,

Please can someone help me recover from a GRUB error?  I can't boot either normally or in recovery mode.  All I can get is:```
Error 25 disc read error

Press any key to continue
```Pressing any key returns me to the GRUB menu, and then the same problem.

I'd had other problems with the system, which I don't think were related, but it was running fine yesterday and shut down normally without incident.

I need the computer for work, and would be really grateful if someone could help me sort this out.  Thanks in advance.

---

### Post by halitech on 2009-05-31
from what I can find error 25 is related to either not finding a bootable kernel or a disk read error

check here and see if there is anything to help you

[http://ubuntuforums.org/showthread.php?t=117271&highlight=grub+error+25](http://ubuntuforums.org/showthread.php?t=117271&highlight=grub+error+25)

---

### Post by Bearly Able on 2009-05-31
Thanks, halitech, I'd searched the forums and Google but failed to find much enlightenment.

I'm really not sure what's going on here.  I have two hard drives, one with XP and one with Ubuntu, each with their own boot sector.  Because for some reason GRUB won't load Windows, we have it set up the other way round, so the Windows boot loader launches GRUB.  I had a lot of help on setting that one up, and feel rather daunted at the prospect of trying to reinstall GRUB, as suggested in the link you posted.

My system is only two years old, and the Ubuntu hard drive just four months old, so I wouldn't expect it to be a hardware problem.

However, I'm running from the Live CD at the moment and while I could mount my Ubuntu drive no problem, I can't now unmount it.  Also, I can't mount the Windows drive or any USB drives.  They all show up under "computer", but nothing happens when I try to mount them.  This is a double problem, as my husband has yet to learn how to back up his data, and I need to rescue it for him.  I can access his home directory, but not anything I can copy it to.  I only have one CD drive, which I'm using to run the Live CD.

I had no problems with anything until I upgraded to Jaunty a couple of weeks ago.  If all else fails, I can reinstall, but I'd really like to rescue my husband's data first.

---

### Post by halitech on 2009-05-31
wish I had more information on error 25 but I don't. If you can mount the ubuntu drive I would say its fine but if you can't mount windows, either it's not reading ntfs properly or there is an issue with that drive (possible since grub is installed on that drive)

is the data on the windows partition that you need to save or the ubuntu drive?

---

### Post by Bearly Able on 2009-05-31
Thanks for the swift reply, halitech.

The data I need is on the Ubuntu drive, which, as I say, I can mount but can't mount anything to copy it to.  (I have a laptop with 8.04 on it, but as I understand it, I need to install ssh or something on both machines to transfer the files that way.)

I've followed one of the links from the thread you gave me, and the information given for Error 25 is basically about physical problems - incorrect jumper setting on IDE drive, etc.  Both my drives are SATA and have been installed for some time.

I believe my GRUB menu is actually installed on the Ubuntu drive, although the Windows drive is used to load it.  (I'm aware I'm not explaining this too well; [this]("http://ubuntuforums.org/showthread.php?t=1060203") is where my original help came from.)

---

### Post by halitech on 2009-05-31
if grub is on the ubuntu drive then you could try taking the windows drive out (just disconnect the cables) and see if it will boot into ubuntu. if it does you may have better luck mounting a usb drive to save the data.

---

### Post by Bearly Able on 2009-05-31
OK, I can do that.

Since I can't unmount the Ubuntu drive now, am I going to have problems with mounting it again when I restart?  The error message I'm getting says:
```
Cannot unmount volume
Error org.freedesktop.Hal.Device.InterfaceLocked.
The enclosing drive for the volume is locked.
```

---

### Post by halitech on 2009-05-31
shouldn't have any issues with mounting it (I hope)

did you try the umount with sudo?

---

### Post by Bearly Able on 2009-05-31
Nope.  I knew there was a way of doing it through the command line, but I didn't know what it was.  I'll try that now.

---

### Post by Bearly Able on 2009-05-31
Well, I tried looking at my system specs to see how it refers to the drive, but when I tried ```
sudo umount -disk:1
```all I got was```
umount invalid option -- 's'
```so I guess I'm doing something wrong here.

---

### Post by halitech on 2009-05-31
whats the output of ```
sudo fdisk -l
```
and ```
sudo mount
```

---

### Post by Bearly Able on 2009-05-31
Here's the information:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfbc4fbc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4462    35840983+   7  HPFS/NTFS
/dev/sda2            4463       19457   120447337+   f  W95 Ext'd (LBA)
/dev/sda5            4463        8295    30788541    7  HPFS/NTFS
/dev/sda6            8296       12416    33101901    7  HPFS/NTFS
/dev/sda7           12417       16600    33607948+   7  HPFS/NTFS
/dev/sda8           16601       19457    22948821    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ec031

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18701   150215751   83  Linux
/dev/sdb2           18702       19457     6072570    5  Extended
/dev/sdb5           18702       19457     6072538+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```and
```
ubuntu@ubuntu:~$ sudo mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

```

---

### Post by halitech on 2009-05-31
try this

```
sudo umount /dev/sdb1
```

---

### Post by Bearly Able on 2009-05-31
Thank you - that's worked.  I'm going out just now, but I'll unplug my Windows drive and check my other connections when I get back, and post back.  Thanks again for your help.

---

### Post by halitech on 2009-05-31
glad to help out thus far. will check back later for any info you have

---

### Post by Bearly Able on 2009-05-31
Well now, this is really weird.

I opened the case and checked all the connections I could find; nothing seemed loose in any way.  The connection to the Windows hard drive is awkward to get at (or, at least, to get a grip of), so rather than physically disconnecting it, I set the BIOS to boot from the second hard drive.  As I understand it, this should just load GRUB direct.  However, I got the usual boot menu with the choice of Windows or GRUB, chose GRUB, and Ubuntu loaded first time.

I can also mount and unmount the various partitions on the Windows drive with no problem.

I have no idea what's happening or why, but I'm about to back up everything while the going's good and hope I can get some help with my nvidia driver problem, which is where I was before the whole system went up the spout!

Thanks again for your help, halitech.

---

### Post by halitech on 2009-05-31
that is odd but doing a backup now sounds like a wise idea. I don't have an Nvidia card so probably won't be much help to you with that.

---


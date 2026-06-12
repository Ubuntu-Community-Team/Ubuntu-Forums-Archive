---
title: "Multiple USB storage devices"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Chew N Tobacca on 2009-02-05
Something I just noticed... 

My objective is quite simple: I would like to transfer data between a USB hard drive and a USB flash drive. Seems pretty easy. However, if one removable device is already mounted and the other is inserted, the one that was mounted first is (apparently) unmounted and replaced with the newly inserted drive. 

For example, I plug in my USB flash drive, it mounts, and everything is good. I then plug in my USB HDD, it mounts and it overrides the flash drive that was mounted. As a result, I have perfect access to the HDD but no longer have access to the flash drive. It is removed from everything. Seems to be the same under any desktop environment.

Long story short, to transfer data from HDD to flash drive, I must copy it to an internal location and remove the source drive. Then insert the destination drive and re-copy the data there. Not the end of the world, but is rather annoying.

Is this just the way it is? Or is there a simple solution I am overlooking? Thanks in advance for any input.

---

### Post by mjheagle8 on 2009-02-05
does one of the drives disappear from /media ?
the onlt thing i can think of is if the drives are named the same thing and one is mounting over where the other one was.

---

### Post by emarkd on 2009-02-05
That's not just the way it is.  Ubuntu should be able to recognize as many usb storage devices as you can physically plug into it.  Try plugging both devices up and then posting the output of the 'mount' command.  It should tell you what's mounted and where.

---

### Post by Chew N Tobacca on 2009-02-05
> does one of the drives disappear from /media ?
Yes. The first inserted drive is removed from the /media folder as well as the desktop.


As requested, here is the output of the "mount" command while both drives are inserted:
```
/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-4-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-4-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sdb1 on /media/CHEW_Z type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=999)
```

---

### Post by Chew N Tobacca on 2009-02-05
My bad... that was the output from a Jaunty Live CD... Here is the output from my installed system:
```
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/chew/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chew)
/dev/sdc1 on /media/CHEW'Z type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
chew@CreepingDeath:~$
```


The HDD shows up fine ("CHEW'Z"), but the flash drive ("MAJIN DRIVE") is nowhere to be found.

---

### Post by Chew N Tobacca on 2009-02-08
Just a bump, hoping to find a solution...

---

### Post by 3rdalbum on 2009-02-08
This shouldn't happen! It's very strange behaviour; is your system fully updated? I believe there was a HAL update some weeks ago that might fix the problem.

Alternatively, you could manually mount the original drive (the one that disappears). Create a directory in /media (for instance, /media/flashdrive) and alter the permissions to allow your user access:

```
sudo mkdir /media/flashdrive
sudo chmod a+rw /media/flashdrive
```

Then find out the device file name of your drive by typing this command:

```
sudo fdisk -l
```

(the device file name begins with /dev/ and you can recognise the correct device by the filesystem and by which one has the highest amount of storage - we'll assume it's /dev/sdb1)

```
pmount /dev/sdb1 flashdrive
```

When you want to unmount it, just use this command:

```
pumount flashdrive
```

Give that a whirl. I haven't tried it myself as I don't have any disks that exhibit odd behaviour like the one you're describing, but I think it should work alright.

---

### Post by Kellemora on 2009-02-08
Hi Chew N

I had sorta a similar problem when I was setting up my data file server.

I have 4 external 500 Gib hard drives on it!
At first it would only see the last two that were plugged in.
It seemed no matter what I did, it would not see but two of them.
At first I though maybe that was a limitation in Ubuntu.
But I did a COLD Reboot (that means from a complete shut down, not just a restart) I had tried the soft restart and that didn't work.
But after the COLD Reboot, all the drives then appeared and even automounted to the desktop.

I never added or changed anything myself in /media or elsewhere, whatever was needed fixed itself when I did the Cold Reboot.
It MIGHT have had something to do with the Bios themselves????? Which is why it took a COLD Reboot?????

Just remember to UNMOUNT anything before you unplug it!

Don't know if this will help in your case or not, but it don't hurt giving it a try!

Of an interesting note, the book that came with my MOBO said limit of 10 USB devices.  I've had as many as 20 USB devices running and was told the limit is more up around 135 right now.  In any case, I've never run out of USB ports yet, hi hi..........

TTUL
Gary

---

### Post by Chew N Tobacca on 2009-02-08
> This shouldn't happen! It's very strange behaviour; is your system fully updated?

I thought this shouldn't happen... it IS very strange behavior. My system is fully updated (as of 12 hours ago). I keep it updated always, but thought I'd double-check.

Before I forget, I have tried rebooting (hard and soft) with both devices inserted and turned on. If I do not remove the first-inserted drive, it makes a mess upon a reboot. I get some strange error before GRUB loads, and something terrible happens. I've only done it once, because as a result I re-formatted the flash drive when it was all done.

I've checked for options in my BIOS, but not much there. No control of USB devices to speak of. 

I tried what you recommended, 3rdalbum, and here are the commands I have run with the flash drive inserted (while it is still accessible). Assuming we are trying to mimic the first device, I hope I am doing this correctly:

```
sudo mkdir /media/majin_drive
sudo chmod a+rw /media/majin_drive
sudo fdisk -l
```

I get this from 'sudo fdisk -l':

```
Disk /dev/sdb: 4126 MB, 4126146560 bytes
16 heads, 32 sectors/track, 15740 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15740     4029424    b  W95 FAT32
```

And then:

```
chew@CreepingDeath:~$ pmount /dev/sdb1 majin_drive
Error: device /dev/sdb1 is not removable
```

Unless I am misunderstanding, this should mount /dev/sdb1 to the majin_drive folder I created in /media, correct?

---

### Post by Chew N Tobacca on 2009-02-09
So I thought I'd test a few more variables. I acquired another USB flash drive, and both are supported at the same time; no trouble at all - they both work as desired. However, neither one will work if inserted before my USB HDD. 

The denominators I've found thus far: 
1.) HDD has autorun software that Ubuntu recognizes. Could the autorun software be somehow conflicting with the other devices? 
2.) The HDD is plugged in to a USB PCI card, and the others I have inserted directly to the front of the tower. Perhaps the PCI and onboard USB controller don't get along... 

For curiosity's sake, I ran 'lsusb' and Ubuntu does not seem to differentiate between onboard ports and PCI ports. Here is what I got with just the keyboard and such:

```
chew@CreepingDeath:~$ lsusb
Bus 007 Device 002: ID 0d8c:0103 C-Media Electronics, Inc. Turtle Beach Audio Advantage Micro
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c218 Logitech, Inc. Logitech RumblePad 2 USB
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by Chew N Tobacca on 2009-02-09
Ah-ha! This morning I devised a solution. I can't guarantee it will work for others with the same issue, but it works for me.

Upon realizing that my HDD was using a PCI USB card, I decided to juggle the devices and try an external hub. So I put the HDD and the hub on the same set of ports (a pair) on the motherboard, using the hub for the flash drives. With that accomplished, I thought I'd try it all again, and voila! They all work fine, all three devices at once. Still does not explain the mystery at hand, but is a solution. For now.

---


---
title: "Mounting aggravation"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by miamaslegi on 2011-09-04
I'm having a problem with a flash drive. :(
I have a 4GB SanDisk Cruzer flash drive that I use sometimes. Usually, when I plug the drive in, it auto-mounts no problem, then when I'm done, I unmount it and take it out, no big deal.
Well, I inserted the drive today and the little USB plug icon (really technical, eh?) that pops up in my panel when I insert the drive didn't pop up. I tried to access the drive through Dolphin, and it told me:

An error occurred while accessing '3.7 GiB Removable Media', the system responded: org.freedesktop.UDisks.Error.Failed: Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sda1 is already mounted on /
mount failed

I'm quite new to Linux, so I don't really know what to do to to get my flash drive back to working properly - I'm not even sure I quite know what Dolphin told me. Any help would be greatly appreciated!

---

### Post by miamaslegi on 2011-09-06
](*,)

Please, can anyone help?
I've tried looking up everything I can think of relating to problems with mounting flash drives, but I can't find anything at all relating to my issue - at least, I've found nothing that I recognize as pertaining to my issue.
I'm just a helpless Linux newbie that doesn't know my rear from a hole in the ground right now - I'm trying, though! I'm also a helpless Linux newbie who really, really needs to access her flash drive from her netbook!
Come on guys, I'm begging!
Help, help!

---

### Post by CharlesA on 2011-09-06
Run this in a terminal with the flash drive plugged in please:

```
sudo fdisk -l
```

The error message in the OP says that that device is already mounted on "/", which would be the problem.

---

### Post by gdonwallace on 2011-09-06
Sounds like it didn't unmount the last time you used it.

Anywho, go to a terminal and type df -h.  This will show all mount points on your system.  If /dev/sda1 is shown and is listed as a your USB, then that would be the problem.  Type umount /dev/sda1 and that should take care of the problem.

For the most part, linux is pretty good about cleaning these types of things up.  Sometimes the process will get hung and it won't be able to unmount automatically.  If you don't already do it, when you are ready to remove the USB drive, right click on it in your file manager and choose the unmount option.  That should keep things like this from happening in the future.

Good luck

---

### Post by vasa1 on 2011-09-06
> **gdonwallace said:**
> ... If you don't already do it, when you are ready to remove the USB drive, right click on it in your file manager and choose the unmount option ...

Is that the same as "eject" which is what I see in Nautilus / Ubuntu 11.04?

---

### Post by miamaslegi on 2011-09-06
Well, I tried this


```
amanda@amanda-AO532h:~$ umount /dev/sda1
umount: /dev/sda1 is not in the fstab (and you are not root)
amanda@amanda-AO532h:~$ sudo umount /dev/sda1
[sudo] password for amanda: 
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
amanda@amanda-AO532h:~$ 

```

and figured something had messed up (oh, yes, /dev/sda1 was listed as a mount point). Then I was going to do what CharlesA suggested, which I didn't see before, and when I inserted the flash drive, it mounted! 
I'm thoroughly confused as to what just transpired, but I'm glad my flash drive mounted!
I am always super careful to unmount my flash drive, so either I forgot one time, or something funky is going on. I'm leaning toward the former. ;)
Thank you all, though, very much - I really appreciate the help!

---

### Post by CharlesA on 2011-09-06
You are trying to unmount the 'root' partition, which won't work since it's in use (that's the partition the OS lives on)

Can you post the output of the fdisk command?

Also the output of this one:

```
cat /etc/fstab
```

This one:
```
mount
```

And this one:

```
sudo blkid -c /dev/null
```

---

### Post by miamaslegi on 2011-09-06
Ah, I can always be counted on to screw something up really well. I thought everything was fine, but my flash drive just disappeared. 
I really have no idea what I'm doing (I **want** to know so badly, but I just don't yet). Oh, what do I type for the fdisk command? I don't know what option to use - yes, I am that clueless.

When I did these commands, the flash drive was inserted - and still is. I don't want to take it out and mess something up more!

Here we go - 

```
amanda@amanda-AO532h:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=29865d6d-4bb3-42d9-be05-0b052369ae4f none            swap    sw              0       0

amanda@amanda-AO532h:~$ 


``````
amanda@amanda-AO532h:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/amanda/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=amanda)
amanda@amanda-AO532h:~$ 


``````
amanda@amanda-AO532h:~$ sudo blkid -c /dev/null
[sudo] password for amanda: 
/dev/sda1: UUID="99d92a57-943a-4b91-869c-0476d1b384ef" TYPE="ext4" 
/dev/sda5: UUID="29865d6d-4bb3-42d9-be05-0b052369ae4f" TYPE="swap" 
/dev/sdb1: LABEL="EFI" UUID="640B-0804" TYPE="vfat" 
/dev/sdb2: LABEL="PCBSD" UUID="F86A-0900" TYPE="vfat" 
amanda@amanda-AO532h:~$ 

```

---

### Post by CharlesA on 2011-09-06
Ok found your problem - fstab lists /dev/sdb1 as the "/" partition, when it's not supposed to be.

Replace /dev/sdb1 with:

```
UUID=99d92a57-943a-4b91-869c-0476d1b384ef
```

In your fstab and reboot.

---

### Post by miamaslegi on 2011-09-06
Hmmm...I think something is wrong. :(

I edited fstab **exactly exactly** the way the way shown. I rebooted my netbook (I'm on my Mac now) with the flash drive still inserted (maybe that's where I screwed up?). A screen came up that said something to the effect of -- the mounting failed - press S to skip mounting or M for manual recovery.

I can press S and nothing happens. Ever. I press M and I get:

```
Filesystem check or mount failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and continue booting after re-trying
filesystems. Any further errors will be ignored
root@amanda-AO532h:~# exit
mountall start/starting
```

Eeep. What do I do? Is my computer going to melt into a puddle because of something stupid I did? :shock:

---

### Post by CharlesA on 2011-09-07
Hmmmm, which mount did it say failed?

You can boot from a livecd and edit the fstab file again to verify that the correct UUID is listed.

The line should look like this:

```
UUID=99d92a57-943a-4b91-869c-0476d1b384ef       /               ext4    errors=remount-ro 0       1
```

---

### Post by miamaslegi on 2011-09-07
I can't remember what it said before the "press S to skip..." Argh.

My computer was frozen with that last bit on the screen still.

```
Filesystem check or mount failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and continue booting after re-trying
filesystems. Any further errors will be ignored
root@amanda-AO532h:~# exit
mountall start/starting
```

I waited and waited to see if it would come to its senses, but no dice. I restarted the little bugger and now I have this on the screen - 

```
GNU GRUB version 1.99~rc1-13ubuntu3
Ubuntu, with Linux 2.6.38-11-generic
Ubuntu, with Linux 2.6.38-11-generic (recovery mode)
Previous Linux versions
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

```

Blargh, what do I pick? Why is it even showing me this??

Oh, I forgot to say, I'm running Ubuntu on an Acer Aspire One 532h - it has no CD drive and one USB port. Would I need to make a bootable USB flash drive since I can't do the CD thing? I don't think I still have the one I made to install Ubuntu in the first place. :(

---

### Post by saltmarshlamb on 2011-09-07
Might be worth booting the livecd - going here and following the instructions

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Yes - you'll need to boot with the bootable usb - as an aside it is always worth keeping one about.

---

### Post by miamaslegi on 2011-09-07
What would be best to create the bootable USB with? I'm working on an iMac right now - I know Unetbootin will run on Macs, but I don't think that would work in this case, right? Aren't bootable USB drives created with Unetbootin only bootable on PCs?

---

### Post by saltmarshlamb on 2011-09-07
Try - [https://help.ubuntu.com/community/Installation/FromUSBStick#From_Mac_OSX](https://help.ubuntu.com/community/Installation/FromUSBStick#From_Mac_OSX)

Afraid I can't help much with the unetbootin thing - never needed to use it.

---

### Post by miamaslegi on 2011-09-07
OK, I did get my bootable USB made.
Do I shut the netbook down, insert the USB drive, power on, go into BIOS, boot from the USB? Then download the boot info script, and so on? :confused:

---

### Post by CharlesA on 2011-09-07
> **miamaslegi said:**
> OK, I did get my bootable USB made.
Do I shut the netbook down, insert the USB drive, power on, go into BIOS, boot from the USB? Then download the boot info script, and so on? :confused:

Boot off the LiveUSB and check to make sure fstab looks like the above post. If it does, download the bootscript so we can figure out what is going on. :)

---

### Post by miamaslegi on 2011-09-07
The fstab looks completely different, not just a wrong line -  

```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```

---

### Post by CharlesA on 2011-09-07
Right forgot you were on a livecd, you've got to mount the root partition first.

```
sudo fdisk -l
```

Find the name of the drive and mount it somewhere - media would work:

```
sudo mount /dev/sdXY /media
```

Check the fstab file:

```
sudo nano /media/etc/fstab
```

---

### Post by miamaslegi on 2011-09-07
It's telling me this:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00020154

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19076   153219072   83  Linux
/dev/sda2           19076       19458     3068929    5  Extended
/dev/sda5           19076       19458     3068928   82  Linux swap / Solaris

Disk /dev/sdb: 4000 MB, 4000317440 bytes
114 heads, 49 sectors/track, 1398 cylinders
Units = cylinders of 5586 * 512 = 2860032 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1399     3906552    b  W95 FAT32
ubuntu@ubuntu:~$ 

```

Is /dev/sda1 the one I want?

---

### Post by CharlesA on 2011-09-07
Yep that's the one you want.

---

### Post by miamaslegi on 2011-09-07
OK, now fstab says

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=99d92a57-943a-4b91-869c-0476d1b384ef
# swap was on /dev/sdb5 during installation
UUID=29865d6d-4bb3-42d9-be05-0b052369ae4f none            swap    sw           $


```

I think that's right, isn't it?
Now download the bootscript, correct?

---

### Post by CharlesA on 2011-09-07
> **miamaslegi said:**
> OK, now fstab says

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=99d92a57-943a-4b91-869c-0476d1b384ef
# swap was on /dev/sdb5 during installation
UUID=29865d6d-4bb3-42d9-be05-0b052369ae4f none            swap    sw           $


```

I think that's right, isn't it?
Now download the bootscript, correct?

Ah, I see what happened.

Change that line to read like this:
```
UUID=99d92a57-943a-4b91-869c-0476d1b384ef       /               ext4    errors=remount-ro 0       1
```

---

### Post by miamaslegi on 2011-09-07
OK, I've got it changed - now reboot, perhaps?

---

### Post by CharlesA on 2011-09-07
Yep, reboot and see what happens.

---

### Post by miamaslegi on 2011-09-07
OK, it told me to remove the usb and press enter, which I did, it rebooted, and it's the same blue screen with

```
GNU GRUB version 1.99~rc1-13ubuntu3

Ubuntu, with Linux 2.6.38-11-generic
Ubuntu, with Linux 2.6.38-11-generic (recovery mode)
Previous Linux versions
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

Use the (up) and (down) keys to select which entry is highlighted.
Press enter to boot the selected OS, 'e' to edit the commands before booting or 'c' 
for a command-line.
```

---

### Post by CharlesA on 2011-09-07
Select the top one and hit enter.

---

### Post by miamaslegi on 2011-09-07
Ah, it's working fine now.  Thank you so very much!!

---

### Post by CharlesA on 2011-09-07
Awesome. Glad you got it working.

Don't forget to mark the thread as solved from thread tools. :)

---


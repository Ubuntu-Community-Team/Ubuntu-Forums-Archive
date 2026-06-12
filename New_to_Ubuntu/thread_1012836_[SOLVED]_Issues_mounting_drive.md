---
title: "[SOLVED] Issues mounting drive"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by vikigal on 2008-12-16
Warning: This is long but I am trying to include as much info as possible.


My cd drive is not reading disks properly. It will not mount volume. In fact it will not mount at all. It will show a music disk in the home folder but not always on the desktop while swearing there is nothing there. Rhythmbox will attempt to play the music disks, and will read the info but it sounds like it is skipping. Data disks are read as nothing there. 

I have uninstalled-reinstalled alsa and ran a config command. In the multi-media section of control center I can run test on audio and get clear sound on default output, however on default input test I get a clear sound on test sound but not on anything else. Pulse, Alsa, and OSS are what is listed.

I upgraded to Hardy last week and have had problems since. The sound is good from anywhere but the cd/dvd drives. Thinking there might be a hardware issue I installed an external drive. It does the same thing except the music will play smoothly for varying times (few seconds to a few songs) then skips out, then stops sounds while the indicator says it is playing. Data other than music does not show up at all.

I have tried so many things I have lost track. I have created a totally new user/admin. and still had the same problem on a clear system. When it started I had no sound at all so somewhere I fixed something. I have tried manually mounting both in properties and through terminal but that does not work either. I have run sound config commands, which was what I think did the initial problem solving.

I have 4 tabs open right now including how to fstab and how to mount partitions but I dont know if this would solve anything because I am not sure where the problem is. Here is my fdisk -l result:

oldgal1@user-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cfba8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9545    76670181   83  Linux
/dev/sda2            9546        9730     1486012+   5  Extended
/dev/sda5            9546        9730     1485981   82  Linux swap / Solaris
oldgal1@user-desktop:~$ 
 
I get an odd error message with lots of stuff in it that I cannot translate. The end says more info may be found at syslog so I ran the command suggested. Here is what I got:
oldgal1@user-desktop:~$ dmesg | tail or so
tail: cannot open `or' for reading: No such file or directory
tail: cannot open `so' for reading: No such file or directory
oldgal1@user-desktop:~$ dmesg | tail
[   84.311157] Bluetooth: RFCOMM TTY layer initialized
[   84.311161] Bluetooth: RFCOMM ver 1.8
[   87.490961] NET: Registered protocol family 17
[   87.719036] [drm] Initialized drm 1.1.0 20060810
[   87.722652] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   87.722667] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   87.722792] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   93.734674] NET: Registered protocol family 10
[   93.735346] lo: Disabled Privacy Extensions
[  103.760465] eth1: no IPv6 routers present
oldgal1@user-desktop:~$ 

attached is a screenshot of my error message.

Here are the results of the mount command. (I will say this has forced me to learn how to use my terminal and not be afraid.)

oldgal1@user-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-22-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
oldgal1@user-desktop:~$ ls /dev/disk/by-uuid -alh
total 0
drwxr-xr-x 2 root root  80 2008-12-16 03:16 .
drwxr-xr-x 5 root root 100 2008-12-16 03:16 ..
lrwxrwxrwx 1 root root  10 2008-12-16 03:16 55193bf0-fe46-4f6c-b4e3-c91323dd7319 -> ../../sda5
lrwxrwxrwx 1 root root  10 2008-12-16 03:16 b3699818-7423-4645-8cb1-a5f72e32aad9 -> ../../sda1
oldgal1@user-desktop:~$ 


Can anybody help me? I need advice badly.

Thanks so much for your patience in reading this mess (whether you help or not!)

8.04 Hardy  Kernel Linux 2.6.24-22-generic
GNOME 2.22.3

Hardware  memory: 495.0 MiB
Processor 0: Intel(R) Pentium(R) 4 CPU 3.00 GHz
Processor 1: Intel(R) Pentium(R) 4 CPU 3.00 GHz

oldgal1@user-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
oldgal1@user-desktop:~$

SOLVED 
 the cd drive is now mounting. It is reading and opening disks. To solve the problem I opened synaptic package manager, entered ¨sound¨ into search. Then I found something that had to do with intel, (the driver I was looking for). It was not installed so I installed it.

 I also reinstalled everything I could find connected to pulseaudio and alsa. I still do not have sound but I am closer than I was. Now when I again work through the how-tos maybe it will work...

I know this is not technically correct wording, but I am working on it. Just hope it makes enough sense to help someone else, if explained better by someone who can figure out what I did.

---

### Post by Michael.Godawski on 2008-12-16
hey, 
can you please post your fstab file?

```
cat /etc/fstab
```

I am now on my way home so I am going to answer in 1 hour.

---

### Post by rlunger on 2008-12-16
> **vikigal said:**
> 
oldgal1@user-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cfba8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9545    76670181   83  Linux
/dev/sda2            9546        9730     1486012+   5  Extended
/dev/sda5            9546        9730     1485981   82  Linux swap / Solaris
oldgal1@user-desktop:~$

This just shows you're hard drive, that you have a primary partition which is ext3 formatted, and that you have an extended partition that contains your swap partition.  Nothing really helpful here...
 
> 
oldgal1@user-desktop:~$ dmesg | tail or so
tail: cannot open `or' for reading: No such file or directory
tail: cannot open `so' for reading: No such file or directory


The 'dmesg' command simply prints out your system messages.  When you use 'dmesg | tail' you're 'piping' the data in 'dmesg' to 'tail'.  'tail' is a program that shows only the last 10 lines of what you send it, so that's all you're getting.  To see the last 20 lines, use 'dmesg | tail -20'.  

> 
oldgal1@user-desktop:~$ dmesg | tail
[   84.311157] Bluetooth: RFCOMM TTY layer initialized
[   84.311161] Bluetooth: RFCOMM ver 1.8
[   87.490961] NET: Registered protocol family 17
[   87.719036] [drm] Initialized drm 1.1.0 20060810
[   87.722652] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   87.722667] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   87.722792] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   93.734674] NET: Registered protocol family 10
[   93.735346] lo: Disabled Privacy Extensions
[  103.760465] eth1: no IPv6 routers present
oldgal1@user-desktop:~$ 
  

I don't know at what point you listed these, but there's nothing useful here.  You would have to use 'dmesg' at the point you run into a problem for there to be anything useful.



> 
oldgal1@user-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-22-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
oldgal1@user-desktop:~$ ls /dev/disk/by-uuid -alh
total 0
drwxr-xr-x 2 root root  80 2008-12-16 03:16 .
drwxr-xr-x 5 root root 100 2008-12-16 03:16 ..
lrwxrwxrwx 1 root root  10 2008-12-16 03:16 55193bf0-fe46-4f6c-b4e3-c91323dd7319 -> ../../sda5
lrwxrwxrwx 1 root root  10 2008-12-16 03:16 b3699818-7423-4645-8cb1-a5f72e32aad9 -> ../../sda1
oldgal1@user-desktop:~$ 


The output of 'mount' simply shows that your root file system is mounted on /dev/sda1 (your primary partition) and that the virtual file systems are mounted properly.  To actually mount something, you would have to use:

    sudo mount -t Type /dev/Device /mnt/MountPoint

where you replace Type with the partition format (such as 'ext3', 'vfat', 'iso9660').  Replace Device with the device name you wish to mount, such as 'sda1' or 'fd0' and replace MountPoint with the folder you have created (like 'otherdrive' in which to mount the file system.  If a partition or device is located in your '/etc/fstab' file (as the previous guy asked for), you can mount that filesystem via:

    sudo mount /dev/Device 

or all of your filesystems at once via:

    sudo mount -a


Hope this helps you figure things out.

---

### Post by vikigal on 2008-12-16
Thank you so much. I will try this later today when I get time again. I am flying by the seat-of-my-pants as this is the first problem I have had. I do not know what I am doing. 

Thank you for telling me things were ok in the mount because I did not know. I don´t know enough to be able to tell, that is why I posted so much information. Sorry if it was too much.

---

### Post by vikigal on 2008-12-16
oldgal1@user-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=b3699818-7423-4645-8cb1-a5f72e32aad9 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=55193bf0-fe46-4f6c-b4e3-c91323dd7319 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
oldgal1@user-desktop:~$ 


I am having trouble with the ntfs config. tool, I think. I have uninstalled it and re-installed with synaptic but it will not give me internal write support. It is always grayed out.  I really hate to show just how little I know, but could this be part of my problem?

---

### Post by vikigal on 2008-12-17
Well, my external drive is working mostly now but not the internal. I finally found the correct tab under administrations - authorizations and changed some permission then it mounted. Thank you.

However, I cannot get a mount point to take on the internal. I ran dmesg as soon as I tried a disk and got a reading that the terminal will not hold,at least I cant find the top. When I copy/paste into a text document it ran over ten pages with the following found in it:

[   60.285665] ata2.00: ATAPI: HL-DT-ST RW/DVD GCC-4320B, 1.11, max UDMA/33
[   60.285680] ata2.00: Drive reports diagnostics failure. This may indicate a drive
[   60.285682] ata2.00: fault or invalid emulation. Contact drive vendor for information.

Also the phrase Sense Key: Hardware error appears repeatedly toward the end.

I have contacted my trusty computer couple and they are setting me up an appt. to bring it in. I am lost. 

Should I post what he finds?

---

### Post by vikigal on 2008-12-18
My computer folks cant help me so I am on my own. Working my way through the how-to section I wandered into pulseaudio and working through it solved some of the problems with sound to it is definitely an upgrade problem. Also working through the alsa how-to solved some issues. I believe there is a compatability problem somewhere. Back to searching, searching, searching...

---


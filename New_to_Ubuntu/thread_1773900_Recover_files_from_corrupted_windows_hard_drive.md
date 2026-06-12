---
title: "Recover files from corrupted windows hard drive"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by Save my files on 2011-06-02
umm..
Well I'm completely new to ubuntu and my laptop  which I've had for 3 years has gotten corrupted the hard drive is ruined and there is no way to boot so i installed ubuntu onto a  usb drive and booted it up so i could recover the files, i first tried accessing my hard drive...nope! well i didn't expect it to work i got this error

 Error mounting: mount exited with exit code 12: Failed to read last sector (153225215): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

hmmm no idea what this means so i looked up some guides online and i was told to open Terminal and type sudo /bin/bash then mkdir /media/disk which gives me this message 

mkdir: cannot create directory `/media/disk': File exists
I don't know if this came up the first time i tried 

then i was told to enter

mount -t ntfs-3g /dev/sda1 /media/disk -o force

but i was to change the /dev/sda1 to whatever it was in the error message 
so i changed it to /dev/sda2

Buuuut then i get this

Failed to read last sector (153225215): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


I'd really appreciate some help because i really need to get those files back :frown:

---

### Post by jtarin on 2011-06-02
To check your correct partition.....use the command ```
sudo parted -l
```Do you have a CD/DVD drive on this laptop?

---

### Post by Autodave on 2011-06-02
[QUOTE=Save my files;10894877]umm..
Well I'm completely new to ubuntu and my laptop  which I've had for 3 years has gotten corrupted the hard drive is ruined and there is no way to boot so i installed ubuntu onto a  usb drive and booted it up so i could recover the files, i first tried accessing my hard drive...nope! well i didn't expect it to work i got this error

 
Since no one else has jumped in here, I'll offer my opinion: sounds like that hard drive is toast.  FAT or bad starting cluster is what it sounds like.

---

### Post by Save my files on 2011-06-02
> **jtarin said:**
> To check your correct partition.....use the command ```
sudo parted -l
```Do you have a CD/DVD drive on this laptop?

Right i entered that and got this
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA Hitachi HTS54258 (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1574MB  1573MB  primary  ntfs
 2      1574MB  80.0GB  78.4GB  primary  ntfs         boot


Model:  USB Flash Memory (scsi)
Disk /dev/sdb: 4006MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  4005MB  4005MB  primary  fat32        boot

And yes i do have a CD/DVD drive on my laptop

---

### Post by gwoodruff on 2011-06-02
If you have a windows CD I would first try to boot to a command prompt and run checkdisk with the /R option.```
chkdsk /R
``` May take hours to recover data from a corrupted disk but it can work.
Gary

---

### Post by Save my files on 2011-06-02
> **gwoodruff said:**
> If you have a windows CD I would first try to boot to a command prompt and run checkdisk with the /R option.```
chkdsk /R
``` May take hours to recover data from a corrupted disk but it can work.
Gary
I bought the laptop off of a friend a few years back and didn't get the windows disk and i don't have the money right now to go out and buy one

---

### Post by jtarin on 2011-06-02
> **Save my files said:**
> Right i entered that and got this
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA Hitachi HTS54258 (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1574MB  1573MB  primary  ntfs
 2      1574MB  80.0GB  78.4GB  primary  ntfs         boot


Model:  USB Flash Memory (scsi)
Disk /dev/sdb: 4006MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  4005MB  4005MB  primary  fat32        boot

And yes i do have a CD/DVD drive on my laptop

Use your CD/DVD drive to boot an Ubuntu Live CD to access your files on whichever partition /dev/sda1 or /dev/sda. You should be able to use a graphical file manager if they have mounted on boot.

---

### Post by Save my files on 2011-06-02
> **jtarin said:**
> Use your CD/DVD drive to boot an Ubuntu Live CD to access your files on whichever partition /dev/sda1 or /dev/sda. You should be able to use a graphical file manager if they have mounted on boot.
I'm on the laptop now with ubuntu from a usb drive, is there a difference between a live cd and a usb one?

---

### Post by jtarin on 2011-06-02
> **Save my files said:**
> I'm on the laptop now with ubuntu from a usb drive, is there a difference between a live cd and a usb one?
Can you see your files?

---

### Post by Save my files on 2011-06-02
> **jtarin said:**
> Can you see your files?
I can see the drive but it won't let me mount it

---

### Post by jtarin on 2011-06-02
> **Save my files said:**
> I can see the drive but it won't let me mount itHave you tried just opening up the Nautilus file manager and clicking on the drive......it should mount. Which partition shows to be the one with your files?

---

### Post by Save my files on 2011-06-02
> **jtarin said:**
> Have you tried just opening up the Nautilus file manager and clicking on the drive......it should mount. Which partition shows to be the one with your files?
Like i said, I'm new to ubuntu so i have no idea what that is I've checked around and i can't find it

---

### Post by Save my files on 2011-06-02
> **jtarin said:**
> Have you tried just opening up the Nautilus file manager and clicking on the drive......it should mount. Which partition shows to be the one with your files?
Oh wait thats the file browser....
Alright i open it up and there's a 78 GB filesystem which i assume is my hard drive but when i click it as i said i get this

Error mounting: mount exited with exit code 12: Failed to read last sector (153225215): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

---

### Post by jtarin on 2011-06-02
Try mounting the entire disk /dev/sda

---

### Post by jtarin on 2011-06-02
Redundant...deleted

---

### Post by alphacrucis2 on 2011-06-02
I think photorec can handle damaged ntfs partitions. Worth a try anyway.

---

### Post by gwoodruff on 2011-06-03
You can download a recovery cd for your version of windows with a bittorrent client. Burn the iso to a cd and boot from it. There is no difference betweeen a live cd and the usb version of Ubuntu you are using. If you cannot mount the partition your chances of recovering info from it are small in my experience. Here is a good tutorial on trying to force the mounting via a terminal:
 [http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

Good luck!

---

### Post by tgalati4 on 2011-06-03
sudo apt-get install testdisk
man testdisk
man photorec

testdisk tries to rebuild partition and directory trees.  photorec pulls out individual files.

---


---
title: "Problems using other partitions of hard disk"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by RobikShrestha on 2011-03-06
I allocated only 10 GB for ubuntu. But now i require much more space coz i love ubuntu. But my I have windows too. When I save file from ubuntu after mounting a hard disk drive (d:, e:, g: as viewed from windows), sometimes the files get lost, sometimes corrupted. I do not why. Is there a way to add space to the drive 'sda7' used by ubuntu?

---

### Post by RobikShrestha on 2011-03-06
Also is there a way to make those partitions compatible for both windows and ubuntu? I mean i can write files from both OS but when i open those files from windows they get lost.

---

### Post by JRV on 2011-03-06
Can we see how you have your partitions set-up?

Open a terminal and run the command:
```
sudo parted
```

When the parted prompt comes up run the command:
```
print
```

And post the results.

---

### Post by RobikShrestha on 2011-03-06
suzuki@suzuki-laptop:~$ sudo parted
GNU Parted 1.8.8.1.159-1e0e
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ATA SAMSUNG HM320II (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  106MB   105MB   primary   ntfs         boot
 2      106MB   54.0GB  53.9GB  primary   ntfs
 3      54.0GB  202GB   148GB   primary   ntfs
 4      213GB   320GB   107GB   extended               lba
 5      213GB   266GB   53.7GB  logical   ntfs
 6      266GB   309GB   42.9GB  logical   ntfs
 7      309GB   320GB   10.7GB  logical   ext4

---

### Post by vanadium on 2011-03-06
Linux supports writing to ntfs file systems, so files should not get lost or corrupted, unless there is erroneous use such as unplugging the drive unproperly. In your scenario, where you use both OS'es, your best bet is to use the ntfs partitions for data storage. This way, your disk space use is most efficient and all of your data are available in both operating systems.

Make sure that your ntfs partitions are kept in a healthy state. Frequently perform a file system check using the Windows file checking tools.

It would be more convenient to automatically mount your ntfs data partitions during system startup. Now, you probably have to click them first in the file manager before they can be used.

Only when Ubuntu becomes your prime OS will the time come to reformat partitions to linux file systems.

---

### Post by RobikShrestha on 2011-03-06
how do i automatically mount them? It always asks me for password, but it's my computer and I am the only user!

---

### Post by vanadium on 2011-03-06
To have partitions mounted automatically, you need to edit the configuration file /etc/fstab in order to add a line for each partition you want to mount. See [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Essentially, it boils down to creating a mount point (an empty directory) and adding one line that gives
1) the UUID of the partition 2) the mount point 3) the file system 4) the options 5) a number for "dump" (0) 6) a number indicating if the file system must be checked on startup.

If you post the output of "sudo blkid", I can give you a hands-on example if needed.

---

### Post by RobikShrestha on 2011-03-06
/dev/sda1: UUID="F6582FF7582FB571" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="FA7C40757C402F27" TYPE="ntfs" 
/dev/sda3: UUID="CC983A55983A3DF0" TYPE="ntfs" 
/dev/sda5: UUID="32728DF9728DC1D9" LABEL="New Volume" TYPE="ntfs" 
/dev/sda6: UUID="0674A5BE74A5B0BB" LABEL="BackUpFiles" TYPE="ntfs" 
/dev/sda7: UUID="9dc8eb36-80b3-4ff0-82f0-4fcad1200fc7" TYPE="ext4"

---

### Post by RobikShrestha on 2011-03-07
Obviously the command is too complicated and for a starter like me it's like sth written in Arabic (of course I do not know Arabic). Isn't there a GUI way of doing it?

---

### Post by vanadium on 2011-03-07
As administrator in linux, you sometimes need a little bit command line. To automatically mount for example your "new volume", first create a mount point for it.
```

sudo mkdir /mnt/new_volume

```
open /etc/fstab as root with the command
```

gksudo gedit /etc/fstab

```
To the bottom of the file, append a line for the partition. You obtain the UUID identifier from the output of the command "sudo blkid" (which you posted)
```

UUID="32728DF9728DC1D9" /mnt/new_volume ntfs dmask=000,fmask=111,utf8  0  0

```
The second entry is the mount point you choose. Then the file system is mentioned, then the options. You can read about fstab here: 
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Mount the drive (and check whether all is OK) with the command
```

sudo mount -a

```

If there is no output from the command, your /etc/fstab is OK and the Windows drive will be accessible in /mnt/new_volume.

To ease access to the volume, put a link into your home directory.
* Open a nautilus window in /mnt
* Open a second nautilus window in your home folder
* Hold Ctrl+shift pressed and drag "new_volume" to your home folder. Upon releasing the mouse button, a link "Link to new_volume" is created. Rename that to a name you like.

Once you understand this, you will be able to do something similar to other partitions you always want available.

---


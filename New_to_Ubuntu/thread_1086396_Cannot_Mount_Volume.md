---
title: "Cannot Mount Volume"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by Reckers on 2009-03-04
I run Windows Vista, until it crashed last night, and now, while the computer will start, Vista refuses to boot.

I proceeded to procure Hardy Heron on a CD, and have booted from that, but when I try to mount my hard drive to gain access to all of my files, I am told "Cannot mount volume." "Unable to mount the volume 'TOSHIBA SYSTEM VOLUME'".

When I click Details, I receive the long-winded message of:

"$LogFile indicates unclean shutdown (0, 0) Failed to mount '/dev/sdal': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: if you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g /dev/sda1 /media/TOSHIBA SYSTEM VOLUME -o force Or add the option to the relevant row in the /etc/fstab file: /dev/sda1 /media/TOSHIBA SYSTEM VOLUME ntfs-3g force 0 0"

I have no external devices.
Did my best with the first half of the second choice.
Have no idea how to approach the second half of the second choice.

I simply hope to gain access to my files and such, transfer them via USB drives to another computer, and then reformat this computer. Maybe along the way I'll become a full-fledged Ubuntu convert. 

Any help you can toss my way, I'll run with as quickly as I can and post the results.

Much appreciated ahead of time!

---

### Post by Therion on 2009-03-04
I don't know that this will solve your problem, but what t second half of option 2 is telling you to do is this...

In Ubuntu, using the LiveCD, go to Applications/Accessories and click on Terminal.

A sort of "DOS-box" looking thing will open.  This is the Terminal.  Cut and paste (or veeeery carefully type) the following line of code into it:```
mount -t ntfs-3g /dev/sda1 /media/TOSHIBA SYSTEM VOLUME -o force
```

---

### Post by Reckers on 2009-03-04
I tried that line, and received:

"bash: unt: command not found"

---

### Post by Therion on 2009-03-04
Try putting sudo in front of that command:```
sudo mount -t ntfs-3g /dev/sda1 /media/TOSHIBA SYSTEM VOLUME -o force
```

---

### Post by bsharp on 2009-03-04
You also need to escape the spaces:

```
sudo mount -t ntfs-3g /dev/sda1 /media/TOSHIBA**\** SYSTEM**\** VOLUME -o force
```

---

### Post by Reckers on 2009-03-04
I put sudo in front of that line, and received this complex response, which I had already seen throughout the day, never having any clue whatsoever how to treat it.

Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by Reckers on 2009-03-04
> **bsharp said:**
> You also need to escape the spaces:

```
sudo mount -t ntfs-3g /dev/sda1 /media/TOSHIBA**\** SYSTEM**\** VOLUME -o force
```

Just gave that a shot as well, and received:

WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/TOSHIBA SYSTEM VOLUME: No such file or directory

---

### Post by Reckers on 2009-03-04
I WAS MISTAKEN!
That last trick did it!
Thank you so so so much.
I think I'm in the clear now, and if I'm not, I'll be back.

THANKS GUYS

---


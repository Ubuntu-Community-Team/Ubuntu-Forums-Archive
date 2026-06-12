---
title: "sudo mount command error"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by mistypotato on 2010-10-31
This command is being rejected as a mount command.
[B]
sudo mount -t ntfs-3g /dev/sdh5 /media/WD250GB Part 2 -o force[/B]

When I use PartImage to view the partitions they are listed as sdh with partitions sdh1,2,3
(but the mount error popup says to use sdh5 for part2?)

Here is all I get when I issue the mount command in a terminal window.....

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

Any ideas why it's not working?

thx

---

### Post by trikster_x on 2010-10-31
Usually the command line brings up the help page when it thinks you have used an unknown option, which would be the "-3g".  Try to wrap ntfs-3g in double quotes(" "), or change it to ntfs without the -3g.

Also it would help if you stated what you are trying to accomplish.  Are you simply attempting to mount a partition?

---

### Post by mistypotato on 2010-10-31
> **trikster_x said:**
> Usually the command line brings up the help page when it thinks you have used an unknown option, which would be the "-3g".  Try to wrap ntfs-3g in double quotes(" "), or change it to ntfs without the -3g.

Also it would help if you stated what you are trying to accomplish.  Are you simply attempting to mount a partition?

Tried both your suggestions with the same result.



Yes...just trying to mount a partition.  There are actually 3 logical partitions inside the one main primary partition.

thx

---

### Post by trikster_x on 2010-10-31
You might check places>>computer to see if the partitions are in the device list there.  If they are, then you should be able to just double click and auto mount.

Also, so I don't waste your time or mine, have you tried any other mount commands?  If so, which ones?

---

### Post by mistypotato on 2010-10-31
No luck so far.

One odd note....

I was able to mount sdh1 but cannot mount sdh3 or sdh 5

all are on the same hard drive....same Primary partition but sdh1, sdh3 and sdh5 are logical partitions of the Primary partition.

So, odd that I can mount the first logical partition but not the other two?

---

### Post by Verbeck on 2010-10-31
instead of **/media/WD250GB Part 2 **try [B]/media/WD250GB\ Part\ 2

[/B]also, does the directory exist?

---

### Post by mistypotato on 2010-10-31
> **Verbeck said:**
> instead of **/media/WD250GB Part 2 **try [B]/media/WD250GB\ Part\ 2

[/B]also, does the directory exist?

Yes, the directory exists and has size as reported by PartImage.

myusername@mycomputer:~$ sudo mount -t ntf3-3g /dev/sdg5 /media/WD250GB\ Part\ 2 -o force

returned.....
 
mount: mount point /media/WD250GB Part 2 does not exist

(It didn't say that with the original mount line...just that it could not mount it.

---

### Post by trikster_x on 2010-10-31
Okay, forgive me if this sounds noobish, but what is "Part 2" there for?  Is it part of the directory you are mounting in?  I only ask because I don't see a "part" option on the man page.

And have you tried to simply:
```
sudo mount /dev/sdh5 /media
```

---

### Post by mistypotato on 2010-10-31
> **trikster_x said:**
> Okay, forgive me if this sounds noobish, but what is "Part 2" there for?  Is it part of the directory you are mounting in?  I only ask because I don't see a "part" option on the man page.

And have you tried to simply:
```
sudo mount /dev/sdh5 /media
```

Hi again,

Yes...the partition label is **WD250GB Part 2**

But I completely understand the confusion :)

---

### Post by trikster_x on 2010-10-31
```
sudo mount -t ntfs-3g /dev/sdh5 /media/"WD250GB Part 2" -o force
```

Command line programs hate spaces in a file path.  Anytime there are spaces in a file or directory name, the portion of the file path needs double quotes. mount probably thought you were asking it to mount to /media/WD250G and adding a non-existent option.

---

### Post by mistypotato on 2010-10-31
All HAIL the Trikster :KS:KS:KS:KS:KS:KS

That last suggestion did the impossible  :P

You are a Ubuntu Genius and get credit not only for the solution, but being generous enough to help.

Thank you SO much !

btw...is trikster by any chance from the series Supernatural ?

Cheers !!!

---

### Post by trikster_x on 2010-10-31
> .is trikster by any chance from the series Supernatural ?
lol, nope, I've been using this screen name for everything from forums to email to game saves for probably 12 years.  And you are welcome for the help.  I actually had some problems arrive because of filenames in the past that forced me to rename a couple hundred files so there were no spaces in the file names.  That's when I found out about the double quotes allowing for spaces.  Needless to say, I just hyphen or underscore in my file names now.  Anyway, have fun with your partition :D

---


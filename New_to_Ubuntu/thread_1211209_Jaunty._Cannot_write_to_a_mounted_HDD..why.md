---
title: "Jaunty. Cannot write to a mounted HDD..why?"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by wetinwales on 2009-07-12
Hi All
Trying to populate my ITB HDD (sdb1) which is mounted ( according to:- mount: according to mtab, /dev/sdb1 is already mounted on /media/disk )

but I get the message:-
You do not have the necessary permissions to save the file. Please, check that you typed the location correctly and try again.

The HDD appears in > Places > as it should.

can anyone help?
WiW

---

### Post by DGortze380 on 2009-07-12
> **wetinwales said:**
> Hi All
Trying to populate my ITB HDD (sdb1) which is mounted ( according to:- mount: according to mtab, /dev/sdb1 is already mounted on /media/disk )

but I get the message:-
You do not have the necessary permissions to save the file. Please, check that you typed the location correctly and try again.

The HDD appears in > Places > as it should.

can anyone help?
WiW

please post the output of 

```

ls -al /media | grep disk

```

```

cat /etc/fstab

```

---

### Post by northern lights on 2009-07-12
Can you post the output of```
cat /etc/fstab
``` and ```
cd /media/ && ls
```

---

### Post by wetinwales on 2009-07-12
Hi DGorze380 and northern nights

Thanks.. Outputs as follows:-

ls -al /media | grep disk
drwxr-xr-x  3 root root 4096 2009-06-19 00:02 disk

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=06b0c54e-d0b2-421f-befe-9da69bce1bd3 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=db834c63-6314-4a26-9bb2-9fc5e8597ba9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


cd /media/ && ls
1TBdrive  cdrom  cdrom0  disk  floppy  floppy0  sdb1


Thanks again!

---

### Post by DGortze380 on 2009-07-12
I think you simply mounted with the wrong options.

try these, in order.

```

sudo umount /media/disk

```

```

sudo mount /dev/sdb1 /media/disk auto rw

```

Post back any errors. 
I'm not positive about those mount options, I don't have time to check syntax right now.
Also, what format is the hard drive?

If that works we can help you add it to fstab so it will automount correctly at boot.

EDIT: You can also try northern lights suggestion, it will not interfere with the commands I gave you. I suggest you run his command after umount and before mount.

---

### Post by northern lights on 2009-07-12
Run```
sudo chown -R USERNAME:USERNAME /media/disk && sudo chmod -R 770 /media/disk
``` with the drive mounted, assuming that its ext2/3/4, where USERNAME needs to be replaced by your username.

---

### Post by wetinwales on 2009-07-12
DGortze380

I get :-   sudo: unmount: command not found

then :-   sudo mount /dev/sdb1 /media/disk auto rw
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

Well I'm lost !!

---

### Post by wetinwales on 2009-07-12
northern lights

result for your instruction:-

sudo chown -R USERNAME:USERNAME /media/disk && sudo chmod -R 770 /media/disk

...seems to work. I have saved a file to the HDD.
Thanks for that. I will study your line to understand why it worked.

Many thanks to both of you.
You Guys keep Linux going for the likes of us!!

---

### Post by LewRockwell on 2009-07-12
it's "umount" with no "N"...

not "unmount"...

.

---

### Post by wetinwales on 2009-07-12
LewRockwell

That needs plastering all over the world. Hell I'm embarrassed.

Thanks

---

### Post by LewRockwell on 2009-07-12
> **wetinwales said:**
> LewRockwell

That needs plastering all over the world. Hell I'm embarrassed.

Thanks

you must be referring to the "Help Vampires" review...lol

(it's even embarrassing to me...lol)

.

---

### Post by northern lights on 2009-07-12
> **wetinwales said:**
> sudo chown -R USERNAME:USERNAME /media/disk && sudo chmod -R 770 /media/disk

...seems to work. I have saved a file to the HDD.
Thanks for that. I will study your line to understand why it worked.
[chown manpage]("http://www.manpagez.com/man/8/chown/")

[chmod manpage]("http://www.manpagez.com/man/1/chmod/")

---


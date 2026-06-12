---
title: "cannot mount gmailfs drive"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by sancho1980 on 2007-04-24
hi

i just installed gmailfs as described here:

[http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-installing.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-installing.html)

and then tried to mount my gmail account as described here:

[http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-using.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-using.html)

but it doesnt work!

this is what i get:

```
root@Kiste:/# mount -t gmailfs /usr/local/bin/gmailfs.py /gmail -o username=user, password=password, fsname=zOlRRa
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
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
```

What am I missing?

Martin

---

### Post by secretkeeper81 on 2007-08-01
I think the problem is that the options should not be separated by spaces but just by commas.

You wrote:

```
username=user, password=password, fsname=zOlRRa
```

Try this instead:

```
username=user,password=password,fsname=zOlRRa
```

---


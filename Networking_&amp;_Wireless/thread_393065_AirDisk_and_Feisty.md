---
title: "AirDisk and Feisty"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by giambrone on 2007-03-25
Hey guys, first...well, second, post (wasn't sure if it was in the right place so I thought I'd cover both areas that it kinda covers:)  - sorry for the double post),

I've been using Ubuntu for a while now, and only just managed to get my wireless working (I can finally unplug my ethernet!). I was trying to get my computer to see the Apple AirDisk on the network. After installing Avahi Zeroconf etc I've got it to print over bonjour, I'm wondering how to get it to mount the Disk on the network because my entire music collection is on there!!

Any help appreciated...

Matt :) :KS :)

---

### Post by smultronstallet on 2007-07-05
I'd also like to know how to mount the AirDisk with Ubuntu. The best I can find is this post on the Apple Discussions Forum:

> 
$ sudo mkdir /path/to/mountpoint
$ sudo mount -t cifs -o users,rw,uid=*USERNAME*,gid=*USERNAME*,ip=10.0.1.1,_netdev,username=*AIRDISKUSERNAME_IFAPPLICABLE*,password=*PASSWORD* //10.0.1.1/SHARE /path/to/mountpoint
[[COLOR="DarkOrange"]http://discussions.apple.com/message.jspa?messageID=4704056[/COLOR]]("http://discussions.apple.com/message.jspa?messageID=4704056")

When I try his instructions I get an error:

```
$ sudo mount -t cifs -o //10.0.1.1/250_GB /media/airdisk/

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

Perhaps someone can translate the instruction code from the Apple Discussions Forum into something more Ubuntu friendly?
Also, giambrone, how did you setup avahi-zeroconf to get the printing working?

---

### Post by smultronstallet on 2007-07-06
Those interested in this problem should refer to another thread of the same name located here:

[[COLOR="DarkOrange"]http://ubuntuforums.org/showthread.php?t=393034[/COLOR]]("http://ubuntuforums.org/showthread.php?t=393034")

Forum member **huygens** has been extremely helpful in this other thread (above link) and has offered plenty of workarounds for this particular problem.

---


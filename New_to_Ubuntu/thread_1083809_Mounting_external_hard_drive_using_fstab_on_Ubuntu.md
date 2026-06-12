---
title: "Mounting external hard drive using fstab on Ubuntu server"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by Da Choice on 2009-03-01
Hi :)
I have an ubuntu server that serves all my media to the rest of the network. All the data is stored on an external 1tb hard drive which is shared on Samba - no problems when manually mounted, works exactly as it is supposed to.

The problem arised when I tried to automate it using fstab - it refuses to acknowledge the existence of the hard drive BUT it works perfectly when I use "mount -a"which [if I understand correctly] should work exactly the same way.

I don't necessarily need to use fstab - I just need a painfree way to mount the hard drive consistently on boot. 

The error says something to the effect of: Error mounting special device: UUID 16E2-0F25 not found.

fstab entry -

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=214c50db-d98e-4a2f-8b1c-48126bc4177c /               ext3    relatime,erro$
# /dev/sda5
UUID=132e2a22-5c94-485e-92de-212e3232e239 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

#/dev/sdb1
UUID=16E2-0F25  /media/backup   vfat    umask=000       0       0

```

Command used to mount hard drive:
```
sudo mount -t vfat -o umask=000 /dev/sdb1 /media/backup
```

---

### Post by taurus on 2009-03-01
What's the output of these commands?

```
sudo fdisk -l
sudo blkid
```

---

### Post by theDaveTheRave on 2009-03-01
This thread

[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

is written by Bodhi Zazen, if you can't get this to function with fstab I'm sure that he will be able to help you find a method to do what you want.

I know that I have done a similar thing to mount a set of 1TB drives into a shared area at mount time, only difference was that they were internal drives. I get the impression however that this shouldn't really make a difference.

From memory, I would suggest you want to use the device "name" as opposed to the UUID (I had an experience where the UUID would change after a crash on another dual boot pc!).

Anyhow, I'm sure that Bodhi will be able to help you out.

David

---

### Post by vanadium on 2009-03-01
I would take the following approach:

1) Announce the drive in /etc/fstab by modifying the line as:
```

UUID=16E2-0F25  /media/backup   vfat,noauto    umask=000       0       0

```

2) Effectively mount the drive later during startup, i.e., in /etc/rc.local

```

mount /media/backup

```

---

### Post by Da Choice on 2009-03-05
Hey guys, it seems vanadium's method worked like a charm :)

Thanks for the all the help!

---


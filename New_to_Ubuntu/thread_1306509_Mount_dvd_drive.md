---
title: "Mount dvd drive"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by nickcollie on 2009-10-30
Hi, 

Stupid really.  have managed to unmount my dvd drive and cannot remount it.

Ubuntu 8.04

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9bc0a5b8-8653-4e5b-9f18-4874b54346e6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d2154ada-0c49-465f-9c25-d6b7a1ddedeb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

if that helps...

Any advice greatfully appreciated

---

### Post by alphaniner on 2009-10-30
How did you unmount it, and what have you done to try to remount it?

Also what is the output when you run **mount** in the terminal?

---

### Post by nickcollie on 2009-10-30
Stuff ( technical term ) from mount:

```
nick@Twofish:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nick/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nick)

```

Unmounted simply on a right click.

---

### Post by alphaniner on 2009-10-30
Good stuff.

Have you tried to eject the disc with the button on the drive, then re-insert?

Or, gone to Places -> Computer, right-click on the drive and select 'Mount Volume'?

---

### Post by nickcollie on 2009-10-30
Disc is out.  When I put in a disk now I get nothing. 

The drive isn't listed in places whether or not it has a disk in it.

Thanks for your time !

---

### Post by alphaniner on 2009-10-30
> The drive isn't listed in places whether or not it has a disk in it.

That's not good.  It should be either way.

Put a disc in and open a terminal.

Run the following command and post the output:

```
sudo mount /dev/scd0 /media/cdrom0
```

---

### Post by nickcollie on 2009-10-30
Sorry for the delay -  Result of that is :


nick@Twofish:~$ sudo mount /dev/scd0 /media/cdrom0
[sudo] password for nick: 
mount: special device /dev/scd0 does not exist

---

### Post by alphaniner on 2009-10-30
> **nickcollie said:**
> mount: special device /dev/scd0 does not exist

I think that means your drive is no longer being seen.

I'm not sure where to go from here, except to reboot, check your BIOS to make sure your drive is still showing up, and maybe try to boot from a disc.  I know a hardware problem seems infinitely unlikely, but it's what I'd do in your situation.  

Another option is to wade through your logs and see if you can find any clues there.  But I don't have the time to help with that.
Sorry.

---

### Post by nickcollie on 2009-10-30
alphaniner

don't apologise!  Thank you so much for the time you have given.  

Nick

---


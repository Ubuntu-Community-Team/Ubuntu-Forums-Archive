---
title: "automount NAS"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by michaelharg on 2008-09-15
Hi there, I'm having trouble getting my Q-NAP 209-II Pro to automount shares. I can navigate to them through Places> Network> Windows Server> NAS> MHNAS, and access all my shares ok.

My etc/fstab looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6a7ca1e5-a160-4314-adeb-53a4f5ece05e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=d2e53d01-1eca-44ac-8f3d-875ca5c0e7c3 /home           ext3    relatime        0       2
# /dev/sda5
UUID=59cb6c1a-7fcd-4b3a-876b-9fef76c46312 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# NAS
//mhnas/qmultimedia /home/michael/Music/NMusic smb defaults 0 0
```

If I try and mount the drive from the command line i get:

```
michael@michael-laptop:~$ sudo mount /home/michael/Music/NMusic
mount: unknown filesystem type 'smb'
```

I've been through most of the forum pages but find I'm a bit out of my depth so any help would be nice.

Thanks

edit: I connect to the sever over a wireless network..

---

### Post by Iowan on 2008-09-15
SMB has been replaced by CIFS.  Try mounting instructions [here]("http://ubuntuforums.org/showthread.php?t=288534").

---


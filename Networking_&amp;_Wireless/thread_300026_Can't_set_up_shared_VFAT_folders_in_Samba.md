---
title: "Can't set up shared VFAT folders in Samba"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by baldercm on 2006-11-15
Hi everybody!

I'm running Kubuntu Edgy and nearly everything works ok. I've set up different share directories on my home network using Samba. My smb.conf uses
```
security=share
```
and my shared folders are defined
```
[shared]
case sensitive = no
guest ok = yes
msdfs proxy = no
read only = no
path = /home/balder/shared

[music]
case sensitive = no
guest ok = yes
msdfs proxy = no
path = /media/LACIE/music
read only = no
```

The shared folder works perfectly, it's part of an EXT3 partition and permissions are 777.

My problem is the music folder: it's in a VFAT partition that KDE mounts automatically. When I scan my network on the other PC, I can see the folder, but I can't read it, I get an error that says that the folder can't be read and the path to smb://balder/music does not exist.

I think it must be a permission problem, but i don't know how to change vfat permissions (is it possible?)...
The mtab entry for VFAT looks like:
```
/dev/sda1 /media/LACIE vfat rw, nosuid, nodev, quiet, shortname=mixed, uid=1000, gid=1000, umask=077, iocharset=utf8 0 0
```

I hope someone can help me... Thanks!

---


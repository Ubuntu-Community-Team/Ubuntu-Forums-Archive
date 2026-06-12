---
title: "NAS CIFS automount and startup errors"
date: 2013-11-14
forum: Networking &amp; Wireless
---

### Post by massimo.cristofoli on 2013-11-14
I've just removed Ubuntu 12.04 and installed Ubuntu GNome 13.10.
I have copied the /etc/fstab I had on 12.04, so I can have my NAS disks mounted on startup for free.
Or so I thought...
Here are the /etc/fstab lines
```
//192.168.1.7/mix /media/Server cifs credentials=/root/LNSsmb.crd,nobrl,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.7/OpenShare /media/OpenShare cifs credentials=/root/LNSsmb.crd,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

The disks are mounted and accessible, but I get these errors during boot
```
Nov 14 18:53:19 PCMIX kernel: [   11.539785] CIFS VFS: Error connecting to socket. Aborting operation.
Nov 14 18:53:19 PCMIX kernel: [   11.540239] CIFS VFS: cifs_mount failed w/return code = -101
Nov 14 18:53:19 PCMIX kernel: [   12.121838] CIFS VFS: Error connecting to socket. Aborting operation.
Nov 14 18:53:19 PCMIX kernel: [   12.121966] CIFS VFS: cifs_mount failed w/return code = -101
```
and a system error popup when I log in.

What could it be?

---

### Post by bab1 on 2013-11-14
> **massimo.cristofoli said:**
> I've just removed Ubuntu 12.04 and installed Ubuntu GNome 13.10.
I have copied the /etc/fstab I had on 12.04, so I can have my NAS disks mounted on startup for free.
Or so I thought...
Here are the /etc/fstab lines
```
//192.168.1.7/mix /media/Server cifs credentials=/root/LNSsmb.crd,nobrl,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.7/OpenShare /media/OpenShare cifs credentials=/root/LNSsmb.crd,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

The disks are mounted and accessible, but I get these errors during boot
```
Nov 14 18:53:19 PCMIX kernel: [   11.539785] CIFS VFS: Error connecting to socket. Aborting operation.
Nov 14 18:53:19 PCMIX kernel: [   11.540239] CIFS VFS: cifs_mount failed w/return code = -101
Nov 14 18:53:19 PCMIX kernel: [   12.121838] CIFS VFS: Error connecting to socket. Aborting operation.
Nov 14 18:53:19 PCMIX kernel: [   12.121966] CIFS VFS: cifs_mount failed w/return code = -101
```
and a system error popup when I log in.

What could it be?
This is usually because networking is not available at mount time.  Apparently it retries the mount again after the network is up.

---

### Post by massimo.cristofoli on 2013-11-16
I thought about the fact that no wireless connection is enabled during boot, so the OS can't find the NAS and these errors appears. I was concerned about the errors I get after the login. By the way, they disappeared... don't know why... Maybe they are related with something else.
I will update the thread if I get them again, with further infos.

Thanks!
MIX

---


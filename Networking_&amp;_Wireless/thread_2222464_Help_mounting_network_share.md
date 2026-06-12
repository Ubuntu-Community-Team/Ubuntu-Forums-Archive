---
title: "Help mounting network share"
date: 2014-05-06
forum: Networking &amp; Wireless
---

### Post by Jens_Bodal on 2014-05-06
I cannot get this network share to mount, I keep getting: mount error(13): Permission denied

```
sudo mount -t cifs //10.0.0.11/MEMORYCARD /Share/Scans -o guest
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

This is a simple network share that doesn't require a username and password, I can access it no problem from OSX or Windows at 10.0.0.11/MEMORYCARD

The share is hosted on an Epson WorkForce 840 Printer's USB Memory card

Using ```
sudo smbclient //10.0.0.11/MEMORYCARD -A /root/.epson
``` logs into the share just fine, as does entering any arbitrary user/password as none are required to access the share.

I've read that using cifs is now a requirement, and can be seen with:

```
sudo mount -t smbfs //10.0.0.11/MEMORYCARD /Share/Scans -o username=spiadmin,noexec
mount: unknown filesystem type 'smbfs'
```

I would just simply like to mount this share to my linux box, does anyone have any suggestions?

---

### Post by Jens_Bodal on 2014-05-06
Problem solved.

CIFS needed the -sec=ntlm option

sudo mount -t cifs //10.0.0.11/MEMORYCARD /mnt/epson -o guest,sec=ntlm

[http://unix.stackexchange.com/questions/70411/mount-t-cifs-operation-not-supported-but-can-connect-via-smbclient](http://unix.stackexchange.com/questions/70411/mount-t-cifs-operation-not-supported-but-can-connect-via-smbclient)

---


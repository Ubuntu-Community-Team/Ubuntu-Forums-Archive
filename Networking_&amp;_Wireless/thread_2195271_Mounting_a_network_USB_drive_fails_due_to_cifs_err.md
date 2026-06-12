---
title: "Mounting a network USB drive fails due to cifs error 13"
date: 2013-12-23
forum: Networking &amp; Wireless
---

### Post by XC-lemens on 2013-12-23
Hi all,
I have a very strange and annoying problem when mounting a USB drive connected on a "Fritz!Box". It *was* easy to access on my old Ubuntu 12.04 32 bit PC by simple adding

```
//192.168.178.1/datatraveler2-0-0-1 /home/ku/Netzwerkordner smbfs guest 0 0
```

to the ```
/etc/fstab file
```. On each restart it was mounted automatically. Now I switched to a new PC and installed 12.04 in 64 bit. I don't know why, but this procedure doesn't work any longer. The drive is not password protected or something else. I can still access it very easy via Windows. I tried

```
//192.168.178.1/datatraveler2-0-0-1 /home/ku/Netzwerkordner cifs default 0 0
```

and other stuff by creating a credential file etc. Everything ended up with the message

```
mount error(22): Invalid argument
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

*But* what works straight ahead is: ```
gvfs-mount smb://192.168.178.1/datatraveler2-0-0-1
```

Does anyone know how to fix this problem, so that the drive gets mounted automatically to a given folder? Thanks a pleasant Christmas!

---

### Post by tfrue on 2013-12-23
Give this article a read and see if that helps.
[http://askubuntu.com/questions/157128/proper-fstab-entry-to-mount-a-samba-share-on-boot](http://askubuntu.com/questions/157128/proper-fstab-entry-to-mount-a-samba-share-on-boot)

-Chris

---

### Post by XC-lemens on 2013-12-23
Hi Chris,
not really. I don't know what to put in username and password for example.

---


---
title: "Mounting cifs at boot"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by skroops on 2007-12-31
I'm trying to mount a windows xp share at boot, but I get nothing after start up.  Here is what I put in my fstab

```
//leroy/Raid\040\050F\051       /mnt/mce        cifs    guest,rw,file_mode=0777,dir_mode=0777 0 0

```

The path is at smb://leroy/Raid (F) and it has guest rw access enabled.

Is the fstab alright and is there a way to view any errors that line may have caused after the boot sequence?

---

### Post by Predator[23rd] on 2007-12-31
Check this please. Maybe it solves your problem ...

[http://ubuntuforums.org/showthread.php?t=336866](http://ubuntuforums.org/showthread.php?t=336866)

---

### Post by HermanAB on 2007-12-31
Try to mount it manually and watch the error messages.  My guess is that your Workgroup is wrong, since that is the most common issue with SMB networks.

Cheers,

Herman

---

### Post by skroops on 2008-01-01
Mounts fine manually, just not at boot.

---


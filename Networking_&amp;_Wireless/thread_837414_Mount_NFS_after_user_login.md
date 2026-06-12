---
title: "Mount NFS after user login"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by Decoy on 2008-06-22
Hi!
Is there any way to mount NFS after user logged into system? While system booting it tries to mounts shares according to /etc/fstab file but on this stage network isn't up yet cause wireless iface bringing up by Network Manager which start after login, so it fails mount on load and holds the boot...

---

### Post by dmizer on 2008-06-23
quickest way i can think of is:
```
sudo mount -a
```

you could also write a script to include this in your networkmanager start sequence, but that could prove to be more difficult than it sounds, and i have zero experience with scripting.

---

### Post by Decoy on 2008-06-25
Temporary used script [http://ubuntuforums.org/showthread.php?t=592968](http://ubuntuforums.org/showthread.php?t=592968) as solution

---


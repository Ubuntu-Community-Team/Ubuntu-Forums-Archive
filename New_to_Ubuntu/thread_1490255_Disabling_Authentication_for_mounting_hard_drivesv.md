---
title: "Disabling Authentication for mounting hard drives/volumes"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by highflie on 2010-05-22
Hi all,
 I use Ubuntu 9.10. Every time I try to open a hard drive/volume I have to enter the password for authentication which after some time gets really irritating. Can anyone suggest a way for me to disable this feature?

Thanks in Advance,
Lalit

---

### Post by Elfy on 2010-05-22
If the drive is always connected add it to fstab so it is mounted at boot.

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by mc4man on 2010-05-22
If you are** the admin. user** than creating a .pkla will remove the need to authenticate mounting internal filesystems in karmic.

open a terminal and create the file (because the file doesn't exist yet I'd copy and paste this carefully rather than manually copy

```
gksu gedit /var/lib/polkit-1/localauthority/10-vendor.d/org.freedesktop.DeviceKit.Disks.pkla

```

Copy and Paste this inside and save (should show up as 4 lines

```
[No password required for admins]
Identity=unix-group:admin
Action=org.freedesktop.devicekit.disks.filesystem-*;org.freedesktop.devicekit.disks.change-system-internal
ResultActive=yes
```

Save the file and that should do it..

---


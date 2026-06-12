---
title: "Mounting a network drive on bootup."
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by Sean K on 2007-02-27
Hey there,

I've been trying to mount a network drive (on an XP machine) so it stays mounted on bootup, and I've been following the instructions I found on the following site: [http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

This is what I'm putting at the very end of fstab:
```
//192.168.0.101/C%20Drive    /mnt/NetworkDisk[AMD0549] smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0
```

When I try to remount /etc/fstab with:
```
sudo mount -a
```

I get the following error:
```
mount: wrong fs type, bad option, bad superblock on //192.168.0.101/C%20Drive,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

After doing that, I try and go to /mnt/NetworkDisk[AMD0549] and it's just a blank folder, which I assume means it hasn't been successfully mounted.

Can anyone help me figure out why it's not working? I'd really appreciate it... thanks in advance. =)

---

### Post by Sean K on 2007-02-28
Okay, so I figured out that part of the problem was that I didn't even have Samba installed. I did that. Now I get a different error message.

```
sudo mount -a
29085: tree connect failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed
```

Any ideas?

---


---
title: "Samba stops responding"
date: 2007-12-23
forum: Networking &amp; Wireless
---

### Post by elicoten on 2007-12-23
I find that after a while I cannot access my samba shares without rebooting. I do
```
mount -t smbfs //server/share /mnt/sharename
```
and it seems to work and then all of a sudden it stops. I tried unmounting it and remounting it, but when I try to unmount I get a device is busy error.

Is there any other way to get this working without rebooting?

thanks in advance

---

### Post by santosh_gr on 2007-12-24
try restarting the samba service by typing

/etc/init.d/samba restart

Also look into /var/log/samba folder to see if you see any errors.  You will need to look into the correct log file as per your setup.

Also try connect within ubuntu using smbclient software.

try smbclient //hostname/sharename -U username

It will prompt you for a password.  And see if it connects.

Make sure that your shared folder is accessible (and exists)  when you try to open it remotely.

---

### Post by elicoten on 2007-12-24
I got an error message /etc/init.d/samba: No such file or directory

Last few messages in that logfile are similar to:
  mount.smbfs: entering daemon mode for service \\server\share, pid=7645

I can still connect to the share from the network folder (smb://server/share), and all the other mounted share are stll accessible.

I think it could be related to RhythmBox see [http://ubuntuforums.org/showthread.php?t=649205](http://ubuntuforums.org/showthread.php?t=649205)

---


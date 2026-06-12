---
title: "[SOLVED] CIFS Unix Extensions Headache"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by gers4302 on 2007-06-25
The ultimate goal of this is to use a WD World Book Edition II as a network backup drive.

I'm using Amanda for doing backups, using their virtual tape driver.  Currently, it's using a 300GB USB2 drive and it works great.  Now I'd like to use the CIFS share off of the World Book.

When I first mounted the drive, the World Book was getting mapped with the UID's off of the device, so when mounted, the drive would be owned by www-data:root.

I found instructions on how to turn off CIFS Unix Extensions, which then allowed me to mount the drive to the system as backup:backup.

Amanda now needs to symlink the virtual tape slots to do the backup.  Symlinking isn't supported in CIFS when the CIFS Unix Extensions are disabled.

What I'm looking for is a way to mount the CIFS share and force the permissions to backup:backup while also being able to symlink directories.

I'm currently mounting the share like the following:

```
# echo 0 > /proc/fs/cifs/LinuxExtensionsEnabled
# sudo mount -t cifs -ouser=amanda,password=******,uid=backup,gid=disk //192.168.1.51/backup /backup
# echo 1 > /proc/fs/cifs/LinuxExtensionsEnabled
```

---

### Post by gers4302 on 2007-06-26
Never mind... I found a way to hack the device to give me NFS, which works much nicer.

---


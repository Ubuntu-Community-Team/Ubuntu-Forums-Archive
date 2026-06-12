---
title: "Please Help With Permissions"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by nakama85 on 2009-11-09
Everything was fine last night but today when I came home from work my hard drive that I have mounted to a folder has the lock symbol on it. I checked the permissions via "sudo nautlius" and they are correct. What happened???

---

### Post by sisco311 on 2009-11-09
Probably an error occurred and the partition was remounted read only.

Unmount it and check it for errors. You can use [gparted]("apt://gparted") or the e2fsck command.

```
sudo unmount /dev/sdXY
```
```
sudo e2fsck -C0 -p -v -f /dev/sdXY
```

replace /dev/sdXY with the actual device name.

---

### Post by nakama85 on 2009-11-09
> **sisco311 said:**
> Probably an error occurred and the partition was remounted read only.
Unmount it and check it for errors. You can use [gparted]("apt://gparted") or the e2fsck command.
```
sudo unmount /dev/sdXY
```
```
sudo e2fsck -C0 -p -v -f /dev/sdXY
```
replace /dev/sdXY with the actual device name.

Thanks. I ran "sudo umount /dev/sda1" like you suggested and tested it with no errors. I then rebooted it and it is working fine. Still scratching my head though on why it happened to begin with. I did not shut down or reboot between the time it was working and the time it stopped.  Thanks Again

---


---
title: "Broken /etc/fstab in changing hard drive from NTFS"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by Chrissd on 2009-04-17
Finally made the leap completely from Windows to 100% Ubuntu now.

In doing so, I made the NTFS hard disk EXT3, and thought I adjusted /etc/fstab. I don't remember what it said, but I think I've changed the UUID and added ext3. 

/etc/fstab now looks like this
```
UUID=660c88b7-d32b-4007-96bc-d7ac0d822096 /media/80GB ext3 defaults,umask=0007,gid=46 0 0
```

If I try and open the hard drive, it says I don't have the privileges to mount it.

Any help? :(

---

### Post by northern lights on 2009-04-17
Do you own /media/80GB?

If not, run```
sudo chown USER:USER /media/80GB && sudo chmod -R 744 /media/80GB
```wher USER needs to be replaced by your username.

---

### Post by unutbu on 2009-04-17
In addition to northern light's suggestion, perhaps try removing ```
umask=0007,gid=46
``` from the options list (for the ext3 partition). 

files and directories on ext3 each have their own permissions and group id setting. Unlike for NTFS, they are not set at mount-time.

---

### Post by Chrissd on 2009-04-23
It now just points towards lost+found. It seems like I've lost my hard drive.

Any other help? :(

---

### Post by unutbu on 2009-04-23
Please post the output of

```
sudo fdisk -l
cat /etc/fstab
sudo blkid -c /dev/null
```

---


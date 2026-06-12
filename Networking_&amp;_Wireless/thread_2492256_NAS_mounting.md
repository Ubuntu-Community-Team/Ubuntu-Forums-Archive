---
title: "NAS mounting"
date: 2023-11-05
forum: Networking &amp; Wireless
---

### Post by aeh63 on 2023-11-05
I can mount my NAS with the following command: sudo mount 192.168.0.56:/Public /mnt/NAS. How can I make this automatic?

---

### Post by TheFu on 2023-11-05
**sudoedit** the /etc/fstab file appropriately.  The type needs to be "nfs".  If the NAS supports NFSv4.1+, then you can improve performance by adding connections from the client mount options.

Google found these references: 
[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

You may want to NOT mandate mounting of NFS stuff, since it could make boots stuck if the NAS isn't network available.  I use **autofs** to avoid this issue, but if you are new to Unix/Linux, that setup is more complex than adding 1 line to the fstab.

---

### Post by TheFu on 2023-11-05
```
sudo mount 192.168.0.56:/Public /mnt/NAS
```
BTW, here's a line for the fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
192.168.0.56:/Public     /mnt/NAS   nfs   defaults    0  0
```

After editing the file and saving it, run **sudo mount -a** to re-read the fstab file and mount anything that isn't already mounted.  IF you NAS is always booted and available BEFORE the computer is booted, this will work fine.

For some more safety, there are two types of automountd methods.  autofs and letting systemd-mountd delay the mounts until specifically requested.  [Https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156](Https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156) is the systemd-authmount method.  I think it comes down to these options:
```
x-systemd.automount,x-systemd.idle-timeout=600s,proto=tcp,noauto
```
use those instead of the "default" in the fstab above.

---


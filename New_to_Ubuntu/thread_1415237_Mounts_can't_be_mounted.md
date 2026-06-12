---
title: "Mounts can't be mounted"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by solissydney on 2010-02-24
Mounts can't be mounted in latest Ubuntu.
Message
Dos waiting for UUID=06b7-60b6
home waiting for uuid=2171a652-f56d-41be-ab01-d176bdbf71e8

One or more of the mounts listed in etc/fstab can't be mounted

Error; via: invalid checksum on /dev/sdb370/8169-492cce32a12a
general error mounting filesystems
a maintenance shell will now be started
control-d will terminate this shell and re-try
root@kp-desktop

When I type in; control-d it says command not found.

Dual booting with XP
Can you help please?

---

### Post by cariboo on 2010-02-24
Boot from your Live CD and once at the desktop, Open an Applications->Accessories->Terminal and type:

```
sudo fsck -a /dev/sdb
```

Substitute your device label for the on in the command above.

---

### Post by prem1234 on 2010-02-25
Thanks!I used the options you specified and that got the drive mounted but I still can't mount any of my other drives without using the command line.

---


---
title: "Auto-mount Windows drives"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by sharks on 2009-07-20
I have 8.10 . Only one windows drive mounts everytime. I do proper shutdown. And i need to manually mount the drives using this : sudo mount /dev/sda5 /media/media -o force


How do i mount all the drives automatically?

---

### Post by komputes on 2009-07-20
If you want partitions to be mounted at boot they must be in /etc/fstab. To learn more read:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Mark Phelps on 2009-07-22
Hope you realize that by adding "force" to the mount command, you're running the risk of corrupting the Windows partition when you mount it.  If it's data, and it's backed up somewhere, then you don't have to worry much, but if you're forcing the mount of an OS partition, you run the risk of rendering it unbootable.

---

### Post by drs305 on 2009-07-22
This link gives you various ways to mount windows (ntfs) partitions. 

[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

ntfs-config is probably the easiest way to mount an ntfs partition. If ntfs-config doesn't work, there is probably something wrong with the filesystem. You can download an app called "ntfsprogs" and run ntfsfix on the device if running a windows filesystem check doesn't fix it.

---


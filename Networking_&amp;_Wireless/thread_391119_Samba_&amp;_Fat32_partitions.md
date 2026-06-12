---
title: "Samba &amp; Fat32 partitions"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by adamosis on 2007-03-22
Hi all,
So I just setup Samba and I have it running but I can't connect to my shared directory. I've narrowed it down to a permissions issue. I know fat32 is a permissions-free file system, but the shared directory resides on this fat32 partition and seems to only be accessible by root. Since I can't change permissions, is there a way to mount with everyone can write capabilities?

What other options do I have here?
Thanks!

---

### Post by angelmartinezn on 2007-03-23
this permissions have to be changed in /etc/fstab:

check this thread: [http://ubuntuforums.org/showthread.php?t=387853&highlight=fstab](http://ubuntuforums.org/showthread.php?t=387853&highlight=fstab)


Regards,

---

### Post by adamosis on 2007-03-24
Excellent, this is exactly what I was looking for. Couldn't remember for the life of me what controlled the auto-mounting on boot.
Thanks

---

### Post by adamosis on 2007-03-25
Problem was resolved by changing the umask from 007 to 000 in the /etc/fstab file.

---


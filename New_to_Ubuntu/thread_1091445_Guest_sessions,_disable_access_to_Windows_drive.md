---
title: "Guest sessions, disable access to Windows drive?"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by ronaldrand on 2009-03-09
Hello,

I have my WindowsXP partition on my desktop in Ubuntu. But I would like it not to show up when Guest session is used. Is that possible? Thanks in advance.

---

### Post by ronaldrand on 2009-03-10
I managed to restrict access to it using my fstab file. I changed it to look like this:

# Windows partition
/dev/sda1  /media/drv0  ntfs-3g  defaults,umask=0007,gid=1000  0  0

The gid is the Group ID for my normal login username. I'd still like to have the drive not show up on the desktop at all though. The drive still shows up, but when someone opens it, it says they don't have rights to it.

Thanks in advance and I hope this helps someone.

---


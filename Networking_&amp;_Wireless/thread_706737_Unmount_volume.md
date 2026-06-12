---
title: "Unmount volume"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by psychofish25 on 2008-02-24
I have mounted a volume under Network via SSH. When I right click there is no unmount option, and I can't delete the volume. How can I get rid of it?

---

### Post by nixscripter on 2008-02-25
How was the volume mounted? If the gnome mounter wasn't used, it needs to be done with the umount command.

Find the directory where it is mounted, and type into the command line: ```
sudo umount **path-to-dir**
``` If you don't know where it is, type in the command line ```
mount
``` and see if you can find it in the list.

---


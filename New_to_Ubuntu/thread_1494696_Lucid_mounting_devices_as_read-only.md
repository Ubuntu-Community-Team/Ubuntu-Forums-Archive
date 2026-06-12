---
title: "Lucid mounting devices as read-only"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by viniciuscarvalho on 2010-05-27
Hello there! I have Sony Vaio VGN-FW465. It has a SD reader, and since I move to Lucid, it is only mounting my SD cards as read-only file system. I tried to edit /etc/mtab:

/dev/mmcblk1p1 /media/CARTAO vfat rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush 0 0


moving ti to defaults, but when I umount and mount again it comes back to this config.

What can I do to be able to write to this filesystem?

Regards

---


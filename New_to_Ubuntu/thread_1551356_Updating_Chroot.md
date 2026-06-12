---
title: "Updating Chroot"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by osorezan on 2010-08-12
Hey!  ;)
I've created a chroot environment but now i want to update it to  the latest release. How can i do that?

[root@leaf build]# cd  chroot_build/
[root@leaf chroot_build]# ls
bin/   builddeps.py*   etc/   initrd/  media/  opt/   root/         sbin/  tmp/  var/
boot/   dev/           home/  lib/     mnt/    proc/  rpmbuild.py*  sys/   usr/
[root@leaf  chroot_build]#

Should I remove (rm -rf /chroot_build) the  chroot_directory and then install it again ?
Should I first umount ?
I  don't know exactly what do to to "remove" it and then create a new one :(

Thanks,

Sara

---

### Post by limestone on 2010-08-12
If you have installed it from source you can't update it, you'll have to download the latest source

---

